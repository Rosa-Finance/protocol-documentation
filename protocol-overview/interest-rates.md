---
description: >-
  Discover how our interest rate model optimally balances liquidity and
  incentivization, adapting to asset characteristics and market conditions for
  enhanced efficiency.
---

# Interest Rates

## **Overview**

Rosa Finance’s interest rate model elegantly addresses the dual requirements of liquidity and incentivization, adapting dynamically to market conditions. By employing a JumpRateModel, Rosa Finance strikes a balance between stability and incentive-driven enhancement to ensure optimal utilization of assets.

## **Core Elements**

The core mechanics of the interest rate model revolve around three key parameters:

* **Base Rate**: A foundational interest rate applied universally across all asset utilization levels.
* **Multipliers**: Two multipliers, regular and "jump," are used to modulate the interest rate in response to the liquidity pool's utilization rate.
* **Kink**: A utilization threshold at which the model switches from a standard multiplier to the jump multiplier, triggering a more rapid increase in interest rates.

These elements function together to provide a fluid interest rate mechanism that encourages both lending and borrowing within the system.

### **Utilization Rate Calculation**

The utilization rate is an essential metric that acts as a conduit to interpret the overall lending and borrowing landscape within the protocol. Defined as the ratio of total borrowed assets (excluding reserves) to the sum of available cash and borrowed assets, the utilization rate reveals the percentage of funds actively engaged in lending.

Mathematically, the utilization rate (UR) is calculated as:

```mathematica
UR = borrows / (cash + borrows - reserves)
```

The relationship between the utilization rate and the interest rate is multifaceted. A high utilization rate indicates increased borrowing, driving interest rates up, while a low utilization rate results in lowered interest rates to stimulate borrowing activity.

## **Interest Rate Models in Rosa Finance**

Rosa Finance's sophistication lies in its deployment of three distinct interest rate models, each calibrated to correspond to varying risk profiles and asset characteristics:

1.  **Stable Rate Model**: Targeted for low-volatility assets, particularly stablecoins, this model maintains a minimal base interest rate and conservative multipliers. The absence of a base rate and moderate multipliers ensures a steady, low-interest rate that resonates with the stability of the underlying assets.

    ```mathematica
    baseRatePerYear = 0; multiplierPerYear = 0.05; jumpMultiplierPerYear = 1.365; kink = 0.80
    ```
2.  **Medium Rate Model**: Suitable for assets with moderate volatility, this model introduces a base rate and provides for a more pronounced reaction to changes in utilization. The configuration is designed to offer an attractive yield for suppliers without overburdening borrowers.

    ```mathematica
    baseRatePerYear = 0.02; multiplierPerYear = 0.225; jumpMultiplierPerYear = 1.25; kink = 0.80
    ```
3.  **Volatile Rate Model**: Tailored for high-risk, volatile assets, this model compensates lenders with a higher base rate and a significantly sharper reaction to utilization beyond the kink. It reflects a strategic balance between incentivizing lenders while prudently controlling the borrowing landscape.

    ```mathematica
    baseRatePerYear = 0.025; multiplierPerYear = 0.225; jumpMultiplierPerYear = 5; kink = 0.80
    ```

These models are not mere static constructs but dynamic frameworks that integrate seamlessly with Rosa Finance's overall risk management and financial ecosystem. Their careful calibration allows the protocol to accommodate a diverse array of assets while promoting a healthy and liquid market.
