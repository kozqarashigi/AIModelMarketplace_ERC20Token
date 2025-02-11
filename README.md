# AIModelMarketplace_ERC20Token
### Team members: 
- Nurgul Bassanova SE-2323
- Amir Kairov SE-2331
- Ulzhan Tamyzgazina SE-2325

## Contents
1. [Overview](#overview)  
2. [Prerequisites](#prerequisites)
3. [Setup and installation](#setup-and-installation)
4. [ERC20 Token Implementation](#erc20-token-implementation)
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

## ERC20 Token Implementation

### **1. Smart Contract Code**

Create a file **`MyToken.sol`** in Remix and paste the following Solidity code:

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

import "@openzeppelin/contracts/token/ERC20/ERC20.sol";

contract UniversityToken is ERC20 {
    address public lastSender;
    address public lastReceiver;
    uint256 public lastTimestamp;

    constructor() ERC20("Ulzhan_Nurgul", "UN") {
        _mint(msg.sender, 2000 * 10**decimals());
    }

    function transfer(address recipient, uint256 amount) public override returns (bool) {
        lastSender = msg.sender;
        lastReceiver = recipient;
        lastTimestamp = block.timestamp;
        return super.transfer(recipient, amount);
    }

    function getLastTransactionTimestamp() public view returns (string memory) {
        return _formatTimestamp(lastTimestamp);
    }

    function getLastSender() public view returns (address) {
        return lastSender;
    }

    function getLastReceiver() public view returns (address) {
        return lastReceiver;
    }

    function _formatTimestamp(uint256 timestamp) internal pure returns (string memory) {
        uint256 SECONDS_PER_DAY = 86400;
        uint16 ORIGIN_YEAR = 1970;

        uint256 daysSinceEpoch = timestamp / SECONDS_PER_DAY;
        uint16 year = ORIGIN_YEAR;
        uint256 leapYears = (daysSinceEpoch + 1) / 1461; // Approximate leap year count
        year += uint16((daysSinceEpoch - leapYears) / 365);

        return uintToString(year);
    }
}

```

### **2. Compile the Contract**

- Open **Remix IDE** → Select Solidity version **0.8.20**.
- Click **Compile MyToken.sol**.

### **3. Deploy the Contract**

- Go to **Deploy & Run Transactions**.
- Select **Injected Provider - MetaMask** (for Sepolia) or **Ganache Provider**.
- Click **Deploy** and confirm the transaction in MetaMask.

![Описание изображения](screens/transact.png)

### **4. Interacting with the Contract**

After deploying, use Remix to interact with the contract:

#### **Check Token Balance**

```solidity
balanceOf("your_address")
```

#### **Transfer Tokens**

```solidity
transfer("receiver_address", amount)
```

#### **Retrieve Transaction Details**

- **Last Transaction Timestamp:** `getLastTransactionTimestamp()`
- **Last Sender Address:** `getLastSender()`
- **Last Receiver Address:** `getLastReceiver()`
