---
description: >-
  This document provides a technical overview of the staking contracts and their
  operations within the protocol.
---

# Staking

## **Distributor.sol**

### **Overview**

The **`Distributor`** contract is responsible for distributing rewards to recipients. It is designed to be highly flexible, supporting multiple reward tokens, and follows an ownable pattern.

### **Key Structs and Variables**

* **`Recipient`**: Contains information related to the individual recipient, including the last share index and credit.
* **`recipients`**: Maps token and account addresses to the recipient's data.
* **`shares`**: Stores the number of shares each account holds.
* **`shareIndex`**: Stores the share index for each token.
* **`totalShares`**: Stores the total number of shares across all accounts.

### **Functions**

#### **addReward**

Allows the addition of rewards to a specific token.

```solidity
function addReward(address token, uint256 amount) public returns (uint256 _shareIndex)
```

#### **updateCredit**

Updates the credit for a specific recipient on a specific token.

```solidity
function updateCredit(address token, address account) public returns (uint256 credit)
```

#### **claim**

Allows a recipient to claim their rewards for a specific token.

```solidity
function claim(address token) external returns (uint256 amount)
```

#### **claimAll**

Allows a recipient to claim all of their rewards.

```solidity
function claimAll() external returns (uint256[] memory amounts)
```

#### **getClaimable**

Retrieves the amount a recipient can claim from a specific token.

```solidity
function getClaimable(address token, address account) external view returns (uint256 amount)
```

#### **addToken**

Adds a new reward token.

```solidity
function addToken(address token) external onlyOwner
```

#### **removeToken**

Removes a reward token.

```solidity
function removeToken(address token) external onlyOwner
```

### **Events**

Events such as **`AddReward`**, **`UpdateCredit`**, **`EditRecipient`**, and **`Claim`** are emitted to keep track of important state changes.

### **Owner Controls**

The owner can add or remove reward tokens through **`addToken(address token)`** and **`removeToken(address token)`** functions.

## **StakedDistributor.sol**

### **Overview**

**`StakedDistributor`** extends the **`Distributor`** contract and enables token holders to stake their tokens in return for rewards. It introduces withdrawal functionality with a time-based lock mechanism.

### **Key Structs and Variables**

* **`Withdrawal`**: Contains information related to a user's withdrawal, including the amount and release time.
* **`withdrawal`**: Associates an address with its pending withdrawals.
* **`withdrawalPendingTime`**: The time (in seconds) a user must wait before they can withdraw their staked tokens.

### **Functions**

#### **mint**

Allows a user to stake their tokens in the contract.

```solidity
function mint(uint256 amount) public
```

#### **burn**

Allows a user to unstake their tokens from the contract.

```solidity
function burn(uint256 amount) public
```

#### **withdraw**

Allows a user to withdraw their unstaked tokens from the contract.

```solidity
function withdraw() public
```

#### **\_afterTokenTransfer**

Updates the balance of the token holders after a token transfer occurs.

```solidity
function _afterTokenTransfer(address from, address to, uint256 /* amount */) internal override
```

#### **setWithdrawalPendingTime**

Allows the owner of the contract to change the pending withdrawal time.

```solidity
function setWithdrawalPendingTime(uint256 withdrawalPendingTime_) public onlyOwner
```

### **Events**

* **`Withdraw`**: Emitted when a user makes a withdrawal.

## **Conclusion**

Rosa Finance's staking contracts are designed to enable an efficient and secure staking and rewards distribution mechanism. The modular and extensible design allows for potential enhancements and supports the integration of various functionalities.
