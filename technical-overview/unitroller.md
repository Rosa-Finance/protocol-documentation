# Unitroller

## Overview

The **`Unitroller.sol`** contract acts as the administrative and upgradeable hub for the Comptroller within the Rosa Finance protocol. This design follows the proxy pattern, enabling various parts of the system to reference a stable address while the logic and functionality behind it may change.

Below are the main components and functions of the **`Unitroller.sol`** contract:

### **Storage**

The contract inherits from the **`UnitrollerAdminStorage`** and contains administrative-related variables:

* **`admin`**: The current administrator of the contract, who has permissions to change the pending administrator and the pending implementation of the comptroller.
* **`pendingAdmin`**: The address that has been proposed to become the new administrator. This address must call **`_acceptAdmin`** to finalize the transfer of admin rights.
* **`comptrollerImplementation`**: The address where the current implementation of the comptroller logic resides.
* **`pendingComptrollerImplementation`**: The address of the new comptroller logic that has been proposed for upgrade. This address must call **`_acceptImplementation`** to finalize the upgrade.

### **Constructor**

The constructor sets the **`admin`** as the deployer of the contract.

### **Admin Functions**

#### **\_setPendingImplementation**

The function **`_setPendingImplementation(address newPendingImplementation)`** allows the current admin to propose a new comptroller implementation address. The proposed address will need to accept the implementation via the **`_acceptImplementation`** function.

#### **\_acceptImplementation**

The function **`_acceptImplementation()`** is designed for the pending comptroller implementation to accept its role as the new implementation, after being proposed by the current admin.

#### **\_setPendingAdmin**

The function **`_setPendingAdmin(address newPendingAdmin)`** allows the current admin to propose a new administrator. The new pending admin must finalize the transfer by calling the **`_acceptAdmin`** function.

#### **\_acceptAdmin**

The function **`_acceptAdmin()`** is used by the pending admin to accept the role of admin, after being proposed by the current admin.

### **Ether Handling**

* **`receive()`**: This function allows the contract to receive Ether, defining behavior if the contract is sent Ether directly.
* **`fallback() payable`**: This function allows the contract to delegate calls to the current **`comptrollerImplementation`**. Any calls to functions that aren't explicitly defined in the Unitroller will be forwarded to the comptrollerImplementation, and any returns or reverts will be propagated back to the caller.

### **Events**

* **`NewPendingImplementation`**: Emitted when the pending implementation is changed.
* **`NewImplementation`**: Emitted when the pending implementation is accepted.
* **`NewPendingAdmin`**: Emitted when the pending admin is changed.
* **`NewAdmin`**: Emitted when the pending admin is accepted.

## **Conclusion**

**`Unitroller.sol`** in the Rosa Finance protocol serves as the central administrative contract that allows for secure and upgradeable management of the system's core logic. By encapsulating these controls within a dedicated contract, it offers an organized and robust framework for both maintenance and future development.
