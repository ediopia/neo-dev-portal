---
sidebar_label: '合约费用'
---

# 合约收费机制

用户在使用 Neo 网络时，需要支付一定的费用，总手续费包含系统费 (System Fee) 和网络费 (Network Fee)，费用单位为 GAS。

其中，智能合约执行，包括自身脚本的执行和调用其他合约的脚本，所需的费用为系统手续费。

承载智能合约部署、调用的交易以及执行验证（Verify）方法所需的费用为网络手续费。

一笔调用智能合约的交易的手续费会同时包括系统手续费（sysfee）和网络手续费（netfee）。每一笔交易的 sysfee 都会被燃烧，而 netfee 会奖励给打包当前区块的共识地址。

在 Neo N3 中手续费是可以动态变化的，下面列举的是基础费用。

## 系统手续费

系统手续费（System Fee）包括以下几项：

- 操作码执行（OpCode）费用
- 系统调用（SysCall）费用
- 原生合约 CPU 使用费用
- 存储区使用费用

### 操作码执行（OpCode）费用

| 执行费用（Datoshi） | 操作码（OpCode）指令名称                                     |
| --------------- | ------------------------------------------------------------ |
| 32768      | CALLT                                                        |
| 8192      | VALUES, APPEND, SETITEM, REVERSEITEMS, CONVERT               |
| 4096      | PUSHDATA4                                                    |
| 2048      | MEMCPY, CAT, SUBSTR, LEFT, RIGHT, MODPOW, PACKMAP, PACKSTRUCT, PACK, UNPACK |
| 512      | PUSHDATA2, CALL, CALL_L, CALLA, THROW, NEWARRAY, NEWARRAY_T, NEWSTRUCT |
| 256      | NEWBUFFER                                                    |
| 64      | INITSLOT, POW, SQRT, HASKEY, PICKITEM                        |
| 32      | EQUAL, NOTEQUAL, MODMUL                                      |
| 16      | XDROP, CLEAR, ROLL, REVERSEN, INITSSLOT, NEWARRAY0, NEWSTRUCT0, KEYS, REMOVE, CLEARITEMS, POPITEM |
| 8      | PUSHDATA1, AND, OR, XOR, ADD, SUB, MUL, DIV, MOD, SHL, SHR, BOOLAND, BOOLOR, NUMEQUAL, NUMNOTEQUAL, LT, LE, GT, GE, MIN, MAX, WITHIN, NEWMAP |
| 4      | PUSHINT128, PUSHINT256, PUSHA, TRY, TRY_L, ENDTRY, ENDTRY_L, ENDFINALLY, INVERT, SIGN, ABS, NEGATE, INC, DEC, NOT, NZ, SIZE |
| 2      | JMP, JMP_L, JMPIF, JMPIF_L, JMPIFNOT, JMPIFNOT_L, JMPEQ, JMPEQ_L, JMPNE, JMPNE_L, JMPGT, JMPGT_L, JMPGE, JMPGE_L, JMPLT, JMPLT_L, JMPLE, JMPLE_L, DEPTH, DROP, NIP, DUP, OVER, PICK, TUCK, SWAP, ROT, REVERSE3, REVERSE4, LDSFLD0, LDSFLD1, LDSFLD2, LDSFLD3, LDSFLD4, LDSFLD5, LDSFLD6, LDSFLD, STSFLD0, STSFLD1, STSFLD2, STSFLD3, STSFLD4, STSFLD5, STSFLD6, STSFLD, LDLOC0, LDLOC1, LDLOC2, LDLOC3, LDLOC4, LDLOC5, LDLOC6, LDLOC, STLOC0, STLOC1, STLOC2, STLOC3, STLOC4, STLOC5, STLOC6, STLOC, LDARG0, LDARG1, LDARG2, LDARG3, LDARG4, LDARG5, LDARG6, LDARG, STARG0, STARG1, STARG2, STARG3, STARG4, STARG5, STARG6, STARG, ISNULL, ISTYPE |
| 1      | PUSHINT8, PUSHINT16, PUSHINT32, PUSHINT64, PUSHT, PUSHF, PUSHNULL, PUSHM1, PUSH0, PUSH1, PUSH2, PUSH3, PUSH4, PUSH5, PUSH6, PUSH7, PUSH8, PUSH9, PUSH10, PUSH11, PUSH12, PUSH13, PUSH14, PUSH15, PUSH16, NOP, ASSERT, ASSERTMSG |
| 0               | ABORT, ABORTMSG, RET, SYSCALL                                          |

