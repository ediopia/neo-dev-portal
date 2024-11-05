# Policy.GetExecFeeFactor Method

Gets NeoVM execution fee. 

Namespace: [Neo.SmartContract.Framework.Native](../index.md)

Assembly: Neo.SmartContract.Framework

## Syntax

```cs
public static extern uint GetExecFeeFactor();
```

Return:

- vm execution fee

## Example

```cs
public static void Test()
{
    var factor = Policy.GetExecFeeFactor();
}
```

[Back](index.md)

