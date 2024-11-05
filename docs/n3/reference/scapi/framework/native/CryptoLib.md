# CryptoLib Class

Provides a series methods of the native contract `CryptoLib`. The contract hash is `0x726cb6e0cd8628a1350a611384688911ab75f51b`。

Namespace：[Neo.SmartContract.Framework.Native](index.md)

Assembly: Neo.SmartContract.Framework

## Syntax

```cs
public static class CryptoLib
```

## Properties

| Name | Description            |
| ---- | ---------------------- |
| Hash | Gets the contract hash |

## Methods

| Name                                   | Description   |
| ---------------------------------------- | --------------- |
| Sha256(ByteString value) | Calculates the byte array with SHA256 hash |
| ripemd160(ByteString value) | Calculates the byte array with RIPEMD160 |
| VerifyWithECDsa(ByteString message, Cryptography.ECC.ECPoint pubkey, ByteString signature, NamedCurve curve) | Uses elliptic curve to verify the signature |
