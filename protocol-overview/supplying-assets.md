---
description: Supply assets in Rosa Finance and earn interest through roTokens.
---

# Supplying Assets

## Overview

The Rosa Finance platform harnesses a value-accumulation model as the backbone of its asset supplying mechanism. Upon supplying tokens to the platform, users are credited with an equivalent amount of roTokens, representative of their contributed underlying assets. The rate of this conversion is regulated by the roToken/Underlying exchange rate, which continually grows in response to the supply interest rate of the asset in question, computed on a per-block basis. This design facilitates uninterrupted interest accrual with each block confirmation, adapting in real-time to shifts in the pool's utilization rate.

To visualize, imagine a situation where WETH suppliers accrue a 10% Annual Percentage Rate (APR) at a given block. The roWETH/WETH exchange rate would mirror this growth, ascending at a comparable 10% annual rate for that specific block. When users choose to redeem their tokens, they simply exchange their roWETH back into WETH. Owing to the dynamic nature of the exchange rate, users receive a greater quantity of WETH than their initial deposit, which factors in both the original principal and the accrued interest.

## **roTokens and Decentralized Lending**

Each asset supported by Rosa Finance is linked through a specific roToken contract. These contracts fulfill EIP-20 compliance for balance representations supplied to the protocol. Users minting roTokens gain two primary benefits: (1) they earn interest through the increasing exchange rate of the roToken relative to the underlying asset, and (2) they can leverage their roTokens as collateral.

The primary user interface for interacting with the Rosa Finance platform is via the roToken contract. This stands true for all user activities, encompassing actions such as minting, redeeming, borrowing, repaying a loan, liquidating a loan, and transferring roTokens.

Each market has a designated APR, or supply interest rate. The Rosa Finance system is architectured to allow users to accrue interest merely by holding roTokens, eliminating the need for constant interest distribution or rebase mechanisms.

## **roToken Management**

Each roToken can be tracked on the Arbitrum network block explorer, Arbiscan. Users can easily locate them within the list of tokens associated with their address.

We advise our users to exercise prudence when transferring roTokens. Any transfer of roTokens effectively translates to the transfer of the corresponding underlying asset balance within the Rosa Finance ecosystem. A transfer from one party to another will reduce the sender's balance (as reflected on the Rosa Finance interface) and increase the receiver's balance.

If an account has entered the market of a specific roToken and the transfer would result in the account's liquidity turning negative, the roToken transfer will be halted.

## **Exchange Rate Mechanics**

The key to interest accrual with roTokens lies in the ongoing growth of their exchange rate. Over time, each roToken can be converted back into an increasing amount of its underlying asset, while the amount of roTokens in your wallet remains unchanged.

At market inception, the exchange rate for roTokens (expressed as the equivalent value of WETH for one unit of roWETH) is set at 0.020000. This value appreciates over time in proportion to the compounding market interest rate. For instance, after a year, the exchange rate could reach 0.022498. Importantly, this exchange rate is universally applicable to all users, with no wallet-specific variations.
