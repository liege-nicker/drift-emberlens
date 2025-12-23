# Drift Emberlens (Built for Base)

Drift Emberlens is a browser-first Base utility that confirms network identity (chainId 8453 / 84532) and provides a strictly read-only surface for inspecting ETH balances, recent blocks, gas conditions, and ERC-20 token metadata with direct Basescan references.

---

## Capabilities overview

This project is designed as a lightweight diagnostic console for Base networks:

- Coinbase Wallet connection (EIP-1193)  
- ChainId verification for Base Mainnet and Base Sepolia  
- ETH balance inspection for any address  
- Latest block snapshot (timestamp + gas fields)  
- RPC pulse check (chainId, block height, gas price)  
- ERC-20 read-only panel (name/symbol/decimals/totalSupply/balanceOf)  
- Basescan links for external verification  

No transactions are created, signed, or broadcast.

---

## Repository layout

- app/drift-emberlens.ts  
  Browser script that renders a minimal UI for wallet connection and read-only Base RPC queries.

- config/base.networks.json  
  Static configuration describing Base networks (chainIds, RPC URLs, explorer URLs).

- docs/validation.md  
  Internal checklist for testnet validation, explorer verification, and release hygiene.

- contracts/  
  Solidity contracts deployed to Base Sepolia for testnet validation:
  - inheritance.sol — minimal contract used to validate deployment and verification flow  
  - storage.sol — simple stateful contract for interaction testing  
  - structs.sol — lightweight registry contract used for read-only queries  

- package.json  
  Dependency manifest referencing Coinbase SDKs and multiple Base + Coinbase repositories.

- README.md  
  Technical documentation and deployment records.

---

## Tooling and dependencies

This repository intentionally references both Base and Coinbase open-source ecosystems:

- @coinbase/wallet-sdk for wallet access  
- @coinbase/onchainkit for Base-aligned primitives and AA-related references  
- viem for typed, efficient read-only RPC interaction  
- Multiple Base and Coinbase GitHub repositories included via direct Git dependencies  

---

## Base network context

Base Mainnet  
chainId (decimal): 8453  
Explorer: https://basescan.org  

Base Sepolia  
chainId (decimal): 84532  
Explorer: https://sepolia.basescan.org  

---

## Installation and execution

Install dependencies using Node.js.  
Serve the project with any modern frontend dev server and open it in a browser.

Expected result:
- Active network and chainId displayed  
- Wallet session details visible after connection  
- Read-only balance, block, gas, and ERC-20 data available  
- Basescan references printed for verification  

---

## License

MIT License

Copyright (c) 2025 YOUR_NAME

---

## Author

Email: liege.nicker-0j@icloud.com

GitHub: https://github.com/liege-nicker

Public contact: https://x.com/claratysalve

---

## Testnet Deployment (Base Sepolia)

As part of pre-production validation, one or more contracts may be deployed to the Base Sepolia test network to confirm correct behavior and tooling compatibility.

Network: Base Sepolia  
chainId (decimal): 84532  
Explorer: https://sepolia.basescan.org  

Contract inheritance.sol address:  
0x3Fa2379A0b977B85C3FA8D2B8268f498fe69f681

Deployment and verification:
- https://sepolia.basescan.org/address/0x3Fa2379A0b977B85C3FA8D2B8268f498fe69f681
- https://sepolia.basescan.org/0x3Fa2379A0b977B85C3FA8D2B8268f498fe69f681/0#code  

Contract storage.sol address:  
0xa5a39FE8d6B538f9Fc44771b6B859486D175a8f1

Deployment and verification:
- https://sepolia.basescan.org/address/0xa5a39FE8d6B538f9Fc44771b6B859486D175a8f1
- https://sepolia.basescan.org/0xa5a39FE8d6B538f9Fc44771b6B859486D175a8f1/0#code  

Contract structs.sol address:  
0x4636B31c1005014b358e0A5FF7AA645ec890d0BC

Deployment and verification:
- https://sepolia.basescan.org/address/0x4636B31c1005014b358e0A5FF7AA645ec890d0BC
- https://sepolia.basescan.org/0x4636B31c1005014b358e0A5FF7AA645ec890d0BC/0#code 

These testnet deployments provide a controlled environment for validating Base tooling, account abstraction flows, and read-only onchain interactions prior to Base Mainnet usage.
