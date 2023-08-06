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

<table><thead><tr><th width="157">Price Feed</th><th>Address</th></tr></thead><tbody><tr><td><strong>ARB/USD</strong></td><td><a href="https://arbiscan.io/address/0xb2A824043730FE05F3DA2efaFa1CBbe83fa548D6">0xb2A824043730FE05F3DA2efaFa1CBbe83fa548D6</a></td></tr><tr><td><strong>USDC/USD</strong></td><td><a href="https://arbiscan.io/address/0x50834f3163758fcc1df9973b6e91f0f0f0434ad3">0x50834F3163758fcC1Df9973b6e91f0F0F0434aD3</a></td></tr><tr><td><strong>USDT/USD</strong></td><td><a href="https://arbiscan.io/address/0x3f3f5df88dc9f13eac63df89ec16ef6e7e25dde7">0x3f3f5dF88dC9F13eac63DF89EC16ef6e7E25DdE7</a></td></tr><tr><td><strong>DAI/USD</strong></td><td><a href="https://arbiscan.io/address/0xc5C8E77B397E531B8EC06BFb0048328B30E9eCfB">0xc5C8E77B397E531B8EC06BFb0048328B30E9eCfB</a></td></tr><tr><td><strong>ETH/USD</strong></td><td><a href="https://arbiscan.io/address/0x639Fe6ab55C921f74e7fac1ee960C0B6293ba612">0x639Fe6ab55C921f74e7fac1ee960C0B6293ba612</a></td></tr><tr><td><strong>WBTC/USD</strong></td><td><a href="https://arbiscan.io/address/0xd0C7101eACbB49F3deCcCc166d238410D6D46d57">0xd0C7101eACbB49F3deCcCc166d238410D6D46d57</a></td></tr><tr><td><strong>LUSD/USD</strong></td><td><a href="https://arbiscan.io/address/0x0411D28c94d85A36bC72Cb0f875dfA8371D8fFfF">0x0411D28c94d85A36bC72Cb0f875dfA8371D8fFfF</a></td></tr><tr><td><strong>STETH/USD</strong></td><td><a href="https://arbiscan.io/address/0x07C5b924399cc23c24a95c8743DE4006a32b7f2a">0x07C5b924399cc23c24a95c8743DE4006a32b7f2a</a></td></tr></tbody></table>

## **Real-time Price Data Retrieval & Application**

When Rosa requires the price of an asset, a query is sent to the oracle contract, which then communicates with the corresponding Chainlink price feed. This interaction ensures:

* **Timely Access to Current Price Data**: The direct interface with the Chainlink network secures the latest and most accurate pricing information.
* **Enhanced System Integrity**: The reliable price data contributes to the collateralization ratios, loan calculations, and risk management processes.
* **Robust Security**: The decentralized nature of the price feed minimizes vulnerabilities and aligns with high security standards in the decentralized finance space.

## **Conclusion**

The integration of Chainlink's decentralized oracle network within Rosa Finance's lending protocol illustrates a thoughtful alignment with industry best practices. By employing meticulous data management and real-time price retrieval processes, Rosa ensures accuracy and integrity in asset valuation and collateral management. The adoption of this decentralized price feed mechanism demonstrates Rosa's adherence to principles of security, transparency, and operational efficiency, contributing to its ongoing efforts to foster trust and innovation within the broader decentralized finance ecosystem.
