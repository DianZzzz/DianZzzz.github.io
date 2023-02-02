---
layout: blog
topic: OutNetwork-Learn-Dune-Analytics
title: DEX
tags: ethereum data dune sql dex
comments: ttorue
date: 2022-04-10
---

# Everything About DEXs

## History of Decentralized Exchanges

![dex](/assets/dex.png)

### Order Book DEX
* Like the stock market
* There would be a trade if there is matching demand and supply
* The price is determined by the order book
* Problem: limited liquidity

### Automated Market Maker
* Like Uniswap and its variations
* The price is not determined by the order book, but by an algorithm
* The liquidity in the market is provided by LPs, liquidity providers who contribute to the liquidity pool

### Aggregators
* Like Google Flights or Expedia
* Aggregators search through different DEXs for the best prices

### Aggregators of Aggregators
* Like Cowswap
* Execute orders in batch so there is no frontrunning
* Minimize the problem of MEV, Maximal Extractable Value

```sql
-- Create a Uniswap v3 trades Table
WITH raw_trade AS (
    SELECT t.evt_block_time AS block_time,
            t.evt_block_number AS block_number,
            t.evt_tx_hash AS tx_hash,
            t.evt_index,
            recipient AS trader_a,
            NULL::bytea AS trader_b,
            token0 AS token_a_address,
            token1 AS token_b_address,
            ABS(amount0) AS token_a_amount_raw,
            ABS(amount1) AS token_b_amount_raw
    FROM uniswap_v3."Pair_evt_Swap" t
    JOIN uniswap_v3."Factory_evt_PoolCreated" f ON t.contract_address = f.pool
    LIMIT 10
)

-- Just showing the transaction table    
SELECT
    tx_hash,
    pa.symbol as token_a_symbol,
    pb.symbol as token_b_symbol,
    token_a_amount_raw / 10 ^ ta.decimals as token_a_amount,
    token_b_amount_raw / 10 ^ tb.decimals as token_b_amount,
    (coalesce(token_a_amount_raw / 10 ^ ta.decimals * pa.price,
              token_b_amount_raw / 10 ^ tb.decimals * pb.price)) AS usd_amount

FROM raw_trade r
LEFT JOIN erc20."tokens" ta ON ta.contract_address = r.token_a_address
LEFT JOIN erc20."tokens" tb ON tb.contract_address = r.token_a_address
LEFT JOIN prices."usd" pa ON pa.contract_address = r.token_a_address
                                AND pa.minute = date_trunc('min', block_time)
LEFT JOIN prices."usd" pb ON pb.contract_address = r.token_b_address
                                AND pb.minute = date_trunc('min', block_time)
WHERE (coalesce( token_a_amount_raw / 10 ^ ta.decimals * pa.price,
                         token_b_amount_raw / 10 ^ tb.decimals * pb.price)) is NOT NULL                    
ORDER BY 2 DESC LIMIT 10

-- Aggregate the transactions by date
SELECT date_trunc('day', block_time) as date,
           sum((coalesce(token_a_amount_raw / 10 ^ ta.decimals * pa.price,
                  token_b_amount_raw / 10 ^ tb.decimals * pb.price))) AS usd_amount

FROM raw_trade r
LEFT JOIN erc20."tokens" ta ON ta.contract_address = r.token_a_address
LEFT JOIN erc20."tokens" tb ON tb.contract_address = r.token_a_address
LEFT JOIN prices."usd" pa ON pa.contract_address = r.token_a_address
          AND pa.minute = date_trunc('min', block_time)
LEFT JOIN prices."usd" pb ON pb.contract_address = r.token_b_address
          AND pb.minute = date_trunc('min', block_time)
WHERE (coalesce(token_a_amount_raw / 10 ^ ta.decimals * pa.price,
                token_b_amount_raw / 10 ^ tb.decimals * pb.price)) is NOT NULL                    
GROUP BY 1  
```

```sql
-- Find top 10 trading pairs by volume
WITH pair_rank AS (
    SELECT  date_trunc('month', block_time) AS month,
            CASE WHEN coalesce(token_a_symbol, token_a_address::text) < coalesce(token_b_symbol, token_b_address::text)
                        THEN coalesce(token_a_symbol, token_a_address::text) || '-' || coalesce(token_b_symbol, token_b_address::text)
                        ELSE coalesce(token_b_symbol, token_b_address::text) || '-' || coalesce(token_a_symbol, token_a_address::text)
            END AS pair,
            sum(usd_amount) AS total_volume,
            rank() over (partition BY date_trunc('month', block_time) ORDER BY sum(usd_amount) DESC) AS rank_
    FROM dex."trades"
    WHERE date_trunc('month', block_time)>now() - interval '6 months'
            AND usd_amount is NOT NULL
            AND category ='DEX'
    GROUP BY 1,2
)
SELECT month,
    CASE WHEN rank_ < 10
    THEN pair ELSE 'Others'
    END AS rank_flag,
    sum(total_volume) AS total
FROM pair_rank
GROUP BY 1, 2
```
