---
layout: blog
topic: Blockchain-and-Money
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

## Unspent Tranaction Output (UTXO) 
*  A UTXO is like the change we receive in a cash transaction which can be used for future transaction. It is a transaction output that can be used as input in a new transaction.
*  Like a note or a coin, a UTXO can not be split. However, new UTXOs can be created. For example, assuming i have a UTXO of 0.8 bitcoin and another UTXO of 0.6 bitcoin. If I wish to send 1 bitcon, the two UTXOs will be used as inputs for the transaction and be destroyed, or spent. Two new outputs will be created, one worth 1 bitcoin sent to the recipient and another worth 0.39 bitcoin (since there is transaction fee) sent back to me. 
*  UTXO addresses the double spend problem. 
*  A UTXO set contains all the currently unspent bitcoins and is stored using a LevelDB database in Bitcoin Core called "chainstate"
*  The sume of all UTXOs equal to the total bitcoin in circulation.

## Bitcoin Script
*  Stack-based code and cannot do loops so not turing-complete

