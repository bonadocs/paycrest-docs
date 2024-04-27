﻿## IGateway

Interface for the Gateway contract.


### OrderCreated

```solidity
event OrderCreated(address sender, address token, uint256 amount, uint256 protocolFee, bytes32 orderId, uint256 rate, bytes32 institutionCode, string messageHash)
```

_Emitted when a deposit is made._

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| sender | address | The address of the sender. |
| token | address | The address of the deposited token. |
| amount | uint256 | The amount of the deposit. |
| protocolFee | uint256 |  |
| orderId | bytes32 | The ID of the order. |
| rate | uint256 | The rate at which the deposit is made. |
| institutionCode | bytes32 | The code of the institution. |
| messageHash | string | The hash of the message. |

### OrderSettled

```solidity
event OrderSettled(bytes32 splitOrderId, bytes32 orderId, address liquidityProvider, uint96 settlePercent)
```

_Emitted when an aggregator settles a transaction._

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| splitOrderId | bytes32 | The ID of the split order. |
| orderId | bytes32 | The ID of the order. |
| liquidityProvider | address | The address of the liquidity provider. |
| settlePercent | uint96 | The percentage at which the transaction is settled. |

### OrderRefunded

```solidity
event OrderRefunded(uint256 fee, bytes32 orderId)
```

_Emitted when an aggregator refunds a transaction._

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| fee | uint256 | The fee deducted from the refund amount. |
| orderId | bytes32 | The ID of the order. |

### SenderFeeTransferred

```solidity
event SenderFeeTransferred(address sender, uint256 amount)
```

_Emitted when the sender's fee is transferred._

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| sender | address | The address of the sender. |
| amount | uint256 | The amount of the fee transferred. |

### TransactionMetadata

```solidity
struct TransactionMetadata {
  bytes8 identifier;
  bytes8 institution;
  bytes8 name;
  bytes8 currency;
  uint256 liquidityProviderID;
}
```
### Order

```solidity
struct Order {
  address sender;
  address token;
  address senderFeeRecipient;
  uint256 senderFee;
  uint256 protocolFee;
  bool isFulfilled;
  bool isRefunded;
  address refundAddress;
  uint96 currentBPS;
  uint256 amount;
}
```
### createOrder

```solidity
function createOrder(address _token, uint256 _amount, bytes32 _institutionCode, uint96 _rate, address _senderFeeRecipient, uint256 _senderFee, address _refundAddress, string messageHash) external returns (bytes32 _orderId)
```

Locks the sender's amount of token into Gateway.

Requirements:
- `msg.sender` must approve Gateway contract on `_token` of at least `amount` before function call.
- `_token` must be an acceptable token. See {isTokenSupported}.
- `amount` must be greater than minimum.
- `_refundAddress` refund address must not be zero address.

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| _token | address | The address of the token. |
| _amount | uint256 | The amount in the decimal of `_token` to be locked. |
| _institutionCode | bytes32 | The institution code of the sender. |
| _rate | uint96 | The rate at which the sender intends to sell `_amount` of `_token`. |
| _senderFeeRecipient | address | The address that will receive `_senderFee` in `_token`. |
| _senderFee | uint256 | The amount in the decimal of `_token` that will be paid to `_senderFeeRecipient`. |
| _refundAddress | address | The address that will receive `_amount` in `_token` when there is a need to refund. |
| messageHash | string | The hash of the message. |

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| _orderId | bytes32 | The ID of the order. |

### settle

```solidity
function settle(bytes32 _splitOrderId, bytes32 _orderId, address _liquidityProvider, uint64 _settlePercent) external returns (bool)
```

Settles a transaction and distributes rewards accordingly.



#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| _splitOrderId | bytes32 | The ID of the split order. |
| _orderId | bytes32 | The ID of the transaction. |
| _liquidityProvider | address | The address of the liquidity provider. |
| _settlePercent | uint64 | The rate at which the transaction is settled. |

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| [0] | bool | bool the settlement is successful. |

### refund

```solidity
function refund(uint256 _fee, bytes32 _orderId) external returns (bool)
```

Refunds to the specified refundable address.

Requirements:
- Only aggregators can call this function.

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| _fee | uint256 | The amount to be deducted from the amount to be refunded. |
| _orderId | bytes32 | The ID of the transaction. |

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| [0] | bool | bool the refund is successful. |

### isTokenSupported

```solidity
function isTokenSupported(address _token) external view returns (bool)
```

Checks if a token is supported by Gateway.



#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| _token | address | The address of the token to check. |

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| [0] | bool | bool the token is supported. |

### getOrderInfo

```solidity
function getOrderInfo(bytes32 _orderId) external view returns (struct IGateway.Order)
```

Gets the details of an order.



#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| _orderId | bytes32 | The ID of the order. |

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| [0] | struct IGateway.Order | Order The order details. |

### getFeeDetails

```solidity
function getFeeDetails() external view returns (uint64 protocolReward, uint256 max_bps)
```

Gets the fee details of Gateway.




#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| protocolReward | uint64 | The protocol reward amount. |
| max_bps | uint256 | The maximum basis points. |

### getSupportedInstitutionByCode

```solidity
function getSupportedInstitutionByCode(bytes32 _code) external view returns (struct SharedStructs.InstitutionByCode)
```

Gets the details of a supported institution by code.



#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| _code | bytes32 | The institution code. |

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| [0] | struct SharedStructs.InstitutionByCode | InstitutionByCode The institution details. |

### getSupportedInstitutions

```solidity
function getSupportedInstitutions(bytes32 _currency) external view returns (struct SharedStructs.Institution[])
```

Gets the details of supported institutions by currency.



#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| _currency | bytes32 | The currency code. |

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| [0] | struct SharedStructs.Institution[] | Institutions An array of institutions. |

