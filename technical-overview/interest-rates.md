---
description: >-
  This section goes into the technical details of the fundamental interest rate
  model used within the Rosa Finance lending protocol.
---

# Interest Rates

## Overview

The primary contracts responsible for this are **`InterestRateModel.sol`** and **`JumpRateModelV4.sol`**. These contracts work collectively to facilitate the calculations and adjustments of interest rates in response to the market's liquidity condition.

**`InterestRateModel.sol`** is an abstract contract that provides the interface for implementing any interest rate model within the protocol. It sets out the blueprint for the necessary functions related to interest rate calculations.

**`JumpRateModelV4.sol`** is a concrete implementation of this abstract contract and is derived from Compound's JumpRateModel. It introduces enhanced flexibility and precision in interest rate calculations based on the market's utilization rate. This contract implements a two-tiered interest rate model, in which the rate linearly increases with the utilization rate until a 'kink' after which it jumps, giving it the name 'JumpRateModel'.

In the following sections, we provide a detailed technical analysis of these contracts.

## **JumpRateModelV4.sol**

The **`JumpRateModelV4`** contract is part of the Rosa Finance lending protocol. It's responsible for calculating the interest rates within the protocol, taking into account both borrowing and lending rates. It's a modified version of Compound's JumpRateModel, introducing more functionality and flexibility.

Here's a detailed technical overview of the contract:

### **Inheritance and Libraries**

* **`InterestRateModel`**: Implements the interest rate model interface for defining standard functions required for interest rate calculations.
* **`Ownable`**: Allows for restricted access to certain functionalities.
* **`SafeMath`**: Safely performs mathematical operations.

### **Events**

* **`NewInterestParams`**: Emitted when the parameters of the interest rate model are updated.

### **State Variables**

* **`blocksPerYear`**: The approximate number of blocks per year, used for converting annual rates to per-block rates.
* **`multiplierPerBlock`**: The multiplier of the utilization rate that defines the slope of the interest rate curve before the kink.
* **`baseRatePerBlock`**: The base interest rate, acting as the y-intercept of the interest rate curve.
* **`jumpMultiplierPerBlock`**: The multiplier that applies after the utilization rate exceeds a certain threshold called the kink.
* **`kink`**: The utilization point where the jump multiplier is applied.
* **`name`**: A human-friendly name for the model, like a token symbol.

### **Constructor**

The constructor sets up the interest rate model parameters, including base rates, multipliers, and the kink. It also sets the contract's owner.

### **Public and External Functions**

* **`updateJumpRateModel`**: Allows the owner to update the interest rate model parameters.
* **`utilizationRate`**: Calculates the utilization rate as **`borrows / (cash + borrows - reserves)`**.
* **`updateBlocksPerYear`**: Updates the estimated number of Ethereum blocks per year.
* **`getBorrowRate`**: Calculates the current borrow interest rate per block, considering the utilization rate and applying the jump rate if necessary.
* **`getSupplyRate`**: Calculates the current supply interest rate per block, based on the borrow rate and reserve factor.
* **`updateJumpRateModelInternal`**: Internal function to actually update the interest rate model parameters.

## **InterestRateModel.sol**

This is an abstract contract that defines the interface for the interest rate models used within the Rosa Finance lending protocol. It provides a blueprint for how interest rate models must be constructed, ensuring consistency and interoperability within the protocol.

### **Constant**

* **`isInterestRateModel`**: A boolean constant used to identify contracts implementing this interface.

### **Abstract Functions**

* **`getBorrowRate`**: An abstract function that must be implemented to calculate the borrow interest rate per block, given the total cash, borrows, and reserves in the market.
* **`getSupplyRate`**: An abstract function that must be implemented to calculate the supply interest rate per block, based on the total cash, borrows, and reserves, and the current reserve factor.

## **Conclusion**

These two contracts collectively form the interest rate logic within the Rosa Finance lending protocol. The abstract **`InterestRateModel`** contract ensures a standardized approach to calculating interest rates, while **`JumpRateModelV4`** is a specific implementation that provides a more granular control over interest rate dynamics, allowing for variable rates based on market utilization and including features for updatable parameters.
