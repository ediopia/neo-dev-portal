# Runtime.Log Method

Sends a log message to the client executing the smart contract. This method can trigger an event on the client but requires the client to be compatible.

Namespace: [Neo.SmartContract.Framework.Services](../index.md)

Assembly: Neo.SmartContract.Framework

## Syntax

```cs
public static extern void Log(string message)
```

Parameters: 

- message: Log as a string.


## Example

```cs
public class Contract1 : SmartContract.Framework.SmartContract
{
    public static void Main(bool debug)
    {
        if(debug)
        {
            Runtime.Log("Execution successful");
        }
    }
}
```



[Back](index.md)
