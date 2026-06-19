# IOTrader Token

IOTrader Token is a BEP-20 compatible token deployed on the BNB Smart Chain. The token is designed for use within the IOTrader ecosystem, supporting decentralised trading, prediction markets, community participation, and future platform utility.

## Token Overview

| Item           | Details                 |
| -------------- | ----------------------- |
| Token Name     | IOTrader                |
| Token Symbol   | IOI                     |
| Network        | BNB Smart Chain         |
| Token Standard | BEP-20                  |
| Decimals       | 18                      |
| Total Supply   | 1,000,000,000 IOI      |
| Contract Type  | Solidity Smart Contract |

## About IOTrader

IOTrader is a decentralised trading and prediction-focused ecosystem built for users who want faster access to market opportunities, event-based trading, and blockchain-powered financial tools.

The IOTrader Token acts as the core digital asset of the ecosystem and may be used for platform access, rewards, community participation, trading features, staking, governance, and future product utilities.

## Features

* BEP-20 compatible token
* Fixed total supply
* Deployed on BNB Smart Chain
* Low transaction fees
* Compatible with MetaMask, Trust Wallet, Binance Web3 Wallet, and other EVM wallets
* Suitable for decentralised exchanges and Web3 integrations
* Built using Solidity and OpenZeppelin standards

## Smart Contract

The IOTrader Token contract is based on the ERC-20/BEP-20 standard and can be deployed on the BNB Smart Chain.

### Example Contract

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

import "@openzeppelin/contracts/token/ERC20/ERC20.sol";

contract IOTraderToken is ERC20 {
    constructor() ERC20("IOTrader", "IOI") {
        _mint(msg.sender, 1_000_000_000 * 10 ** decimals());
    }
}
```

## Requirements

Before deploying the contract, make sure you have the following installed:

* Node.js
* npm or yarn
* Hardhat
* MetaMask wallet
* BNB for gas fees
* BNB Smart Chain RPC configuration

## Installation

Clone the project and install dependencies:

```bash
npm install
```

Install Hardhat and OpenZeppelin contracts:

```bash
npm install --save-dev hardhat
npm install @openzeppelin/contracts
```

## Hardhat Setup

Create a Hardhat project:

```bash
npx hardhat
```

Select:

```text
Create a JavaScript project
```

## BNB Smart Chain Network Configuration

Update your `hardhat.config.js` file:

```javascript
require("@nomicfoundation/hardhat-toolbox");
require("dotenv").config();

module.exports = {
  solidity: "0.8.20",
  networks: {
    bsc: {
      url: process.env.BSC_RPC_URL,
      accounts: [process.env.PRIVATE_KEY]
    },
    bscTestnet: {
      url: process.env.BSC_TESTNET_RPC_URL,
      accounts: [process.env.PRIVATE_KEY]
    }
  }
};
```

## Environment Variables

Create a `.env` file in the root directory:

```env
PRIVATE_KEY=your_wallet_private_key
BSC_RPC_URL=https://bsc-dataseed.binance.org/
BSC_TESTNET_RPC_URL=https://data-seed-prebsc-1-s1.binance.org:8545/
BSCSCAN_API_KEY=your_bscscan_api_key
```

Important: Never share your private key publicly. Do not upload your `.env` file to GitHub.

## Deployment Script

Create a file named `deploy.js` inside the `scripts` folder:

```javascript
const hre = require("hardhat");

async function main() {
  const IOTraderToken = await hre.ethers.getContractFactory("IOTraderToken");
  const token = await IOTraderToken.deploy();

  await token.waitForDeployment();

  console.log("IOTrader Token deployed to:", await token.getAddress());
}

main().catch((error) => {
  console.error(error);
  process.exitCode = 1;
});
```

## Deploy on BNB Smart Chain Testnet

Run:

```bash
npx hardhat run scripts/deploy.js --network bscTestnet
```

## Deploy on BNB Smart Chain Mainnet

Run:

```bash
npx hardhat run scripts/deploy.js --network bsc
```

After deployment, copy the contract address from the terminal.

## Verify Contract on BscScan

Install the verification plugin:

```bash
npm install --save-dev @nomicfoundation/hardhat-verify
```

Update `hardhat.config.js`:

```javascript
require("@nomicfoundation/hardhat-toolbox");
require("dotenv").config();

module.exports = {
  solidity: "0.8.20",
  networks: {
    bsc: {
      url: process.env.BSC_RPC_URL,
      accounts: [process.env.PRIVATE_KEY]
    },
    bscTestnet: {
      url: process.env.BSC_TESTNET_RPC_URL,
      accounts: [process.env.PRIVATE_KEY]
    }
  },
  etherscan: {
    apiKey: {
      bsc: process.env.BSCSCAN_API_KEY,
      bscTestnet: process.env.BSCSCAN_API_KEY
    }
  }
};
```

Verify on BNB Smart Chain Mainnet:

```bash
npx hardhat verify --network bsc CONTRACT_ADDRESS
```

Verify on BNB Smart Chain Testnet:

```bash
npx hardhat verify --network bscTestnet CONTRACT_ADDRESS
```

Replace `CONTRACT_ADDRESS` with your deployed token contract address.

## Add Token to MetaMask

To add IOTrader Token manually in MetaMask:

1. Open MetaMask.
2. Select BNB Smart Chain.
3. Click Import Tokens.
4. Paste the deployed token contract address.
5. MetaMask will automatically detect the token symbol and decimals.
6. Click Add Custom Token.

## Suggested Token Details

| Field        | Value           |
| ------------ | --------------- |
| Network      | BNB Smart Chain |
| Token Name   | IOTrader        |
| Symbol       | IOI             |
| Decimals     | 18              |
| Total Supply | 1,000,000,000   |

## Security Notes

* Use OpenZeppelin contracts for reliable token standards.
* Keep the private key safe.
* Do not commit `.env` files to GitHub.
* Test deployment on BNB Smart Chain Testnet before deploying on mainnet.
* Verify the contract on BscScan after deployment.
* Consider a professional audit before public launch or exchange listing.

## Licence

This project is released under the MIT Licence.

## Disclaimer

IOTrader Token is a blockchain-based digital asset. This README is for technical and informational purposes only. It does not represent financial advice, investment advice, or a guarantee of token value. Users should do their own research before interacting with any blockchain asset.
