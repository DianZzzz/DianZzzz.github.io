---
layout: blog
topic: Solidity
title: Build a Web3 App - Building the Website
tags: ethereum solidity web3 smartcontract
comments: true
date: 2022-04-25
---

# Build a Web3 App - Building the Website

To be totally honest, coding a website from scratch is a bit too much for me. Here I am simply copy&paste the code from [here](https://gist.github.com/adilanchian/71890bf4fcd8f78e94c77cf694b24659).

## Change the website code

Use the following codes for the  `src/App.jsx` file on Replit

```js
import React, { useEffect, useState } from "react";
import { ethers } from "ethers";
import './App.css';
import abi from './utils/WavePortal.json';

const App = () => {
  const [currentAccount, setCurrentAccount] = useState("");
  /**
   * Create a varaible here that holds the contract address after you deploy!
   */
  const contractAddress = "0x527D0C58c2deE5DC420D7B817F106d3124A224B0";
  const contractABI = abi.abi;

  const checkIfWalletIsConnected = async () => {
    try {
      const { ethereum } = window;

      if (!ethereum) {
        console.log("Make sure you have metamask!");
        return;
      } else {
        console.log("We have the ethereum object", ethereum);
      }

      const accounts = await ethereum.request({ method: 'eth_accounts' });

      if (accounts.length !== 0) {
        const account = accounts[0];
        console.log("Found an authorized account:", account);
        setCurrentAccount(account)
      } else {
        console.log("No authorized account found")
      }
    } catch (error) {
      console.log(error);
    }
  }

  const connectWallet = async () => {
    try {
      const { ethereum } = window;

      if (!ethereum) {
        alert("Get MetaMask!");
        return;
      }

      const accounts = await ethereum.request({ method: "eth_requestAccounts" });

      console.log("Connected", accounts[0]);
      setCurrentAccount(accounts[0]);
    } catch (error) {
      console.log(error)
    }
  }

  const wave = async () => {
    try {
      const { ethereum } = window;

      if (ethereum) {
        const provider = new ethers.providers.Web3Provider(ethereum);
        const signer = provider.getSigner();
        const wavePortalContract = new ethers.Contract(contractAddress, contractABI, signer);

        let count = await wavePortalContract.getTotalWaves();
        console.log("Retrieved total wave count...", count.toNumber());

        const waveTxn = await wavePortalContract.wave();
        console.log("Mining...", waveTxn.hash);

        await waveTxn.wait();
        console.log("Mined -- ", waveTxn.hash);

        count = await wavePortalContract.getTotalWaves();
        console.log("Retrieved total wave count...", count.toNumber());
      } else {
        console.log("Ethereum object doesn't exist!");
      }
    } catch (error) {
      console.log(error)
    }
  }

  useEffect(() => {
    checkIfWalletIsConnected();
  }, [])

  return (
    <div className="mainContainer">
      <div className="dataContainer">
        <div className="header">
        👋 wazzup beijing!
        </div>

        <div className="bio">
          Shoutout to all my homies in Beijing & Shanghai for keepin it real.
        </div>

        <button className="waveButton" onClick={wave}>
          Wave at Me
        </button>

        {!currentAccount && (
          <button className="waveButton" onClick={connectWallet}>
            Connect Wallet
          </button>
        )}
      </div>
    </div>
  );
}

export default App
```

## Get the WavePortal Address

From the terminal output in the [previous step](https://dianzzzz.github.io/code/Solidity/Web3-App-+-Ethereum-Smart-Contracts-p2.html)

![smart-contract-4](/assets/smart-contract-4.PNG)

## Get API content

Look for the local file at `artifacts/contracts/WavePortal.sol/WavePortal.json`

Copy the content of this local file and then go to Replit. First create a new folder `utils` under `src` and then create a file named  `WavePortal.json` and paste the content onto this Replit file.

## Final Look of the Website
![smart-contract-6](/assets/smart-contract-6.PNG)
