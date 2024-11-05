# NEO.TotalSupply Method

Gets the total supply of NEO.

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
        BigInteger result = NEO.TotalSupply();
        return result;
    }
}
```

Response body:

```json
{
    "Type":"Integer",
    "value":"100000000"
}
```

Response description:

- Integer type: token total supply is successfully requested.

- Others: failed.

[Back](index.md)
