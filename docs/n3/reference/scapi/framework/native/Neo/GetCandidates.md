# NEO.GetCandidates Method ()

Gets the list of candidates.

Namespace: [Neo.SmartContract.Framework.Native](../index.md)

Assembly: Neo.SmartContract.Framework

## Syntax

```cs
public static extern (ECPoint, BigInteger)[] GetCandidates();
```

## Example

```cs
public class Contract1 : SmartContract.Framework.SmartContract
{
    public static object Test()
    {
        (ECPoint, BigInteger)[] result = NEO.GetCandidates();
        return result;
    }
}
```

Response description:

```json
[{
    "type": "Array",
    "value": [{
        "type": "Struct",
        "value": [{
            "type": "ByteString",
            "value": "Apls6R4n/uoL7MTn/cB3Llj8G\u002BuLJ7LUyL/JWBQg4I0y"
        }, {
            "type": "Integer",
            "value": "10000"
        }]
    }]
}]
```

Response description:

- Array type: candidates are successfully requested.

- Others: failed.

[Back](index.md)

