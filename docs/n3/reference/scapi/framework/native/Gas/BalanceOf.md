# GAS.BalanceOf Method

Gets the GAS balance in the account.

Namespace: [Neo.SmartContract.Framework.Native](../index.md)

Assembly: Neo.SmartContract.Framework

## Syntax

```cs
public static extern BigInteger BalanceOf(byte[] account);
```

Parameters:

- account: Script hash of the account

## Example

```cs
public class Contract1 : SmartContract.Framework.SmartContract
{
    private static readonly UInt160 account = "NXsG3zwpwcfvBiA3bNMx6mWZGEro9ZqTqM".ToScriptHash();

    public static object Test()
    {
        BigInteger result = GAS.BalanceOf(account);
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

Response description

- Integer type: The account balance obtained successfully.

- Other: failed.

[Back](index.md)
