# NEO.GetNextBlockValidators Method ()

Gets the list of validators for the next block

Namespace: [Neo.SmartContract.Framework.Native](../index.md)

Assembly: Neo.SmartContract.Framework

## Syntax

```cs
public static extern string[] GetNextBlockValidators();
```

## Example

```cs
public class Contract1 : SmartContract.Framework.SmartContract
{
    public static object Test()
    {
        string[] result = NEO.GetNextBlockValidators();
        return result;
    }
}
```

Response body:

```json
[{
    "type": "Array",
    "value": [{
        "type": "ByteString",
        "value": "Auj/F8Vn1i8nT\u002BJHzIhKKmzTuP0Nd5qMWFYomlYKzKy0"
    }]
}]
```

Response description:

- Array type: validators by persisting block are successfully requested.

- Others: failed.

[Back](index.md)
