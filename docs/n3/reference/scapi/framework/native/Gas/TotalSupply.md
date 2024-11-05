# GAS.TotalSupply Method

Gets the total supply of GAS.

Namespace: [Neo.SmartContract.Framework.Native](../index.md)

Assembly: Neo.SmartContract.Framework

## Syntax

```cs
public static extern BigInteger TotalSupply();
```

## Example

```cs
public class Contract1 : SmartContract.Framework.SmartContract
{
    public static object Test()
    {
        BigInteger result = GAS.TotalSupply();
        return result;
    }
}
```

[Back](index.md)
