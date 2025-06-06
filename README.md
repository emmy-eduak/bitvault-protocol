# BitVault Protocol

> Decentralized Bitcoin-Backed Lending Platform

BitVault Protocol is a sophisticated DeFi lending platform built on Stacks Layer 2, enabling Bitcoin holders to unlock liquidity through over-collateralized loans while maintaining their Bitcoin exposure and earning yield.

## 🚀 Overview

BitVault Protocol represents the next evolution of Bitcoin DeFi, leveraging Stacks' unique architecture to create a trustless lending platform where Bitcoin holders can access instant liquidity without selling their BTC.

### Key Features

- **Over-collateralized Lending** - Secure loans backed by Bitcoin collateral with dynamic interest rates
- **Automated Risk Management** - Intelligent liquidation engine with real-time monitoring
- **Multi-Asset Support** - Collateral support for BTC and STX tokens
- **Governance-Driven Parameters** - Community-controlled protocol adjustments
- **Real-Time Price Feeds** - Accurate asset pricing for risk assessment
- **Capital Efficient Liquidations** - Optimized liquidation mechanisms to protect both borrowers and lenders

## 📋 Protocol Parameters

| Parameter | Default Value | Description |
|-----------|---------------|-------------|
| Minimum Collateral Ratio | 150% | Required over-collateralization for new loans |
| Liquidation Threshold | 120% | Collateral ratio that triggers liquidation |
| Platform Fee Rate | 1% | Protocol fee on loan origination |
| Base Interest Rate | 5% | Annual interest rate for loans |

## 🔧 Core Functions

### Platform Management

- `initialize-platform()` - Initialize the protocol (owner only)
- `update-collateral-ratio(uint)` - Adjust minimum collateral requirements
- `update-liquidation-threshold(uint)` - Modify liquidation trigger threshold
- `update-price-feed(asset, price)` - Update asset price feeds

### Lending Operations

- `deposit-collateral(amount)` - Deposit Bitcoin as collateral
- `request-loan(collateral, loan-amount)` - Request a new loan against collateral
- `repay-loan(loan-id, amount)` - Repay an active loan with interest

### Query Functions

- `get-loan-details(loan-id)` - Retrieve specific loan information
- `get-user-loans(user)` - Get all loans for a specific user
- `get-platform-stats()` - View protocol statistics
- `get-valid-assets()` - List supported collateral assets

## 💰 How It Works

1. **Deposit Collateral**: Users deposit Bitcoin as collateral into the protocol
2. **Request Loan**: Borrow against collateral with minimum 150% collateralization
3. **Maintain Position**: Monitor collateral ratio to avoid liquidation
4. **Repay or Liquidate**: Repay loan to reclaim collateral, or face liquidation if ratio falls below 120%

## 🛡️ Risk Management

The protocol implements multiple layers of risk management:

- **Over-collateralization**: All loans require minimum 150% collateral backing
- **Automated Liquidations**: Positions are automatically liquidated when collateral ratio drops below 120%
- **Real-time Monitoring**: Continuous price feed updates ensure accurate risk assessment
- **Interest Accrual**: Dynamic interest calculation based on loan duration and blocks

## 🏗️ Architecture

```
┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐
│   User Interface │    │  Price Oracles  │    │   Governance    │
└─────────┬───────┘    └─────────┬───────┘    └─────────┬───────┘
          │                      │                      │
          ▼                      ▼                      ▼
┌─────────────────────────────────────────────────────────────────┐
│                    BitVault Protocol                            │
├─────────────────┬─────────────────┬─────────────────┬───────────┤
│  Loan Manager   │ Collateral Mgmt │ Liquidation Eng │ Risk Mgmt │
└─────────────────┴─────────────────┴─────────────────┴───────────┘
          │                      │                      │
          ▼                      ▼                      ▼
┌─────────────────────────────────────────────────────────────────┐
│                     Stacks Blockchain                          │
└─────────────────────────────────────────────────────────────────┘
          │
          ▼
┌─────────────────────────────────────────────────────────────────┐
│                     Bitcoin Network                             │
└─────────────────────────────────────────────────────────────────┘
```

## 📊 Protocol States

### Loan Status Types

- `active` - Loan is currently active and accruing interest
- `repaid` - Loan has been fully repaid by borrower
- `liquidated` - Loan was liquidated due to insufficient collateral

## ⚠️ Error Codes

| Code | Error | Description |
|------|-------|-------------|
| 100 | NOT-AUTHORIZED | Caller lacks required permissions |
| 101 | INSUFFICIENT-COLLATERAL | Collateral below minimum requirements |
| 102 | BELOW-MINIMUM | Amount below minimum threshold |
| 103 | INVALID-AMOUNT | Invalid or zero amount provided |
| 104 | ALREADY-INITIALIZED | Protocol already initialized |
| 105 | NOT-INITIALIZED | Protocol not yet initialized |
| 106 | INVALID-LIQUIDATION | Liquidation conditions not met |
| 107 | LOAN-NOT-FOUND | Specified loan does not exist |
| 108 | LOAN-NOT-ACTIVE | Loan is not in active state |
| 109 | INVALID-LOAN-ID | Loan ID out of valid range |
| 110 | INVALID-PRICE | Price feed data invalid |
| 111 | INVALID-ASSET | Asset not supported |

## 🔐 Security Features

- **Access Control**: Owner-only functions for critical protocol parameters
- **Input Validation**: Comprehensive validation of all user inputs
- **Overflow Protection**: Safe arithmetic operations throughout
- **State Consistency**: Atomic operations ensure protocol state integrity

## 📈 Protocol Statistics

Track key metrics including:

- Total Bitcoin locked in protocol
- Total number of loans issued
- Current collateral and liquidation ratios
- Platform utilization rates

## 🚦 Getting Started

1. Ensure the protocol is initialized by the contract owner
2. Check current price feeds for supported assets (BTC, STX)
3. Deposit collateral using `deposit-collateral`
4. Request loan with appropriate collateralization via `request-loan`
5. Monitor your loan health and repay before liquidation threshold
