---
description: >-
  Explore the liquidation process steps and the security measures in place to
  safeguard the system's integrity.
---

# Liquidations

## Overview

Rosa Finance deploys a robust, overcollateralized lending model, fortified by a robust security infrastructure that mirrors the best-in-class practices. Each loan extended within the Rosa Finance protocol is secured with collateral assets that significantly exceed the loan amount. This overcollateralization creates an additional safety buffer, ensuring the interests of lenders are protected, even in times of tumultuous market behavior.

## **Liquidation Mechanism**

### **Monitoring and Risk Management**

Liquidators, acting as external watchdog entities, continually scrutinize the collateral-to-loan ratio across the portfolio. If a loan becomes undercollateralized due to market fluctuations, and the collateral value descends below a system-defined threshold, the liquidation process is automatically triggered.

### **Initiation of Liquidation**

Upon detecting a loan that has fallen below its collateralization threshold, liquidators have the authority to commence the liquidation process within the Rosa Finance ecosystem. They may opt to repay a part or the entire distressed loan, thereby acting on behalf of the borrower.

### **Debt Offset and Collateral Seizure**

During this phase, the liquidator simultaneously repays a segment of the borrower's debt and seizes a corresponding portion of the borrower's collateral. This collateral is acquired at a preferential rate, defined as the liquidation incentive. This mechanism serves not only as compensation but also as a stimulus for liquidators, encouraging them to vigilantly supervise the financial integrity of the loans within Rosa.

### **Resale and Settlement**

Following the successful liquidation, liquidators frequently divest the acquired collateral on the open market, generating revenue. Concurrently, the borrower is left to reconcile any residual debt (if applicable) and claim the remaining collateral.

## **Liquidation Safeguards and Protocols**

Rosa Finance implements an array of safeguards within its liquidation process to help ensure the integrity and accuracy of each liquidation event. These measures are thoughtfully designed, reflecting industry standards, and include:

* **Checks and Balances**: Specific operations encompass a series of checks and balances that aim to verify the legitimacy of a liquidation, adhering to protocol policy.
* **Transfer Control Mechanisms**: Controls are put in place to manage the transfer of collateral from the borrower to the liquidator, aligning with the predefined rules of the system.
* **Transparency and Traceability**: Every action within the liquidation process generates a solidity event. This facilitates transparency and traceability, providing a clear record of each liquidation executed.
* **Anomaly Handling**: While the system is designed to minimize potential mishaps, should they occur, Rosa Finance's architecture includes procedures to handle them appropriately, preventing misuse or unexpected behaviors.

These safeguards, coupled with Rosa Finance's overcollateralized lending model, contribute to the protocol's reliability and security.

{% hint style="info" %}
For a more technical examination of the safeguards and the liquidation process as a whole, please refer to our [**core repository**](../technical-overview/developer-links.md#core-repository) contracts.
{% endhint %}

## **Important Considerations**

Much like other DeFi platforms, Rosa Finance offers significant potential upside but also carries capital risks. The complexities of the protocol, specifically the liquidation process, necessitate users to have a thorough understanding of their operations to properly safeguard their assets. Before engaging with any DeFi platform, always conduct extensive research or consult with a trusted financial advisor if needed.
