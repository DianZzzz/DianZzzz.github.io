---
layout: blog
course: Blockchain-and-Money
title: Blockchain Basics & Consensus
tags: blockchain crypto defi finance bitcoin btc cryptography
comments: true
date: 2022-02-13
---

# Blockchain Basics & Consensus

## Byzantine Generals Problem

The Problem: Two generals are on the opposite side of a city. They have to launch their attack at the same time. Otherwise they lose. There is no other way of communication but to send a messenger. However, the messenger could be caught by the enemy and replaced by a fake messenger. So how can the generals be sure the information they received from the messenger is correct?
Application in blockchain: the generals represent the nodes in a distributed system. How does the system verify the information sent by each node is accurate?
A more specific application in cryptocurrency - the double spending problem: how does the recipient node verify that the money it received has not already been spent elsewhere?

## Solutions to the Byzantine Generals Problem

### Proof of Work (PoW)
PoW has the following characteristics to make it Byzantine fault tolerant 
*   The work is difficult. In bitcoin, mining requires a significant amount of computing power to solve cryptographical puzzles.
*   Tempering is difficult. The attacker has to take over 51% of the system to affect changes. 
*   Verification is easy. Thus consensus can be reached quickly.

In bitcoin, the work is to find the nounce that results in a hash with a targeted number of leading zeros. The current target is 19 zeroes. The genesis block mined on January 3, 2009 has 10 leading zeroes, even though Satoshi required only leading zeroes. 

## Economic Incentive System
*   BTC was created through Coinbase Transaction in each block
*   Originally each block rewards 50 BTC. The rewards halve every 210,000 blocks. Currently 12.5 BTC are created each block. 
*   Current inflation rate: current # of BTC in circulation / # of BTC in circulation a year ago - 1 = 18.958/18.629-1 = 1.77% source: [https://www.blockchain.com/charts/total-bitcoins](https://www.blockchain.com/charts/total-bitcoins)
*   The maximum number of bitcoin is 21 million, expected to be reached in 2140

## Network
*   Full nodes: store full blockchain and is able to validate all transactions
*   Lightweight nodes: Simplied Payment Verification (SPV) nodes, store blockchain headers only
*   Mempool: pool of unconfirmed transactions
