---
layout: blog
topic: OutNetwork-Learn-Dune-Analytics
title: Smart Contract Events
tags: ethereum data dune sql token smartcontract
comments: true
date: 2022-04-07
---

# Smart Contract Events

SET Basic Issuance: https://etherscan.io/address/0xd8ef3cace8b4907117a45b0b125c68560532f94d#events

```sql
# Calculating the current supply of the Metaverse Index
# MVI: https://etherscan.io/token/0x72e364f2abdc788b7e918bc238b21f109cd634d7

WITH units AS (
    -- Amount Issued
    SELECT
        SUM("_quantity"/1e18) AS units
    FROM setprotocol_v2."BasicIssuanceModule_evt_SetTokenIssued"
    WHERE "_setToken" = '\x72e364f2abdc788b7e918bc238b21f109cd634d7'

    UNION ALL
    -- Amount Redeemed
    SELECT
        -SUM("_quantity"/1e18) AS units
    FROM setprotocol_v2."BasicIssuanceModule_evt_SetTokenRedeemed"
    WHERE "_setToken" = '\x72e364f2abdc788b7e918bc238b21f109cd634d7'

)

SELECT
    SUM(units) AS unit_supply
FROM units
```

## SQL: Join
![join](/assets/join.PNG)

### Cross Join
Generate all possible combinations

### Sample Code

```sql
-- Find the price of DPI in USD
-- By joining a table of DPI price in eth with a table of eth price in USD

WITH dpi_uniswap_v3_swaps AS (

    SELECT
            date_trunc('hour', "evt_block_time") AS hour,
            AVG((ABS(amount1)) / (ABS(amount0))) AS swap_price -- token0 = DPI, -- token1 = ETH
    FROM    uniswap_v3."Pair_evt_Swap"
    WHERE   contract_address = '\x9359c87b38dd25192c5f2b07b351ac91c90e6ca7' -- DPI
    GROUP BY 1

),

eth_usd AS (
    SELECT
        date_trunc('hour', "minute") AS hour,
        AVG(price) AS price
    FROM prices.usd
    WHERE contract_address = '\xc02aaa39b223fe8d0a0e5c4f27ead9083c756cc2' -- wrapped ETH
    GROUP BY 1
)

SELECT
    a.hour,
    a.swap_price * b.price AS price
FROM dpi_uniswap_v3_swaps a
LEFT JOIN eth_usd b ON a.hour = b.hour
WHERE a.hour >= '2021-05-07'
```

```sql
-- List the LP address that have minted liquidity in v2 or v3
SELECT lp_address FROM v2_mint
UNION
SELECT lp_address FROM v3_mint

-- List the LP addresses that have minted liquidity in both v2 and v3
SELECT lp_address FROM v2_mint
INTERSECT
SELECT lp_address FROM v3_mint

-- List the LP addresses that have minted on v3 and not on v2
SELECT lp_address FROM v2_mint
EXCEPT
SELECT lp_address FROM v3_mint
```
