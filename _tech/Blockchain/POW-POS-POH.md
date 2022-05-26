---
layout: blog
topic: Blockchain
title: POW, POS and POH
tags: blockchain pow pos bitcoin eth poh
comments: true
date: 2022-02-03
---

# POW, POS and POH

## Proof of Work - Bitcoin
*   Verification is achieved not through a central authority but rather through solving a puzzle that requires a significant amount of work

## Proof of Stake - Ethereum
*   Verification is achieved through validators who lock up set amounts of cryptocurrency in a smart contract on the blockchain in exchange for the right to validate new transactions
*   If validators are found improperly validate bad or fraudulent transactions, they may lose some or all of their stake as a penalty.

## Proof of History - Solana
*  Verification is achieved through Verifiable Delay Functions (VDFs).
*  All Solana transactions are hashed with an preimage resistant algorithm such as SHA256 that runs over itself continuously with the previous output used as input for the next hash. The input hash, the counter and the output hash are public
*  If one takes a picture with that day's New York Times, one can be certain that the photo took place after that day's NYT was published; similarly, if one receives a message with the input hash, we know it was generated after the counter which is linked with that input hash
