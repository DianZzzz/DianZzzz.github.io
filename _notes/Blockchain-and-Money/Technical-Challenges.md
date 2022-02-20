---
layout: blog
course: Blockchain-and-Money
title: Technical Challenges
tags: blockchain 
comments: true
date: 2022-02-19
---

# Technical Challenges
![trilemma](/assets/trilemma.png)

Source: [https://vitalik.ca/general/2021/04/07/sharding.html](https://vitalik.ca/general/2021/04/07/sharding.html)

## Challenges with Blockchain Technology
*   Performance, Scalability, & Efficiency
*   Privacy & Security
*   Interoperability
*   Governance & Collective Action
*   Commercial Use Cases
*   Public Policy & Legal Frameworks 

### Performance, Scalability, & Efficiency

#### Throughput
*   Bitcoin: 7 – 10 transactions / sec
*   Ethereum: 20 transactions / sec
*   Visa: 65,000 / sec
*   DTCC (stock transaction): up to 100,000 / sec

#### Proof of Work Energy Consumption
![bitcoin energy by year](/assets/bitcoin-energy-year.png)
![bitcoin energy by country](/assets/bitcoin-energy-country.png)
![bitcoin energy as country percentage](/assets/bitcoin-energy-country-percentage.png)
Source: [https://digiconomist.net/bitcoin-energy-consumption](https://digiconomist.net/bitcoin-energy-consumption)

#### Alternatives Network Structure
*   Sidechain
*   Sharding
*   Layer 2
*   Payment Channels
*   Lightning Network

#### Alternative Consensus Protocal
Generally Randomized or Delegated Selection of Nodes to Validate next Block. May have added mechanism to confirm Block Validators’ Work

*   Proof of Stake – Stake in Native Currency
*   Proof of Activity - Hybrid of POW and POS
*   Proof of Burn – Validation comes with Burning of Coins
*   Proof of Capacity (Storage or Space) – Based upon Hardware Space

Major Permissionless Blockchain Applications still use Proof of Work – though:
*   DASH is a hybrid of POW with a tiered system of ‘Masternodes’
*   NEO uses a Delegated protocol of ‘Professional Nodes’

### Privacy & Security
*   Law Enforcement & Regulators want more transparency
*   Financial Institutions, Regulators & Some Users want less public transparency

Concerns about Privacy Coins & Mechanisms Fostering Illicit Activities
*   Coins: Dash, Monero, Zcash
*   Mechanisms: Mixers or Tumblers

Cybersecurity Challenges of Private Key Custody, Generation & Storage
*   Significant Losses due to Hacks, Mismanagement and Thefts

#### Possible Solutions
*   Zero Knowledge Proofs: to prove a statement is true without revealing the message of that statment
*   Pedersen Commitments: cryptographic algorithms that allow a prover to commit to a certain value without revealing it or being able to change it.

### Interoperability
*   To view, access, and share information across different blockchains or blockchain networks

#### Hard Forks and Soft Forks
*   A hard fork is a change to a blockchain protocol that renders older versions invalid. e.g. bitcoin cash, etherum classic
*   A soft fork is a change to a blockchain protocal that is backward compatible. 

