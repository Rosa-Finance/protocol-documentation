---
description: >-
  Explore how to supply assets as collateral, control borrowing capacity, and
  effectively manage risks amidst liquidation and price volatility.
---

# Collateral Management

## **Introduction to Collateralization**

Rosa Finance operates on a robust and secure framework allowing users to supply assets for collateralization, which subsequently can be leveraged for borrowing various other assets. When you deposit an asset into the Rosa Finance protocol, it's initially available as a collateral option. Explicit enabling, however, is required to utilize it for borrowing purposes.

### **Collateral Factor**

Every asset within Rosa Finance is associated with a specific 'collateral factor.' This term defines the percentage of the asset's value that may be borrowed. As an illustrative example, should the collateral factor for WETH stand at 75%, and you supply WETH worth $1000, your borrowing capability would extend to $750 in other assets.

## **Control Over Collateral Assets**

### **Enabling and Disabling Collaterals**

You exercise complete control over the assets you supply, including the ability to designate them as collateral. The Rosa Finance Interface offers seamless options to enable or disable an asset as collateral. It's essential to note that disabling an asset that might render your account under-collateralized is prohibited.

### **Collateral Value and Borrow Capacity**

Your total collateral value is computed as the aggregate value of each supplied asset, each multiplied by its unique collateral factor. This total value dictates your borrowing capacity. The Rosa Finance Interface elegantly presents a 'Borrow Capacity' metric, providing a real-time insight into the maximum value you are eligible to borrow, given your current collateral position.

An account exceeding its borrowing capacity becomes under-collateralized, creating a tangible risk of liquidation.

## **Liquidation Protocols**

When your borrowed assets' value transcends your collateral's safety margin, your account enters a potential liquidation phase. During such an event, an authorized liquidator may clear part or all of your borrowed obligations to the protocol, seizing a corresponding portion of your collateral at a preferential rate.

### **Avoiding Liquidation**

Avoiding liquidation requires diligent maintenance of sufficient collateral and constant monitoring of the Borrow Capacity. Ensuring your loans remain within secure bounds is paramount.

{% hint style="info" %}
For more details on liquidation procedures, kindly refer to the [**Liquidations**](liquidations.md) section of our comprehensive documentation, or explore our smart contracts on [**GitHub**](../technical-overview/developer-links.md).
{% endhint %}

### **Understanding Price Volatility Implications**

The fluctuating market prices of the underlying assets define both your collateral's value and your borrowing potential. Any market-driven changes directly impact your Borrow Capacity and, by extension, your risk of liquidation.

In the rapidly changing landscape of decentralized finance, understanding these market dynamics is vital. As a responsible user of Rosa Finance, carefully managing your account and staying attuned to price fluctuations can significantly mitigate associated risks. The tools and metrics provided by Rosa Finance are designed to empower you to make informed and strategic decisions.

## Collateral Factors on Rosa Finance

<table><thead><tr><th width="252">roToken</th><th>Collateral Factor</th></tr></thead><tbody><tr><td>USDC</td><td>0.85</td></tr><tr><td>DAI</td><td>0.85</td></tr><tr><td>USDT</td><td>0.85</td></tr><tr><td>ETH</td><td>0.80</td></tr><tr><td>WBTC</td><td>0.80</td></tr><tr><td>FXS</td><td>0.60</td></tr><tr><td>GMX</td><td>0.70</td></tr><tr><td>LUSD</td><td>0.70</td></tr><tr><td>ARB</td><td>0.70</td></tr><tr><td>stETH</td><td>0.75</td></tr><tr><td>FRAX</td><td>0.75</td></tr><tr><td>PENDLE</td><td>0.70</td></tr></tbody></table>
