---
layout: blog
course: OutNetwork-Learn-Dune-Analytics
title: Ethereum Data Basics
tags: ethereum data dune sql
comments: true
date: 2022-03-31
---

# Ethereum Data Basics

## The Web3 Raw Data Space

### Ethereum Client
* An implementation of Ethereum that allows one to read data and interact with the blockchain from the desktop. Essentially, like downloading a software and running on your own desktop without relying on any third parties

### Node Endpoints-as-a-service
* Infrastructure provider running an Ethereum Client and openning up an API endpoint for anyone to query

### Data Mappers
* Parsing transaction and event log data into a format that can be queried with transitional languages like SQL and GraphQL

## Three Main Transaction Tables in dune

### ethereum."transactions"
* from: sender address
* to: recipient address
* success: state
* value: ETH value transfered
* gas columns: gas_limit, gas_price, gas_used
* calldata: function call data
* hash: transaction hash
* blocknumber: transaction block number
* block_time: time of the transaction

### ethereum."traces"
* from: sender address
* to: recipient address
* success: state
* value: ETH value transfered
* input: function input data
* output: function return
* code: typically a call or create
* call_type: opcodes
* gas columns
* tx_hash
* blocknumber
* block_time

### ethereum."logs"
* contract_address
* topic1: event signature
* topic2: first indexed parameter emitted
* topic3: second indexed parameter emitted
* topic4: third indexed parameter emitted
* data: any other parameter emitted
* tx_hash
* blocknumber
* block_time

## Code Example
```sql
# look at the first 10 ethereum transactions
SELECT * FROM ethereum."transactions"
LIMIT 10
```

```sql
# just need the hashes
SELECT "hash" FROM ethereum."transactions"
LIMIT 10
```

```sql
# look up the exact transaction based on a specific hash
# the leading 0 in the hash needs to be changed to "\"
SELECT * FROM ethereum."transactions" tx
WHERE "hash" = '\x2a72c6e47f8283723b5ca132cf6ec7614bcdec7af6d210cca26bcac37ac7fb26'
```

```sql
# look up the value transferred for a specific transaction
# transform the value from heximal to decimal using the bytea2numeric function
SELECT "data", bytea2numeric("data")/1e6 as "data_trans" FROM ethereum."logs" el
WHERE el."tx_hash" = '\x2a72c6e47f8283723b5ca132cf6ec7614bcdec7af6d210cca26bcac37ac7fb26'
```

```sql
# look up transactions that happen within the last month from certain users in aave
# in descending order based on transaction amount
SELECT * FROM aave_v2."LendingPool_evt_Deposit"
WHERE "user" IN ('\x0f8361ef329b43fa48ac66a7cd8f619c517274f1','\x7ffc460cea6f22f598b6e02f1c9b1e197a597b19','\xbce6053b60c5913f4190c95f629f473be0e379aa')
AND "evt_block_time" > now() - interval '1 month'
ORDER BY "amount" DESC
```
