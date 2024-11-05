# Ledger Class

Provides a series attributes and methods of the native contract GasToken, which hash is`0xda65b600f7124ce6c79950c1772a36403104f2be`.

Namespace：[Neo.SmartContract.Framework.Native](index.md)

Assembly: Neo.SmartContract.Framework

## Syntax

```cs
public class Ledger
```

## Properties

| Name         | Description                                                  |
| ------------ | ------------------------------------------------------------ |
| Hash         | Gets the contract hash.                                      |
| CurrentHash  | Gets hash of the latest block                                |
| CurrentIndex | Gets latest block height in current blockchain<br/>Block height = Block index = Block count - 1<br/> |

## Methods

| Name                                                         | Description                                                  |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [GetBlock()](GetBlock.md)                             | Gets block by the block hash or index                        |
| [GetTransaction(UInt256 hash)](GetTransaction.md)     | Gets transaction by transaction ID                           |
| [GetTransactionFromBlock()](GetTransactionFromBlock.md) | Gets the specified transaction by the block and transaction indexes |
| [GetTransactionHeight(UInt256 hash)](GetTransactionHeight.md) | Gets the block height where the transaction occurs by the transaction hash |
