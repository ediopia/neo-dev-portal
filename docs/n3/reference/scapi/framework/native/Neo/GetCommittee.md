# NEO.GetCommittee Method ()

Gets the list of committee members.

Namespace: [Neo.SmartContract.Framework.Native](../index.md)

Assembly: Neo.SmartContract.Framework

## Syntax

```cs
public static extern string[] GetCommittee();
```

## Example

```cs
public class Contract1 : SmartContract.Framework.SmartContract
{
    public static object Test()
    {
        string[] result = NEO.GetCommittee();
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

Respond description:

- Array type: committee members are successfully requested.

- Others: failed.

[Back](index.md)
