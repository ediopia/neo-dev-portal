# Storage.CurrentContext Property

Returns the current storage context. After obtaining the storage context, the object can be passed as an argument to other contracts (as a way of authorization), allowing other contracts to perform read/write operations on the persistent store of the current contract.

Namespace: [Neo.SmartContract.Framework.Services](../index.md)

Assembly: Neo.SmartContract.Framework

## Syntax

```cs
public static extern StorageContext CurrentContext {get;}
```

Attribute value: Current storage context as a [StorageContext](../StorageContext.md).



[Back](index.md)
