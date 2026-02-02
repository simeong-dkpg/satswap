# Satswap Protocol

**Bitcoin-Secured Decentralized Exchange on Stacks L2**  
_Version 1.0.0_

[![Clarity Version](https://img.shields.io/badge/Clarity-2.0.0-blue)](https://docs.stacks.co/docs/clarity/)

## Overview

Satswap is an Automated Market Maker (AMM) protocol built on Stacks L2, designed to enable Bitcoin-native decentralized finance through:

- Non-custodial token swaps
- Capital-efficient liquidity pools
- MEV-resistant transaction mechanics
- Bitcoin script-compatible smart contracts

## Key Features

### 1. Advanced AMM Engine

- Constant product market maker model (x\*y=k)
- Dynamic fee structure (0.3% base, adjustable)
- Liquidity pool creation for any SIP-010 token pair
- Price impact calculation with 2% maximum threshold

### 2. Flash Loan System

- Atomic borrow/repay transactions
- 0.1% protocol fee structure
- Block-bound loan expiration
- Borrower whitelisting capabilities

### 3. Governance Mechanism

- STX-based voting power delegation
- Parameter adjustment proposals:
  - Fee structure updates
  - Protocol treasury management
  - Emergency circuit breakers
- Quadratic voting implementation

### 4. Yield Farming

- Liquidity mining incentives
- Reward multiplier system (100x base)
- Per-block reward distribution
- Staking lock-up periods

### 5. Bitcoin Compliance

- Taproot address compatibility
- BIP-340 Schnorr signature support
- Lightning Network liquidity hooks
- Bitcoin timestamp anchoring

## Technical Architecture

### Core Contracts

| Contract         | Purpose                                  |
| ---------------- | ---------------------------------------- |
| `satswap-core`   | AMM pool management & swap execution     |
| `satswap-gov`    | Governance and parameter control         |
| `satswap-oracle` | TWAP price feeds & volatility monitoring |
| `satswap-flash`  | Flash loan execution engine              |
| `satswap-farm`   | Yield farming reward distribution        |

## Installation

### Prerequisites

- Node.js v16+
- Clarinet v2.0.0+
- Bitcoin testnet node (regtest)

### Setup

```bash
git clone https://github.com/satswap-protocol/core.git
cd satswap
```

## Usage

### 1. Create Liquidity Pool

```clarity
(create-pool 'token-x 'token-y u1000000 u1000000)
```

### 2. Add Liquidity

```clarity
(add-liquidity pool-id 'token-x 'token-y u500000 u500000 u1000)
```

### 3. Execute Swap

```clarity
(swap-exact-x-for-y pool-id 'token-x 'token-y u1000 u950)
```

### 4. Flash Loan

```clarity
(flash-swap pool-id 'token-x 'token-y u10000 'callback-contract)
```

### 5. Yield Farming

```clarity
(stake-in-farm pool-id u500000)
(claim-rewards pool-id)
```

## Governance

### Voting Process

1. Stake governance tokens
2. Submit proposals
3. Delegated voting period (72 hours)
4. Automatic execution of approved proposals

```clarity
(propose-parameter-change "protocol-fee-rate" u75)
(delegate-votes 'delegate-address)
```

## Contributing

1. Fork repository
2. Create feature branch (`feat/feature-name`)
3. Add test cases
4. Submit PR with documentation updates

## References

- [Stacks Documentation](https://docs.stacks.co)
- [Clarity Language Reference](https://book.clarity-lang.org)
- [Bitcoin Improvement Proposals](https://github.com/bitcoin/bips)
