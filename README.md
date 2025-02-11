# AIModelMarketplace_ERC20Token
### Team members: 
- Nurgul Bassanova SE-2323
- Amir Kairov SE-2331
- Ulzhan Tamyzgazina SE-2325

## Contents
1. [Overview](#overview)  
2. [Prerequisites](#prerequisites)
3. [Setup and installation](#setup-and-installation)
4. [Smart Contract Functions](#smart-contract-functions)
5. [Deployment](#deployment)
6. [FrontEnd](#frontend)
7. [Conclusion](#conclusion)
8. [Files](#files)
9. [License](#license)
10. [References](#references)

## Overview
- <b><i>Goal</i>:</b> to create a decentralized application that allows users to list, purchase, and rate AI models with UI/UI design
- <b><i>Tasks</i></b>:
1. **Smart Contract Development**  
   - Implement functions for listing, purchasing, and rating AI models.  
   - Add functionality for creators to withdraw funds and retrieve model details.  

2. **Blockchain Environment Setup**  
   - Configure `web3.js` and connect it to Ganache or a testnet like Goerli.  
   - Link Metamask to the blockchain network.  

3. **Contract Deployment**  
   - Compile and deploy the smart contract using Truffle or Hardhat.  

4. **Frontend Development**  
   - Create forms for listing models and rating purchased models.  
   - Add buttons for purchasing models, viewing details, and withdrawing funds.  
   - Display available models in a list or grid format.  

5. **Testing**  
   - Test contract functions with tools like Truffle Console or Remix.  
   - Validate frontend integration in a local blockchain environment.  

6. **Project Finalization**  
   - Deploy the application to a public testnet.  
   - Host the frontend on a platform like GitHub Pages or Vercel.  
   - Include detailed instructions in the README file.  


## Prerequisites

1. **Node.js** (version 14.x or later) - [Install Node.js](https://nodejs.org/)
2. **Ganache** - [Download Ganache](https://www.trufflesuite.com/ganache)
3. **MetaMask** browser extension - [Install MetaMask](https://metamask.io/)
4. **VS Code** - [Download VS Code](https://code.visualstudio.com/)

## Setup and installation 

### 1. Clone the repository:

```bash
git clone https://github.com/kozqarashigi/BT_assignment2
cd BT_assignment2
```
### 2. Install dependencies:

```bash
npm install
```
### 3. Set up Ganache:
- Open Ganache and create a new workspace.
- Note the RPC server URL (usually http://127.0.0.1:7545).
- Ensure you have at least two account with Ether (Ganache provides some pre-funded accounts).

### 4. Set up MetaMask:
- Open MetaMask and create a two wallets if you haven't already.
- Connect MetaMask to your local Ganache network using the RPC URL from Ganache (http://127.0.0.1:7545).
= Import one of the Ganache accounts into MetaMask using the private key provided by Ganache.


### 5. Deploy the Contract:
```bash
node server.js
```
