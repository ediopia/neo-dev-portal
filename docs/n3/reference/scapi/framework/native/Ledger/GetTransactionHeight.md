# Ledger.GetTransactionHeight Method

Gets the block height where the transaction occurs by the transaction hash.

Namespace：[Neo.SmartContract.Framework.Native](../index.md)

Assembly: Neo.SmartContract.Framework

## Syntax

```cs
public static extern int GetTransactionHeight(UInt256 hash);
```

Parameter:

- hash: The hash of the queried transaction

## Example

```cs
public class Contract1 : SmartContract.Framework.SmartContract
{
    public static int Test(UInt256 txHash)
    {
        return Ledger.GetTransactionHeight(txHash);
    }
}
```

[Back](index.md)
