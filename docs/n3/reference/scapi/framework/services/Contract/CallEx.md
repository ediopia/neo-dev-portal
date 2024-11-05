# Contract.CallEx Method (UInt160, string, object[], CallFlags)

Invokes the contract.

Namespace: [Neo.SmartContract.Framework.Services](../index.md)

Assembly:  Neo.SmartContract.Framework

## Syntax

```cs
public static extern object CallEx(UInt160 scriptHash, string method, object[] arguments, CallFlags flag)
```

Parameters:

- scriptHash: The contract script hash
- method: The contract method
- arguments: The contract method arguments
- flag: The contract call flag

## Example

```cs
public class Contract1 : SmartContract
 {
     delegate object Dyncall(string method, object[] args);

     //0x230cf5ef1e1bd411c7733fa92bb6f9c39714f8f9 in little endian order
     //HexToBytes()、ToScriptHash() can only operate on constants and cannot be written in the Main method
     //scriptHash can be modified to be passed in from the parameter or read from storage
     static byte[] ScriptHash = "f9f81497c3f9b62ba93f73c711d41b1eeff50c23".HexToBytes();

     public static object Main(string operation, object[] args)
     {
         if (operation == "name")
         {
             return Contract.Call((UInt160)ScriptHash, "name", new object[0], CallFlags.ReadOnly);
         }
         if (operation == "totalSupply")
         {
             return Contract.Call((UInt160)ScriptHash, "totalSupply", new object[0], CallFlags.ReadOnly);
         }
         return true;
     }
 }
```



[Back](index.md)
