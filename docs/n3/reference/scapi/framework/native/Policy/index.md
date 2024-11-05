# Policy Class

Provides a series of methods of the native contract Policy, which contract hash is `0xcc5e4edd9f5f8dba8bb65734541df7a1c081c67b`.

Namespace：[Neo.SmartContract.Framework.Native](index.md)

Assembly: Neo.SmartContract.Framework

## Syntax

```cs
public class Policy
```

## Attribute

| Name | Description       |
| ---- | ----------------- |
| Hash | The contract hash |

## Methods

| Name                                              | Description                                                  |
| ------------------------------------------------- | ------------------------------------------------------------ |
| [GetFeePerByte()](GetFeePerByte.md)        | Gets the network fee per transaction byte                    |
| [GetExecFeeFactor()](GetExecFeeFactor.md)  | Gets the execution fee factor. This is a multiplier that can be adjusted by the committee to adjust the system fees for transactions |
| [GetStoragePrice()](GetStoragePrice.md)    | Gets the storage price                                       |
| [IsBlocked(UInt160 account)](IsBlocked.md) | Determines whether the specified account is blocked          |
