# NftAllowance

An approved allowance of NFT transfers for a spender.

| Field            | Type                                               | Description                                                                                                                                                                                     |
| ---------------- | -------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `TokenId`        | TokenID                                            | The token that the allowance pertains to                                                                                                                                                        |
| `owner`          | AccountID                                          | The account ID of the hbar owner (ie. the grantor of the allowance)                                                                                                                             |
| `spender`        | AccountID                                          | The account ID of the spender of the hbar allowance                                                                                                                                             |
| `serialNumbers`  | repeated int64                                     | The list of serial numbers that the spender is permitted to transfer                                                                                                                            |
| `approvedForAll` | google.protobuf.BoolValuegoogle.protobuf.BoolValue | If true, the spender has access to all of the account owner's NFT instances (currently **** owned and any in the future). If this field is set to true the serialNumbers field should be empty. |

####
