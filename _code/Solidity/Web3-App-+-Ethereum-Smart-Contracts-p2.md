---
layout: blog
topic: Solidity
title: Build a Web3 App - Website Building
tags: ethereum solidity web3 smartcontract
comments: true
date: 2022-04-24
---

# Build a Web3 App - Website Building

The website will be deployed using [Replit](https://replit.com).

Set up a Replit account and fork this [repo](https://replit.com/@adilanchian/waveportal-starter-project?v=1).

Then go to [alchemy](https://www.alchemy.com/), set up an account and create a new app. Choose Rinkeby as the network.

## Getting fake $$

Set MetaMask network to Rinkeby.

Create an account on [https://app.mycrypto.com](https://app.mycrypto.com) by connecting MetaMask

Use this [link](https://app.mycrypto.com/faucet) to request some fake $$

## Deploy to Rinkeby Testnet

Add the following codes to the `hardhat.config.js` file

```solidity
require("@nomiclabs/hardhat-waffle");

module.exports = {
  solidity: "0.8.0",
  networks: {
    rinkeby: {
      url: "YOUR_ALCHEMY_API_URL", //get from Alchemy
      accounts: ["YOUR_PRIVATE_RINKEBY_ACCOUNT_KEY"] // get from MetaMask
    },
  },
};
```
Open a new command window and run

```shell
cd my-wave-portal
npx hardhat run scripts/deploy.js --network rinkeby
```
The terminal will return something like
![smart-contract-4](/assets/smart-contract-4.PNG)

We can take the WavePortal address `0x527D0C58c2deE5DC420D7B817F106d3124A224B0` and check it on [Etherscan](https://rinkeby.etherscan.io/)

![smart-contract-5](/assets/smart-contract-5.PNG)
