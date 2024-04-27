﻿## GatewaySettingManager


### MAX_BPS

```solidity
uint256 MAX_BPS
```

### protocolFeePercent

```solidity
uint64 protocolFeePercent
```

### treasuryAddress

```solidity
address treasuryAddress
```

### _aggregatorAddress

```solidity
address _aggregatorAddress
```

### _isTokenSupported

```solidity
mapping(address => uint256) _isTokenSupported
```

### supportedInstitutions

```solidity
mapping(bytes32 => struct SharedStructs.Institution[]) supportedInstitutions
```

### supportedInstitutionsByCode

```solidity
mapping(bytes32 => struct SharedStructs.InstitutionByCode) supportedInstitutionsByCode
```

### SettingManagerBool

```solidity
event SettingManagerBool(bytes32 what, address value, uint256 status)
```

### SupportedInstitutionsUpdated

```solidity
event SupportedInstitutionsUpdated(bytes32 currency, struct SharedStructs.Institution[] institutions)
```

### ProtocolFeeUpdated

```solidity
event ProtocolFeeUpdated(uint64 protocolFee)
```

### ProtocolAddressUpdated

```solidity
event ProtocolAddressUpdated(bytes32 what, address treasuryAddress)
```

### SetFeeRecipient

```solidity
event SetFeeRecipient(address treasuryAddress)
```

### settingManagerBool

```solidity
function settingManagerBool(bytes32 what, address value, uint256 status) external
```



Sets the boolean value for a specific setting.

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| what | bytes32 | The setting to be updated. |
| value | address | The address or value associated with the setting. |
| status | uint256 | The boolean value to be set. Requirements: - The value must not be a zero address. |


### setSupportedInstitutions

```solidity
function setSupportedInstitutions(bytes32 currency, struct SharedStructs.Institution[] institutions) external
```



Sets the supported institutions for a specific currency.

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| currency | bytes32 | The currency for which the institutions are being set. |
| institutions | struct SharedStructs.Institution[] | The array of institutions to be set. |


### updateProtocolFee

```solidity
function updateProtocolFee(uint64 _protocolFeePercent) external
```



Updates the protocol fee percentage.

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| _protocolFeePercent | uint64 | The new protocol fee percentage to be set. |


### updateProtocolAddress

```solidity
function updateProtocolAddress(bytes32 what, address value) external
```



Updates a protocol address.

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| what | bytes32 | The address type to be updated (treasury or aggregator). |
| value | address | The new address to be set. Requirements: - The value must not be a zero address. |


