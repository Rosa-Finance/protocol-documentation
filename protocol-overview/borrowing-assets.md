---
description: >-
  Learn about borrowing, interest accumulation and repayment mechanisms on Rosa
  Finance.
---

# Borrowing Assets

## Overview

Rosa Finance's asset borrowing functionality is grounded in a fully collateralized borrowing paradigm. By supplying collateral (e.g., WETH) and obtaining the corresponding roTokens (e.g., roWETH), users gain the ability to borrow other supported assets within the platform. The borrowing capacity is contingent upon the collateral factor of the provided asset and its underlying value.

Illustratively, should a user supply WETH with a collateral factor of 75%, they are entitled to borrow up to 75% of their roWETH's value in other available assets. This borrowed sum will then accrue interest, computed on a per-block basis, and dynamically adjusts in alignment with the specific asset's borrowing demand.

The accumulated interest is effectively considered a debt linked to the user's account and must be fulfilled upon the decision to repay the loan. This interest is accumulated through the roToken/underlying asset exchange rate, signifying that the required roTokens to settle the borrowed sum will increment over time. Loans can be repaid at any time by furnishing the corresponding amount of roTokens to the protocol.

## **Collateral, Debt, and roTokens**

Within the borrowing landscape, roTokens fulfill two essential roles: (1) acting as collateral for the borrowed assets, and (2) symbolizing the borrower's debt.

The roTokens allocated as collateral continue to accrue interest within the protocol. Simultaneously, the roTokens symbolizing debt amass interest until the loan is satisfied. The accrued interest is effectively compounded into the debt, and the total obligation consists of the original borrowed sum along with the cumulative interest.

## **Management of Borrowed Assets**

Upon the successful borrowing of an asset, it will manifest in your wallet as the specified asset (e.g., DAI, USDT, etc.). These borrowed funds are at your disposal, provided that the full amount, inclusive of accumulated interest, is repaid to the Rosa Finance protocol upon loan settlement.

## **Interest Rates, Repayment, and Liquidation**

The interest on borrowed assets is compounded according to the asset's borrowing interest rate, a variable rate that dynamically adapts to the asset's supply and demand within the protocol.

Upon deciding to settle your loan, the required sum of the borrowed asset must be transferred back to the protocol. This sum is the aggregate of the original borrowed amount and the accrued interest, readily accessible within the Rosa Finance Interface under your account's borrowed asset section.

It's critical to recognize that a failure to repay the loan or a decrease in collateral value beneath a defined threshold may trigger a liquidation of your collateral to cover the loan. This mechanism fortifies the fully collateralized nature of Rosa Finance, safeguarding lenders against potential defaults, and maintaining the integrity and robustness of the system.
