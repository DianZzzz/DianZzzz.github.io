---
layout: blog
course: Blockchain-and-Money
title: Blockchain Basics & Transactions
tags: blockchain crypto defi finance bitcoin btc cryptography
comments: true
date: 2022-02-15
---

# Blockchain Basics & Transactions

## Bitcoin Transaction Format

### Input
*  Previous Transaction ID
*  Index (indicate how much bitcoin for transaction)
*  Signature

### Output
*  Value in Satoshis
*  Public Key (bitcoin address)


## Coinbase Transaction
*  Generation of a freshly minited bitcoin
*  The only input is the coinbase block reward
*  Reward halves every 210,000 blocks (originally 50 bitcoins per block)
*  May include 100 bytes of arbitray data
*  The Genesis Bock included Headline from Financial Times: "The Times 03/Jan/2009 Chancellor on brink of second bailout for banks"

![genesis-block](/assets/genesis-block.PNG)

Source: [https://en.bitcoin.it/wiki/Genesis_block](https://en.bitcoin.it/wiki/Genesis_block)

translated into 

![genesis-translated](/assets/genesis-translated.PNG)

Source: [https://en.bitcoin.it/wiki/Genesis_block](https://en.bitcoin.it/wiki/Genesis_block)

## Unspent Tranaction Output (UTXO) Set
*  Contains all currently unspent transaction outputs
*  Stored using a LevelDB databse in Bitcoin Core called "chainstate"
