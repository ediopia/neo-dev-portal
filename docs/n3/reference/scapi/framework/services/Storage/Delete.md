# Storage.Delete Method

Deletes the value corresponding to the given key from the specific storage context.

Namespace: [Neo.SmartContract.Framework.Services](../index.md)

Assembly: Neo.SmartContract.Framework

## Syntax

```cs
public static extern void Delete(StorageContext context, byte[] key);
public static extern void Delete(StorageContext context, ByteString key);
```

Parameters:

- Context: Storage context as a [StorageContext](../StorageContext.md).

- Key: Key as a byte array or string. Max length 64 bytes.


Return value: void.

```cs
public static extern void Delete(byte[] key);
public static extern void Delete(string key);
```

Parameters:

Key: Key as a byte array or string.

Return value: void.

## Example

```cs
public class Contract1 : SmartContract.Framework.SmartContract
{
    public static void Main()
    {
        Storage.Delete(Storage.CurrentContext, "aa");
        Storage.Delete(Storage.CurrentContext, new byte[] { 0 });
        Storage.Delete("aa");
        Storage.Delete(new byte[] { 0 });
    }
}
```



[Back](index.md)
