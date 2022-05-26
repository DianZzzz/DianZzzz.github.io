---
layout: blog
topic: Blockchain
title: Gas
tags: bitcoin blockchain gas
comments: true
date: 2022-05-19
---

# Gas

Gas represents the computational resource needed to conduct an Ethereum transaction, like the fuel that drives the car.

## Gas fee

Gas fees are paid in ETH and denote in gwei.

`10^9 gwei = 1 ETH`

wei is the smallest unit of ETH.

`10^9 wei = 1 gwei`

Thus,

`10^18 wei = 1 ETH`

## Calculate Gas Fee Before London Upgrade

`Total Fee = Gas Used * Gas Price Per Unit`

21,000 is the  minimum amount of gas an operation on Ethereum will use.


## Calculate Gas Fee After London Upgrade

The London Upgrade, or EIP-1599, was implemented on August 5, 2021

The base fee represents the amount of ETH burned or destroyed.

The tip represents the amount awarded to miners.

`Total Fee = Gas Used * (Base fee + Tip)`
