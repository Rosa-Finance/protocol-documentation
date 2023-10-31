---
description: >-
  Explore how Rosa Finance harnesses the power of Chainlink's decentralized
  oracle network to provide precise, real-time asset pricing on the Arbitrum
  network.
---

# Price Feed Mechanism

## Overview

Rosa Finance integrates Chainlink's decentralized oracle network, enabling the provision of precise, real-time asset pricing on the Arbitrum network. This integration serves as an essential part of Rosa's lending mechanism, and in the following sections, we detail the key elements of the price feed process, its interaction with Chainlink, and the management of supported assets within the Rosa ecosystem.

## **Orchestrating the Price Data**

### **Initialization & Configuration**

The price oracle contract in Rosa Finance holds the essential price feed parameters. It's initialized with:

1. **Asset-Specific Chainlink Contract Address**: A unique identifier for each individual asset, this address ensures specific and secured access to the appropriate pricing information.
2. **Asset Decimal Configuration**: This aligns with the number of decimal places utilized by the asset, enabling an accurate scale for value calculation.

The combined use of these two components, stored within Rosa's oracle contract, allows for an effective interpretation of price data, facilitating accurate value calculations of assets within the system.

### Price Feed Contract Adresses

Each asset supported within Rosa Finance is assigned a dedicated Chainlink price feed contract.

<table><thead><tr><th width="157">Price Feed</th><th>Address</th></tr></thead><tbody><tr><td><strong>TBD</strong></td><td><strong>TBD</strong></td></tr><tr><td><strong>TBD</strong></td><td><strong>TBD</strong></td></tr><tr><td><strong>TBD</strong></td><td><strong>TBD</strong></td></tr><tr><td><strong>TBD</strong></td><td><strong>TBD</strong></td></tr><tr><td><strong>TBD</strong></td><td><strong>TBD</strong></td></tr><tr><td><strong>TBD</strong></td><td><strong>TBD</strong></td></tr><tr><td><strong>TBD</strong></td><td><strong>TBD</strong></td></tr><tr><td><strong>TBD</strong></td><td><strong>TBD</strong></td></tr></tbody></table>

## **Real-time Price Data Retrieval & Application**

When Rosa requires the price of an asset, a query is sent to the oracle contract, which then communicates with the corresponding Chainlink price feed. This interaction ensures:

* **Timely Access to Current Price Data**: The direct interface with the Chainlink network secures the latest and most accurate pricing information.
* **Enhanced System Integrity**: The reliable price data contributes to the collateralization ratios, loan calculations, and risk management processes.
* **Robust Security**: The decentralized nature of the price feed minimizes vulnerabilities and aligns with high security standards in the decentralized finance space.

## **Conclusion**

The integration of Chainlink's decentralized oracle network within Rosa Finance's lending protocol illustrates a thoughtful alignment with industry best practices. By employing meticulous data management and real-time price retrieval processes, Rosa ensures accuracy and integrity in asset valuation and collateral management. The adoption of this decentralized price feed mechanism demonstrates Rosa's adherence to principles of security, transparency, and operational efficiency, contributing to its ongoing efforts to foster trust and innovation within the broader decentralized finance ecosystem.
