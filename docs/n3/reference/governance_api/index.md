---
sidebar_label: 'Governance API'
sidebar_position: 0
---

# Governance API

## Candidates

There is no duty assigned to candidates. However, committee members and consensus nodes are elected from certain number of candidates with most votes. 

### How to Become a Candidate

An address can be registered as candidate or unregistered afterwards. Corresponding contract methods are as follows:

| Method | Parameters | Fee in GAS |
| ---- | ------------------------------------ | ---- |
| [`RegisterCandidate`](../scapi/framework/native/Neo/RegisterCandidate.md) | ECPoint publicKey | Adjustable, initially 0.00001 |
| [`UnregisterCandidate`](../scapi/framework/native/Neo/UnregisterCandidate.md) | ECPoint publicKey | 0.00065536 (CpuFee) |

:::note
Registering / unregistering candidate requires signature. It means candidate registering / unregistering is only self-determined. 
:::

### Candidate Voting 

Every address has the right to vote to only one address (whether or not it's a candidate). Candidate's received votes are defined as the sum of NEO held by its voter. Every standby committee member will vote to itself in genesis block. 

Voting contract method is as follows. Please not that voter's signature will be checked. 

| Method | Parameters | Fee in GAS |
| ---- | ------------------------------------ | ---- |
| [`Vote`](../scapi/framework/native/Neo/Vote.md) | UInt160 account, byte[] voteTo | 0.00065536 (CpuFee) |

As voters' votes & held NEO, as well as registered candidates keep changing, candidate set and their votes are re-calculated in every block.

| Method | Parameters | Fee in GAS |
| ---- | ------------------------------------ | ---- |
| [`GetCandidates`](../scapi/framework/native/Neo/GetCandidates.md) | null | 0 |

## Committee

### Function & Scope

Committee members have the privilege to modify the configuration of Neo network by voting, including:

* Role designation
* Set fee per byte for network transmission
* Set execution fee (CpuFee) factor
* Set storage price
* Block / unblock account
* Set Oracle service price
* Set gas released per block
* Set fee to register a candidate
* Add NNS root
* Set the NNS registration/renewal fee
* Update the NNS contract
* Set minimum fee for contract deployment

Method definition and corresponding fee are defined in PolicyContract as shown below:

| Method | Parameters | Fee in GAS | Contract |
| ---- | ------------------------------------ | ---- | ---- |
| DesignateAsRole | Role role, ECPoint[] nodes | 0.00032768 (CpuFee) | RoleManagement |
| SetFeePerByte | long value | 0.00032768 (CpuFee) | PolicyContract |
| SetExecFeeFactor | uint value | 0.00032768 (CpuFee) | PolicyContract |
| SetStoragePrice | uint value | 0.00032768 (CpuFee) | PolicyContract |
| SetPrice | long price | 0.00032768 (CpuFee) | OracleContract |
| SetGasPerBlock | BigInteger gasPerBlock | 0.00032768 (CpuFee) | NeoToken |
| SetRegisterPrice | long registerPrice | 0.00032768 (CpuFee) | NeoToken |
| AddRoot | string root | 0.00032768 (CpuFee) | NameService |
| SetPrice | long price | 0.00032768 (CpuFee) | NameService |
| Update | ByteString nef, string manifest | StoragePrice * (nefFile.Length + manifest.Length) | NameService |
| SetMinimumDeploymentFee | BigInteger value | 0.00032768 (CpuFee) | ContractManagement |

To bring such modification into effect, committee members should send a transaction which calls corresponding method & includes enough signatures on chain. This transaction is executed as long as it's signed by more than half of the committee members.

Furthermore, corresponding reading methods are also supported:

| Method | Parameters | Fee in GAS | Contract |
| ---- | ------------------------------------ | ---- | ---- |
| [`GetDesignatedByRole`](../scapi/framework/native/RoleManagement/GetDesignatedByRole.md) | Role role, uint index | 0.00032768 (CpuFee) | RoleManagement |
| [`GetFeePerByte`](../scapi/framework/native/Policy/GetFeePerByte.md) | null | 0.00032768 (CpuFee) | PolicyContract |
| [GetExecFeeFactor](../scapi/framework/native/Policy/GetExecFeeFactor.md) | null | 0.00032768 (CpuFee) | PolicyContract |
| [GetStoragePrice](../scapi/framework/native/Policy/GetStoragePrice.md) | null | 0.00032768 (CpuFee) | PolicyContract |
| [`IsBlocked`](../scapi/framework/native/Policy/IsBlocked.md) | UInt160 account | 0.00032768 (CpuFee) | PolicyContract |
| GetPrice | null | 0.00032768 (CpuFee) | OracleContract |
| [`GetGasPerBlock`](../scapi/framework/native/Neo/GetGasPerBlock.md) | null | 0.00032768 (CpuFee) | NeoToken |
| GetRegisterPrice | null | 0.00032768 (CpuFee) | NeoToken |
| GetMinimumDeploymentFee | null | 0.00032768 (CpuFee) | ContractManagement |

### How are committee members elected

1. Sort the registered candidates by votes
2. Take certain numbers of candidates (21 by default) with the most votes as committee members.
Committee members are refreshed every 21 blocks.

### Corresponding contract method

| Method | Parameters | Fee in GAS | Return value |
| ---- | ------------------------------------ | ---- | ---- |
| [`GetCommittee`](../scapi/framework/native/Neo/GetCommittee.md) | null | 0.04194304 (CpuFee) | Current committee members in format of ECPoint[] |

## Consensus Nodes

### Function & Scope

Consensus nodes are nodes which are able to start or vote to new block proposals. 

### How are consensus nodes elected

1. Sort the registered candidates by votes
2. Take certain numbers of candidates (7 by default) with the most votes as consensus nodes.
Similar to committee members, consensus nodes are refreshed every 21 blocks.

### Corresponding contract method

| Method | Parameters | Fee in GAS | Return value |
| ---- | ------------------------------------ | ---- | ---- |
|  [`GetNextBlockValidators`](../scapi/framework/native/Neo/GetNextBlockValidators.md)  | null | 0.04194304 (CpuFee) | Consensus nodes by persisting block in format of ECPoint[] |

## Token Distribution

Total NEO amount, or 100 million tokens are distributed in genesis block to standby consensus nodes' multi-signature address.

All interactions in Neo are performed through transactions. Sending a transaction on chain requires paying GAS tokens as fee, including system fee and network fee. System fee will be burnt as resource consumption for transaction execution, while network fee will be distributed to the speaker (the consensus node who starts a new-block proposal) of the block where corresponding transaction is included.

## Nep17 Contract Method

NEO and GAS are [Nep17](https://github.com/neo-project/proposals/blob/master/nep-17.mediawiki) contracts. Nep17 contract methods are as follows:

| Method | Parameters | Fee in GAS | Result |
| ---- | ---- | ---- | ---- |
| [`symbol.md`](symbol.md)  | null | 0 | Token symbol.md in String |
|  [`decimals.md`](decimals.md)  | null | 0 | Token decimals.md in UInt |
| [`TotalSupply`](../scapi/framework/native/Neo/TotalSupply.md) | null | 0.00032768 (CpuFee) | Token total supply in BigInteger |
| [`BalanceOf`](../scapi/framework/native/Neo/BalanceOf.md) | UInt160 account | 0.00032768 (CpuFee) | account balance in BigInteger |
| [`Transfer`](../scapi/framework/native/Neo/Transfer.md) | UInt160 from, UInt160 to, BigInteger amount | 0.00131072 (CpuFee) + 0.0000005 (StorageFee) | Send specified amount of token from Address *from* to Address *to*. Please note that it will check *from*'s signature, whether caller is *from*, whether *to* is payable, whether *from*'s balance is enough |

Contract methods by NEO:

| Method | Parameters | Fee in GAS | Return value |
| ---- | ------------------------------------ | ---- | ---- |
| [`UnclaimedGas`](../scapi/framework/native/Neo/UnclaimedGas.md) | UInt160 account | 0.00131072 (CpuFee) | unclaimed GAS amount of this address in uint |