参考：[ApplicationEngine.OpCodePrices.cs](https://github.com/neo-project/neo/blob/master/src/Neo/SmartContract/ApplicationEngine.OpCodePrices.cs)

### 系统调用费用

| 系统调用名称                          | 执行费用（Datoshi）      |
| ------------------------------------- | -------------------- |
| System.Contract.Call                  | 32768           |
| System.Contract.CallNative            | 参考原生合约费用     |
| System.Contract.IsStandard            | 1024           |
| System.Contract.GetCallFlags          | 1024           |
| System.Contract.CreateStandardAccount | 256           |
| System.Contract.CreateMultisigAccount | 256           |
| Neo.Crypto.CheckSig                   | 32768           |
| Neo.Crypto.CheckMultisig              | 根据签名数量动态计算 |
| System.Iterator.Create                | 16           |
| System.Iterator.Next                  | 32768           |
| System.Iterator.Value                 | 16           |
| System.Runtime.Platform               | 8           |
| System.Runtime.GetTrigger             | 8           |
| System.Runtime.GetTime                | 8           |
| System.Runtime.GetScriptContainer     | 8           |
| System.Runtime.GetExecutingScriptHash | 16           |
| System.Runtime.GetCallingScriptHash   | 16           |
| System.Runtime.GetEntryScriptHash     | 16           |
| System.Runtime.CheckWitness           | 1024           |
| System.Runtime.GetInvocationCounter   | 16           |
| System.Runtime.Log                    | 32768           |
| System.Runtime.Notify                 | 32768           |
| System.Runtime.GetNotifications       | 256           |
| System.Runtime.GasLeft                | 16           |

参考：

[ApplicationEngine.Contract.cs](https://github.com/neo-project/neo/blob/master/src/Neo/SmartContract/ApplicationEngine.Contract.cs)

[ApplicationEngine.Crypto.cs](https://github.com/neo-project/neo/blob/master/src/Neo/SmartContract/ApplicationEngine.Crypto.cs)

[ApplicationEngine.Contract.cs](https://github.com/neo-project/neo/blob/master/src/Neo/SmartContract/ApplicationEngine.Contract.cs)

[ApplicationEngine.Iterator.cs](https://github.com/neo-project/neo/blob/master/src/Neo/SmartContract/ApplicationEngine.Iterator.cs)

[ApplicationEngine.Runtime.cs](https://github.com/neo-project/neo/blob/master/src/Neo/SmartContract/ApplicationEngine.Runtime.cs)

[ApplicationEngine.Storage.cs](https://github.com/neo-project/neo/blob/master/src/neo/SmartContract/ApplicationEngine.Storage.cs)

### 原生合约执行费用

| 原生合约名称       | 原生合约方法            | 执行费用（Datoshi）                 |
| ------------------ | ----------------------- | ------------------------------- |
| ContractManagement | Deploy                  | 参考存储区使用费用，最低 10 GAS |
| ContractManagement | Update                  | 参考存储区使用费用              |
| LedgerContract     | GetTransactionFromBlock | 65536                      |
| NeoToken           | UnclaimedGas            | 131072                      |
| NeoToken           | RegisterCandidate       | 动态计算，默认 1000 GAS         |
| NeoToken           | UnregisterCandidate     | 65536                      |
| NeoToken           | Vote                    | 65536                      |
| NeoToken           | GetCandidates           | 4194304                      |
| NeoToken           | GetCommittee            | 4194304                      |
| NeoToken           | GetNextBlockValidators  | 4194304                      |
| NeoToken、GasToken | Transfer                | 131072                      |
| OracleContract     | Request                 | 动态计算，用户调用时指定手续费  |
| StdLib             | Deserialize             | 8192                      |
| StdLib             | JsonDeserialize         | 8192                      |
| StdLib             | 其他                    | 2048                      |

其他未列出的原生合约方法的手续费均为 32768 Datoshi。

参考： [neo/SmartContract/Native](https://github.com/neo-project/neo/tree/master/src/Neo/SmartContract/Native)

### 存储区费用

按写入字节收费，默认单价为 0.001 GAS / Byte，委员会可动态调整，但最大不会超过 1 GAS / Byte

根据写入的 key 是初次写入还是修改数据，存储区收费规则参见下表。

| 场景                                        | 收费规则                                                     | 示例                                             | 手续费<br/>(默认单价0.001)            |
| ------------------------------------------- | ------------------------------------------------------------ | ------------------------------------------------ | ------------------------------------- |
| 首次写入                                    | (key.Length + value.Length) × 单价                           | key = `key`, value= `hello world`, 共 14 字节    | **0.014** GAS                         |
| 非首次写入存储区，且新数据大小 ≤ 旧数据大小 | 不收取 key 的费用，value 部分首字节正常计费，剩余字节 2.5 折 计费 | 修改 value 为 `hello neo3`, 共 10 字节           | (1+(10-1)/4 )×0.001 = **0.003** GAS   |
| 非首次写入存储区，且新数据大小 > 旧数据大小 | 不收取 key 的费用，value 部分旧数据大小按照上一条计费，新增数据的大小按照原价计费 | 修改 value 为`hello neo3.0`, 共 12 字节          | 0.003 + (12-10)×0.001 = **0.005** GAS |
| 非首次写入存储区，且新数据大小 > 旧数据大小 | 与上一条相同                                                 | 修改 value 为`hello neo3.0 preview5`, 共 21 字节 | 0.005 + (21-12)×0.001 = **0.014** GAS |
| 删除 value                                  | 0                                                            | 删除 value                                       | **0** GAS                             |

参考：[ApplicationEngine.Storage.cs](https://github.com/neo-project/neo/blob/master/src/Neo/SmartContract/ApplicationEngine.Storage.cs)

## 网络手续费

网络手续费（Network Fee）包括以下几项：

- 网络字节费
- 验证脚本执行所需的费用

### 网络字节费

网络字节费默认 0.00001 GAS / Byte，委员会可动态调整。

参考：

[PolicyContract.cs](https://github.com/neo-project/neo/blob/master/src/Neo/SmartContract/Native/PolicyContract.cs)

[Transaction.cs#L302](https://github.com/neo-project/neo/blob/ee898bf41667cdbe3b836b3bd08c2d3199046c2e/src/neo/Network/P2P/Payloads/Transaction.cs#L302)

### 脚本验证费用

验证脚本执行所需的费用最大不超过 0.5 GAS，计算公式为：

`脚本验证费` = `脚本验证执行费` * `倍率`

其中，`脚本验证执行费` = `操作码执行费` + `系统调用费` + `原生合约 CPU 使用费` + `存储区使用费`

`验证脚本默认执行费率倍率` 默认为 30，委员会可动态调整，但最大不得超过 1000。

开发者可以通过 InvokeContractVerify API 估算验证脚本执行所需费用。

例：

标准地址验证脚本费用为 (OpCode.PUSHDATA1 + OpCode.PUSHDATA1 + OpCode.SYSCALL + Neo.Crypto.CheckSig) ×30 = **0.0098352** GAS。

参考：

[PolicyContract.cs](https://github.com/neo-project/neo/blob/master/src/Neo/SmartContract/Native/PolicyContract.cs)

[Transaction.cs#L302](https://github.com/neo-project/neo/blob/ee898bf41667cdbe3b836b3bd08c2d3199046c2e/src/neo/Network/P2P/Payloads/Transaction.cs#L302)
