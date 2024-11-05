# Ledger.GetTransactionFromBlock Method

Gets the specified transaction by the block index (or block hash) and transaction index.

Namespace：[Neo.SmartContract.Framework.Native](../index.md)

Assembly: Neo.SmartContract.Framework

## Syntax

```cs
public static extern Transaction GetTransactionFromBlock(UInt256 blockHash, int txIndex);
public static extern Transaction GetTransactionFromBlock(uint blockHeight, int txIndex);
```

Parameters:

- blockHash: the hash of the specified block

- blockHeight: the index of the specified block (block height)
- txIndex: transaction index. The transaction index starts from 0 and increases sequentially.

## Example

```cs
public class Contract1 : SmartContract.Framework.SmartContract
{
    public static void GetFirstTransaction(uint block)
    {
        var tx = Ledger.GetTransactionFromBlock(block, 0);
    }
    public static void GetFirstTransaction(UInt256 block)
    {
        var tx = Ledger.GetTransactionFromBlock(block, 0);
    }
}
```

[Back](index.md)
