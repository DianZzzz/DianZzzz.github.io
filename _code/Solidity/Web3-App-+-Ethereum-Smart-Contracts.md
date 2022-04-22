---
layout: blog
topic: Solidity
title: Build a Web3 App
tags: ethereum solidity web3 smartcontract
comments: true
date: 2022-04-20
---

# Build a Web3 App

## Setting up

1. Get node/npm [here](https://hardhat.org/tutorial/setting-up-the-environment.html)
2. Install [Hardhat](https://nodejs.org/en/about/releases/)
3. Run commands

```shell
mkdir my-wave-portal
cd my-wave-portal
npm init -y
npm install --save-dev hardhat
```

## Sample project
1. Run Hardhat
```shell
npx hardhat
```
2. Install dependencies
```shell
npm install --save-dev @nomiclabs/hardhat-waffle ethereum-waffle chai @nomiclabs/hardhat-ethers ethers
```
