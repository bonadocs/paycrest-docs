﻿## Gateway

This contract serves as a gateway for creating orders and managing settlements.


### fee

```solidity
struct fee {
  uint256 protocolFee;
  uint256 liquidityProviderAmount;
}
```
### constructor

```solidity
constructor() public
```







### initialize

<BonadocsWidget widgetConfigUri="ipfs://bafkreigu3fc74fxtt5slxaow52iuoe3iqnrkjoxnrx2fgoprwhu7c74p2m" contract="Gateway" functionKey="0x8129fc1c" />



Initialize function.



### onlyAggregator

```solidity
modifier onlyAggregator()
```

_Modifier that allows only the aggregator to call a function._

### pause

<BonadocsWidget widgetConfigUri="ipfs://bafkreigu3fc74fxtt5slxaow52iuoe3iqnrkjoxnrx2fgoprwhu7c74p2m" contract="Gateway" functionKey="0x8456cb59" />



Pause the contract.



### unpause

<BonadocsWidget widgetConfigUri="ipfs://bafkreigu3fc74fxtt5slxaow52iuoe3iqnrkjoxnrx2fgoprwhu7c74p2m" contract="Gateway" functionKey="0x3f4ba83a" />



Unpause the contract.



### createOrder

<BonadocsWidget widgetConfigUri="ipfs://bafkreigu3fc74fxtt5slxaow52iuoe3iqnrkjoxnrx2fgoprwhu7c74p2m" contract="Gateway" functionKey="0xd12ff20a" />



See `{createOrder-IGateway}`.



### _handler

```solidity
function _handler(address _token, uint256 _amount, address _refundAddress, address _senderFeeRecipient, uint256 _senderFee, bytes32 _institutionCode) internal view
```



Internal function to handle order creation.

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| _token | address | The address of the token being traded. |
| _amount | uint256 | The amount of tokens being traded. |
| _refundAddress | address | The address to refund the tokens in case of cancellation. |
| _senderFeeRecipient | address | The address of the recipient for the sender fee. |
| _senderFee | uint256 | The amount of the sender fee. |
| _institutionCode | bytes32 | The code of the institution associated with the order. |


### settle

<BonadocsWidget widgetConfigUri="ipfs://bafkreigu3fc74fxtt5slxaow52iuoe3iqnrkjoxnrx2fgoprwhu7c74p2m" contract="Gateway" functionKey="0xf22ee704" />



See `{settle-IGateway}`.



### refund

<BonadocsWidget widgetConfigUri="ipfs://bafkreigu3fc74fxtt5slxaow52iuoe3iqnrkjoxnrx2fgoprwhu7c74p2m" contract="Gateway" functionKey="0x71eedb88" />



See `{refund-IGateway}`.



### getOrderInfo

<BonadocsWidget widgetConfigUri="ipfs://bafkreigu3fc74fxtt5slxaow52iuoe3iqnrkjoxnrx2fgoprwhu7c74p2m" contract="Gateway" functionKey="0x768c6ec0" />



See `{getOrderInfo-IGateway}`.



### isTokenSupported

<BonadocsWidget widgetConfigUri="ipfs://bafkreigu3fc74fxtt5slxaow52iuoe3iqnrkjoxnrx2fgoprwhu7c74p2m" contract="Gateway" functionKey="0x75151b63" />



See `{isTokenSupported-IGateway}`.



### getSupportedInstitutionByCode

<BonadocsWidget widgetConfigUri="ipfs://bafkreigu3fc74fxtt5slxaow52iuoe3iqnrkjoxnrx2fgoprwhu7c74p2m" contract="Gateway" functionKey="0xc2280103" />



See `{getSupportedInstitutionByCode-IGateway}`.



### getSupportedInstitutions

<BonadocsWidget widgetConfigUri="ipfs://bafkreigu3fc74fxtt5slxaow52iuoe3iqnrkjoxnrx2fgoprwhu7c74p2m" contract="Gateway" functionKey="0x02621338" />



See `{getSupportedInstitutions-IGateway}`.



### getFeeDetails

<BonadocsWidget widgetConfigUri="ipfs://bafkreigu3fc74fxtt5slxaow52iuoe3iqnrkjoxnrx2fgoprwhu7c74p2m" contract="Gateway" functionKey="0xb810c636" />



See `{getFeeDetails-IGateway}`.



