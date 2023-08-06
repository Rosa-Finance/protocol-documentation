---
description: >-
  The Comptroller contract is a smart contract that serves as the central
  controller for the Rosa Finance lending protocol. It manages the overall
  functionality of the protocol, including market listing
---

# Comptroller

### Contract Structure

The Comptroller contract is implemented in Solidity and consists of several imported contracts, including `CToken.sol` (referred to as roToken), `ErrorReporter.sol`, `PriceOracle.sol`, `ComptrollerInterface.sol`, `ComptrollerStorage.sol`, `Unitroller.sol`, and `Rosa.sol`. These imported contracts provide the necessary functionality for the Comptroller to operate.

The Comptroller contract itself is defined as a contract named "Comptroller" and is inherited from various other contracts, such as `ComptrollerV7Storage`, `ComptrollerInterface`, `ComptrollerErrorReporter`, and `ExponentialNoError`.

The contract defines several events that are emitted during various actions, such as market listing, entering and exiting markets, changing parameters, and distributing rewards. These events provide transparency and allow for better tracking of protocol activities.

### Account Management

The Comptroller contract provides functions for account management, including tracking the assets that an account has entered, checking membership in a market, adding assets to an account's liquidity calculation, and removing assets from an account's liquidity calculation.

The `getAssetsIn` function returns a dynamic list of assets that an account has entered. The `checkMembership` function checks whether an account is a member of a given asset market.

The `enterMarkets` function allows an account to add multiple markets to its list of entered assets. It returns a list indicating whether each market was successfully entered.

The `addToMarketInternal` function is an internal function that adds a market to an account's "assets in" list. It performs various checks and updates the necessary data structures.

The `exitMarket` function allows an account to remove an asset from its list of entered assets. It checks whether the account has any outstanding borrow balance or is providing collateral for a borrow before allowing the exit.

### Policy Hooks

The Comptroller contract implements various policy hooks that determine whether certain actions should be allowed. These hooks include `mintAllowed`, `redeemAllowed`, `borrowAllowed`, `repayBorrowAllowed`, `liquidateBorrowAllowed`, `transferAllowed`, `seizeAllowed`, and `redeemAllowedInternal`.

These hooks check various conditions, such as whether the market is listed, whether the account has sufficient liquidity, and whether the requested action exceeds certain limits. They also update the necessary data structures and distribute rewards.

### Liquidity/Liquidation Calculations

The Comptroller contract provides functions for calculating account liquidity and determining the number of collateral tokens to seize in a liquidation.

The `getAccountLiquidity` function calculates the current account liquidity with respect to collateral requirements. It returns the account liquidity in excess of collateral requirements and the account shortfall below collateral requirements.

The `getHypotheticalAccountLiquidity` function determines the hypothetical account liquidity if certain amounts were redeemed or borrowed. It takes into account the balances, exchange rates, and prices of the assets involved.

The `liquidateCalculateSeizeTokens` function calculates the number of collateral tokens to seize in a liquidation based on the borrowed and collateral assets' prices, the liquidation incentive, and the exchange rate.

### Admin Functions

#### `_setPriceOracle`

* Sets a new price oracle for the Comptroller.
* Only the admin can call this function.
* Returns 0 on success, otherwise a failure.

#### `_setCloseFactor`

* Sets the close factor used when liquidating borrows.
* Only the admin can call this function.
* Returns 0 on success, otherwise a failure.

#### `_setCollateralFactor`

* Sets the collateral factor for a market.
* Only the admin can call this function.
* Returns 0 on success, otherwise a failure.

#### `_setLiquidationIncentive`

* Sets the liquidation incentive.
* Only the admin can call this function.
* Returns 0 on success, otherwise a failure.

#### `_supportMarket`

* Adds a market to the markets mapping and sets it as listed.
* Only the admin can call this function.
* Returns 0 on success, otherwise a failure.

#### `_addMarketInternal`

* Internal function to add a market to the allMarkets array.

#### `_initializeMarket`

* Internal function to initialize the state of a market.
* Sets the initial supply and borrow indices for the market.

#### `_setMarketBorrowCaps`

* Sets the borrow caps for the given roToken markets.
* Only the admin or borrowCapGuardian can call this function.

#### `_setBorrowCapGuardian`

* Changes the Borrow Cap Guardian.
* Only the admin can call this function.

#### `_setPauseGuardian`

* Changes the Pause Guardian.
* Only the admin can call this function.
* Returns 0 on success, otherwise a failure.

#### `_setMintPaused`

* Pauses or unpauses minting for a specific market.
* Only the pause guardian or admin can call this function.

#### `_setBorrowPaused`

* Pauses or unpauses borrowing for a specific market.
* Only the pause guardian or admin can call this function.

#### `_setTransferPaused`

* Pauses or unpauses transfers for the entire protocol.
* Only the pause guardian or admin can call this function.

#### `_setSeizePaused`

* Pauses or unpauses asset seizures for the entire protocol.
* Only the pause guardian or admin can call this function.

#### `_become`

* Allows this contract to become the new implementation of the Unitroller.
* Only the admin of the current Unitroller can call this function.

#### `fixBadAccruals`

* A one-off function to fix incorrect ROSA accruals for affected users.
* Only the admin can call this function.
* Once executed, it cannot be called again.

### ROSA Distribution

#### `updateCompSupplyIndex`

* Accrues ROSA to the market by updating the supply index.
* Internal function called when the supply speed of a market is updated.

#### `updateCompBorrowIndex`

* Accrues ROSA to the market by updating the borrow index.
* Internal function called when the borrow speed of a market is updated.

#### `distributeSupplierComp`

* Calculates ROSA accrued by a supplier and transfers it to them.
* Internal function called when ROSA is claimed by a supplier.

#### `distributeBorrowerComp`

* Calculates ROSA accrued by a borrower and transfers it to them.
* Internal function called when ROSA is claimed by a borrower.

#### `updateContributorRewards`

* Calculates additional accrued ROSA for a contributor since the last accrual.
* Called when a contributor interacts with the protocol.

#### `claimComp`

* Claims all the ROSA accrued by a user in all or specified markets.
* Can claim both borrowing and supplying rewards.
* Can claim for multiple users at once.

#### `grantCompInternal`

* Transfers ROSA to the user.
* Internal function called when ROSA is claimed by a user.

### ROSA Distribution Admin

#### `_grantComp`

* Transfers ROSA to the recipient.
* Only the admin can call this function.

#### `_setCompSpeeds`

* Sets the ROSA speeds for the specified markets.
* Only the admin can call this function.

#### `_setContributorCompSpeed`

* Sets the ROSA speed for a single contributor.
* Only the admin can call this function.

### Other Functions

#### `getAllMarkets`

* Returns all the markets in the protocol.

#### `isDeprecated`

* Returns true if the given roToken market has been deprecated.

#### `getBlockNumber`

* Returns the current block number.

#### `getCompAddress`

* Returns the address of the ROSA token.

### Conclusion

The Comptroller contract serves as the central controller for the Rosa Finance lending protocol. It manages market listing, account management, interest rate calculations, and reward distribution. It provides functions for entering and exiting markets, checking account liquidity, and performing liquidations. The contract is designed to ensure the security, efficiency, and transparency of the lending protocol.
