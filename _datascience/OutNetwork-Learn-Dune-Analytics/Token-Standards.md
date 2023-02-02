---
layout: blog
topic: OutNetwork-Learn-Dune-Analytics
title: Token Standards
tags: ethereum data dune sql token
comments: true
date: 2022-04-03
---

# Token Standards

Each token has a smart contract that is used to
* Create tokens
* Handle transactions
* Track balances

Without standards, Web3 apps need custom codes to interact with each new token.
With standards, Web3 app can use the same code to interact with all tokens.

## ERC20 tokens
* Fungible tokens: any one token is exactly the same as any other token

## ERC721 tokens
* Nonfungible tokens: each token is unique

## SQL Aggregation Functions
```sql
-- count how many successful transactions took place in a specific week
SELECT COUNT(*)
FROM genieswap."GenieSwap_call_multiAssetSwap"
WHERE "call_block_time" >= '10-18-2021'
AND "call_block_time" <= '10-24-2021'
AND "call_success" = True
```

```sql
-- count how many successful transactions took place each week
SELECT COUNT(*),
date_trunc('week',"call_block_time") AS weeks
FROM genieswap."GenieSwap_call_multiAssetSwap"
WHERE "call_success" = True
GROUP BY weeks
```

```sql
-- count the average daily transactions
WITH count_per_day AS (
SELECT COUNT(*) AS count,
date_trunc('day',"call_block_time") AS days
FROM genieswap."GenieSwap_call_multiAssetSwap"
WHERE "call_success" = True
GROUP BY days
)
SELECT AVG(count)
FROM count_per_day
```
