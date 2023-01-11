---
layout: blog
topic: Solidity
title: Build a Web3 App - Setting Up
tags: ethereum solidity web3 smartcontract
comments: true
date: 2022-04-20
---

# Build a Web3 App - Setting Up

## Setting up

1. Get node/npm [here](https://hardhat.org/tutorial/setting-up-the-environment.html)
2. Install [Hardhat](https://nodejs.org/en/about/releases/)
3. Run commands

```shell
mkdir my-wave-portal
cd my-wave-portal
npm init -y
npm install --save-dev hardhat
npx hardhat
npm install --save-dev @nomiclabs/hardhat-waffle ethereum-waffle chai @nomiclabs/hardhat-ethers ethers
```
## Writing Contracts

Move over to Visual Studio Code. Create `WavePortal.sol` under the `contracts` directory and then write the following code.

```solidity
// SPDX-License-Identifier: UNLICENSED

pragma solidity ^0.8.0;

import "hardhat/console.sol";

contract WavePortal {
    uint256 totalWaves;

    constructor() {
        console.log("wazzup beijing!");
    }

    function wave() public {
        totalWaves += 1;
        console.log("%s has waved!", msg.sender);
    }

    function getTotalWaves() public view returns (uint256) {
        console.log("We have %d total waves!", totalWaves);
        return totalWaves;
    }
}
```
Create a file named `run.js` under `scripts` folder with the following code.

```solidity

  const main = async () => {
    const [owner, randomPerson] = await hre.ethers.getSigners();
    const waveContractFactory = await hre.ethers.getContractFactory("WavePortal");
    const waveContract = await waveContractFactory.deploy();
    await waveContract.deployed();

    console.log("Contract deployed to:", waveContract.address);
    console.log("Contract deployed by:", owner.address);

    let waveCount;
    waveCount = await waveContract.getTotalWaves();

    let waveTxn = await waveContract.wave();
    await waveTxn.wait();

    waveCount = await waveContract.getTotalWaves();

    waveTxn = await waveContract.connect(randomPerson).wave();
    await waveTxn.wait();

    waveCount = await waveContract.getTotalWaves();

  };

  const runMain = async () => {
    try {
      await main();
      process.exit(0);
    } catch (error) {
      console.log(error);
      process.exit(1);
    }
  };

  runMain();
```
## Keep the local network alive

Create a new command window and run
```shell
cd my-wave-portal
npx hardhat node
```
Terminal output:
![smart-contract-1.5](/assets/smart-contract-1.5.PNG)!

## Deploy the contract

Create a file named `deploy.js` under `scripts` folder with the following code.

```shell
const main = async () => {
    const [deployer] = await hre.ethers.getSigners();
    const accountBalance = await deployer.getBalance();

    console.log("Deploying contracts with account: ", deployer.address);
    console.log("Account balance: ", accountBalance.toString());

    const waveContractFactory = await hre.ethers.getContractFactory("WavePortal");
    const waveContract = await waveContractFactory.deploy();
    await waveContract.deployed();

    console.log("WavePortal address: ", waveContract.address);
  };

  const runMain = async () => {
    try {
      await main();
      process.exit(0);
    } catch (error) {
      console.log(error);
      process.exit(1);
    }
  };

  runMain();
```
Open a new terminal window and run

```shell
cd my-wave-portal
npx hardhat run scripts/deploy.js --network localhost
```
Current Terminal Output:
![smart-contract-2](/assets/smart-contract-2.PNG)

Node Terminal Output:
![smart-contract-3](/assets/smart-contract-3.PNG)
