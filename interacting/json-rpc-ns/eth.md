---
title: eth namespace
sidebar_label: eth
sidebar_position: 3
---

# eth namespace

import Tabs from "@theme/Tabs"; import TabItem from "@theme/TabItem";

#### eth\_blobBaseFee

Returns the base fee per blob gas in wei

```bash
curl localhost:8545 \
  -X POST \
  -H "Content-Type: application/json" \
  --data '{
      "jsonrpc": "2.0",
      "id": 0,
      "method": "eth_blobBaseFee",
      "params": []
    }'
```

```json
{
  "jsonrpc": "2.0",
  "id": 0,
  "result": result
}
```

`result`: _string_ (hex integer)

#### eth\_blockNumber

Returns current block number

```bash
curl localhost:8545 \
  -X POST \
  -H "Content-Type: application/json" \
  --data '{
      "jsonrpc": "2.0",
      "id": 0,
      "method": "eth_blockNumber",
      "params": []
    }'
```

```json
{
  "jsonrpc": "2.0",
  "id": 0,
  "result": result
}
```

`result`: _string_ (hex integer)

#### eth\_call

Executes a tx call (does not create a transaction)

1. `transactionCall`: _object_
   * `blockHash`: _string_ (hash)
   * `blockNumber`: _string_ (hex integer)
   * `blockTimestamp`: _string_ (hex integer)
   * `gas`: _string_ (hex integer)
   * `hash`: _string_ (hash)
   * `transactionIndex`: _string_ (hex integer)
   * `type`: _integer_
2. `blockParameter`: _string_ (block number or hash or either of `earliest`, `finalized`, `latest`, `pending`, or `safe`)
3. `stateOverride`: map of _object_

* `balance`: _string_ (hex integer)
* `code`: _string_ (hex data)
* `movePrecompileToAddress`: _string_ (address)
* `nonce`: _string_ (hex integer)
* `state`: map of _string_ (hash)
* `stateDiff`: map of _string_ (hash)

```bash
curl localhost:8545 \
  -X POST \
  -H "Content-Type: application/json" \
  --data '{
      "jsonrpc": "2.0",
      "id": 0,
      "method": "eth_call",
      "params": [transactionCall, blockParameter, stateOverride]
    }'
```

```json
{
  "jsonrpc": "2.0",
  "id": 0,
  "result": result
}
```

`result`: _string_

#### eth\_chainId

Returns ChainID

```bash
curl localhost:8545 \
  -X POST \
  -H "Content-Type: application/json" \
  --data '{
      "jsonrpc": "2.0",
      "id": 0,
      "method": "eth_chainId",
      "params": []
    }'
```

```json
{
  "jsonrpc": "2.0",
  "id": 0,
  "result": result
}
```

`result`: _string_ (hex integer)

#### eth\_config

Provides configuration data for the current and next fork

```bash
curl localhost:8545 \
  -X POST \
  -H "Content-Type: application/json" \
  --data '{
      "jsonrpc": "2.0",
      "id": 0,
      "method": "eth_config",
      "params": []
    }'
```

```json
{
  "jsonrpc": "2.0",
  "id": 0,
  "result": result
}
```

`result`: _object_

* `item`: _object_
* `item`: _object_
* `options`: _object_
  * `hasValue`: _boolean_
  * `value`: _object_
    * `propertyNameCaseInsensitive`: _boolean_
* `parent`: _object_
* `root`: _object_

#### eth\_createAccessList

Creates an [EIP2930](https://eips.ethereum.org/EIPS/eip-2930) type AccessList for the given transaction

1. `transactionCall`: _object_
   * `blockHash`: _string_ (hash)
   * `blockNumber`: _string_ (hex integer)
   * `blockTimestamp`: _string_ (hex integer)
   * `gas`: _string_ (hex integer)
   * `hash`: _string_ (hash)
   * `transactionIndex`: _string_ (hex integer)
   * `type`: _integer_
2. `blockParameter`: _string_ (block number or hash or either of `earliest`, `finalized`, `latest`, `pending`, or `safe`)
3. `stateOverride`: map of _object_

* `balance`: _string_ (hex integer)
* `code`: _string_ (hex data)
* `movePrecompileToAddress`: _string_ (address)
* `nonce`: _string_ (hex integer)
* `state`: map of _string_ (hash)
* `stateDiff`: map of _string_ (hash)

4. `optimize`: _boolean_

```bash
curl localhost:8545 \
  -X POST \
  -H "Content-Type: application/json" \
  --data '{
      "jsonrpc": "2.0",
      "id": 0,
      "method": "eth_createAccessList",
      "params": [transactionCall, blockParameter, stateOverride, optimize]
    }'
```

```json
{
  "jsonrpc": "2.0",
  "id": 0,
  "result": result
}
```

`result`: _object_

* `accessList`: _object_
* `error`: _string_
* `gasUsed`: _string_ (hex integer)

#### eth\_estimateGas

Executes a tx call and returns gas used (does not create a transaction)

1. `transactionCall`: _object_
   * `blockHash`: _string_ (hash)
   * `blockNumber`: _string_ (hex integer)
   * `blockTimestamp`: _string_ (hex integer)
   * `gas`: _string_ (hex integer)
   * `hash`: _string_ (hash)
   * `transactionIndex`: _string_ (hex integer)
   * `type`: _integer_
2. `blockParameter`: _string_ (block number or hash or either of `earliest`, `finalized`, `latest`, `pending`, or `safe`)
3. `stateOverride`: map of _object_

* `balance`: _string_ (hex integer)
* `code`: _string_ (hex data)
* `movePrecompileToAddress`: _string_ (address)
* `nonce`: _string_ (hex integer)
* `state`: map of _string_ (hash)
* `stateDiff`: map of _string_ (hash)

```bash
curl localhost:8545 \
  -X POST \
  -H "Content-Type: application/json" \
  --data '{
      "jsonrpc": "2.0",
      "id": 0,
      "method": "eth_estimateGas",
      "params": [transactionCall, blockParameter, stateOverride]
    }'
```

```json
{
  "jsonrpc": "2.0",
  "id": 0,
  "result": result
}
```

`result`: _string_ (hex integer)

#### eth\_feeHistory

Returns block fee history.

1. `blockCount`: _string_ (hex integer)
2. `newestBlock`: _string_ (block number or hash or either of `earliest`, `finalized`, `latest`, `pending`, or `safe`)
3. `rewardPercentiles`: array of _object_

```bash
curl localhost:8545 \
  -X POST \
  -H "Content-Type: application/json" \
  --data '{
      "jsonrpc": "2.0",
      "id": 0,
      "method": "eth_feeHistory",
      "params": [blockCount, newestBlock, rewardPercentiles]
    }'
```

```json
{
  "jsonrpc": "2.0",
  "id": 0,
  "result": result
}
```

`result`: _object_

* `baseFeePerBlobGas`: array of _string_ (hex integer)
* `baseFeePerGas`: array of _string_ (hex integer)
* `blobGasUsedRatio`: array of _object_
* `gasUsedRatio`: array of _object_
* `oldestBlock`: _string_ (hex integer)
* `reward`: array of array of _string_ (hex integer)

#### eth\_gasPrice

Returns miner's gas price

```bash
curl localhost:8545 \
  -X POST \
  -H "Content-Type: application/json" \
  --data '{
      "jsonrpc": "2.0",
      "id": 0,
      "method": "eth_gasPrice",
      "params": []
    }'
```

```json
{
  "jsonrpc": "2.0",
  "id": 0,
  "result": result
}
```

`result`: _string_ (hex integer)

#### eth\_getAccount

Retrieves Accounts via Address and Blocknumber

1. `accountAddress`: _string_ (address)
2. `blockParameter`: _string_ (block number or hash or either of `earliest`, `finalized`, `latest`, `pending`, or `safe`)

```bash
curl localhost:8545 \
  -X POST \
  -H "Content-Type: application/json" \
  --data '{
      "jsonrpc": "2.0",
      "id": 0,
      "method": "eth_getAccount",
      "params": [accountAddress, blockParameter]
    }'
```

```json
{
  "jsonrpc": "2.0",
  "id": 0,
  "result": result
}
```

`result`: _object_

* `balance`: _string_ (hex integer)
* `codeHash`: _object_
  * `bytes`: _object_
    * `isEmpty`: _boolean_
    * `item`: _object_
    * `length`: _string_ (hex integer)
  * `bytesAsSpan`: _object_
    * `isEmpty`: _boolean_
    * `item`: _object_
    * `length`: _string_ (hex integer)
* `nonce`: _string_ (hex integer)
* `storageRoot`: _object_
  * `bytes`: _object_
    * `isEmpty`: _boolean_
    * `item`: _object_
    * `length`: _string_ (hex integer)
  * `bytesAsSpan`: _object_
    * `isEmpty`: _boolean_
    * `item`: _object_
    * `length`: _string_ (hex integer)

#### eth\_getAccountInfo

Retrieves Account with code and no storageRoot via Address and Blocknumber

1. `accountAddress`: _string_ (address)
2. `blockParameter`: _string_ (block number or hash or either of `earliest`, `finalized`, `latest`, `pending`, or `safe`)

```bash
curl localhost:8545 \
  -X POST \
  -H "Content-Type: application/json" \
  --data '{
      "jsonrpc": "2.0",
      "id": 0,
      "method": "eth_getAccountInfo",
      "params": [accountAddress, blockParameter]
    }'
```

```json
{
  "jsonrpc": "2.0",
  "id": 0,
  "result": result
}
```

`result`: _object_

* `balance`: _string_ (hex integer)
* `code`: _string_ (hex data)
* `nonce`: _string_ (hex integer)

#### eth\_getBalance

Returns account balance

1. `address`: _string_ (address)
2. `blockParameter`: _string_ (block number or hash or either of `earliest`, `finalized`, `latest`, `pending`, or `safe`)

```bash
curl localhost:8545 \
  -X POST \
  -H "Content-Type: application/json" \
  --data '{
      "jsonrpc": "2.0",
      "id": 0,
      "method": "eth_getBalance",
      "params": [address, blockParameter]
    }'
```

```json
{
  "jsonrpc": "2.0",
  "id": 0,
  "result": result
}
```

`result`: _string_ (hex integer)

#### eth\_getBlockAccessListByHash

Retrieves block access list for a block by hash.

1. `blockHash`: _string_ (hash)

```bash
curl localhost:8545 \
  -X POST \
  -H "Content-Type: application/json" \
  --data '{
      "jsonrpc": "2.0",
      "id": 0,
      "method": "eth_getBlockAccessListByHash",
      "params": [blockHash]
    }'
```

```json
{
  "jsonrpc": "2.0",
  "id": 0,
  "result": result
}
```

`result`: _object_

* `accountChanges`: array of _object_
  * `address`: _string_ (address)
  * `balanceChanges`: array of _object_
    * `blockAccessIndex`: _object_
    * `postBalance`: _string_ (hex integer)
  * `codeChanges`: array of _object_
    * `blockAccessIndex`: _object_
    * `newCode`: _string_ (hex data)
  * `nonceChanges`: array of _object_
    * `blockAccessIndex`: _object_
    * `newNonce`: _string_ (hex integer)
  * `storageChanges`: array of _object_
    * `changes`: map of _object_
      * `blockAccessIndex`: _object_
      * `newValue`: _string_ (hex integer)
    * `slot`: _string_ (hex integer)
  * `storageReads`: array of _object_
    * `key`: _string_ (hex integer)

#### eth\_getBlockAccessListByNumber

Retrieves block access list for a block by number.

1. `number`: _string_ (hex integer)

```bash
curl localhost:8545 \
  -X POST \
  -H "Content-Type: application/json" \
  --data '{
      "jsonrpc": "2.0",
      "id": 0,
      "method": "eth_getBlockAccessListByNumber",
      "params": [number]
    }'
```

```json
{
  "jsonrpc": "2.0",
  "id": 0,
  "result": result
}
```

`result`: _object_

* `accountChanges`: array of _object_
  * `address`: _string_ (address)
  * `balanceChanges`: array of _object_
    * `blockAccessIndex`: _object_
    * `postBalance`: _string_ (hex integer)
  * `codeChanges`: array of _object_
    * `blockAccessIndex`: _object_
    * `newCode`: _string_ (hex data)
  * `nonceChanges`: array of _object_
    * `blockAccessIndex`: _object_
    * `newNonce`: _string_ (hex integer)
  * `storageChanges`: array of _object_
    * `changes`: map of _object_
      * `blockAccessIndex`: _object_
      * `newValue`: _string_ (hex integer)
    * `slot`: _string_ (hex integer)
  * `storageReads`: array of _object_
    * `key`: _string_ (hex integer)

#### eth\_getBlockByHash

Retrieves a block by hash

1. `blockHash`: _string_ (hash)
2. `returnFullTransactionObjects`: _boolean_

```bash
curl localhost:8545 \
  -X POST \
  -H "Content-Type: application/json" \
  --data '{
      "jsonrpc": "2.0",
      "id": 0,
      "method": "eth_getBlockByHash",
      "params": [blockHash, returnFullTransactionObjects]
    }'
```

```json
{
  "jsonrpc": "2.0",
  "id": 0,
  "result": result
}
```

`result`: _object_

* `author`: _string_ (address)
* `baseFeePerGas`: _string_ (hex integer)
* `blobGasUsed`: _string_ (hex integer)
* `blockAccessList`: _object_
  * `accountChanges`: array of _object_
    * `address`: _string_ (address)
    * `balanceChanges`: array of _object_
      * `blockAccessIndex`: _object_
      * `postBalance`: _string_ (hex integer)
    * `codeChanges`: array of _object_
      * `blockAccessIndex`: _object_
      * `newCode`: _string_ (hex data)
    * `nonceChanges`: array of _object_
      * `blockAccessIndex`: _object_
      * `newNonce`: _string_ (hex integer)
    * `storageChanges`: array of _object_
      * `changes`: map of _object_
        * `blockAccessIndex`: _object_
        * `newValue`: _string_ (hex integer)
      * `slot`: _string_ (hex integer)
    * `storageReads`: array of _object_
      * `key`: _string_ (hex integer)
* `blockAccessListHash`: _string_ (hash)
* `difficulty`: _string_ (hex integer)
* `excessBlobGas`: _string_ (hex integer)
* `extraData`: _string_ (hex data)
* `gasLimit`: _string_ (hex integer)
* `gasUsed`: _string_ (hex integer)
* `hash`: _string_ (hash)
* `logsBloom`: _string_ (hex data)
* `miner`: _string_ (address)
* `mixHash`: _string_ (hash)
* `nonce`: _string_ (hex data)
* `number`: _string_ (hex integer)
* `parentBeaconBlockRoot`: _string_ (hash)
* `parentHash`: _string_ (hash)
* `receiptsRoot`: _string_ (hash)
* `requestsHash`: _string_ (hash)
* `sha3Uncles`: _string_ (hash)
* `signature`: _string_ (hex data)
* `size`: _string_ (hex integer)
* `slotNumber`: _string_ (hex integer)
* `stateRoot`: _string_ (hash)
* `step`: _string_ (hex integer)
* `timestamp`: _string_ (hex integer)
* `totalDifficulty`: _string_ (hex integer)
* `transactions`: array of _object_
* `transactionsRoot`: _string_ (hash)
* `uncles`: array of _string_ (hash)
* `withdrawals`: array of _object_
  * `address`: _string_ (address)
  * `amountInGwei`: _string_ (hex integer)
  * `amountInWei`: _string_ (hex integer)
  * `index`: _string_ (hex integer)
  * `validatorIndex`: _string_ (hex integer)
* `withdrawalsRoot`: _string_ (hash)

#### eth\_getBlockByNumber

Retrieves a block by number

1. `blockParameter`: _string_ (block number or hash or either of `earliest`, `finalized`, `latest`, `pending`, or `safe`)
2. `returnFullTransactionObjects`: _boolean_

```bash
curl localhost:8545 \
  -X POST \
  -H "Content-Type: application/json" \
  --data '{
      "jsonrpc": "2.0",
      "id": 0,
      "method": "eth_getBlockByNumber",
      "params": [blockParameter, returnFullTransactionObjects]
    }'
```

```json
{
  "jsonrpc": "2.0",
  "id": 0,
  "result": result
}
```

`result`: _object_

* `author`: _string_ (address)
* `baseFeePerGas`: _string_ (hex integer)
* `blobGasUsed`: _string_ (hex integer)
* `blockAccessList`: _object_
  * `accountChanges`: array of _object_
    * `address`: _string_ (address)
    * `balanceChanges`: array of _object_
      * `blockAccessIndex`: _object_
      * `postBalance`: _string_ (hex integer)
    * `codeChanges`: array of _object_
      * `blockAccessIndex`: _object_
      * `newCode`: _string_ (hex data)
    * `nonceChanges`: array of _object_
      * `blockAccessIndex`: _object_
      * `newNonce`: _string_ (hex integer)
    * `storageChanges`: array of _object_
      * `changes`: map of _object_
        * `blockAccessIndex`: _object_
        * `newValue`: _string_ (hex integer)
      * `slot`: _string_ (hex integer)
    * `storageReads`: array of _object_
      * `key`: _string_ (hex integer)
* `blockAccessListHash`: _string_ (hash)
* `difficulty`: _string_ (hex integer)
* `excessBlobGas`: _string_ (hex integer)
* `extraData`: _string_ (hex data)
* `gasLimit`: _string_ (hex integer)
* `gasUsed`: _string_ (hex integer)
* `hash`: _string_ (hash)
* `logsBloom`: _string_ (hex data)
* `miner`: _string_ (address)
* `mixHash`: _string_ (hash)
* `nonce`: _string_ (hex data)
* `number`: _string_ (hex integer)
* `parentBeaconBlockRoot`: _string_ (hash)
* `parentHash`: _string_ (hash)
* `receiptsRoot`: _string_ (hash)
* `requestsHash`: _string_ (hash)
* `sha3Uncles`: _string_ (hash)
* `signature`: _string_ (hex data)
* `size`: _string_ (hex integer)
* `slotNumber`: _string_ (hex integer)
* `stateRoot`: _string_ (hash)
* `step`: _string_ (hex integer)
* `timestamp`: _string_ (hex integer)
* `totalDifficulty`: _string_ (hex integer)
* `transactions`: array of _object_
* `transactionsRoot`: _string_ (hash)
* `uncles`: array of _string_ (hash)
* `withdrawals`: array of _object_
  * `address`: _string_ (address)
  * `amountInGwei`: _string_ (hex integer)
  * `amountInWei`: _string_ (hex integer)
  * `index`: _string_ (hex integer)
  * `validatorIndex`: _string_ (hex integer)
* `withdrawalsRoot`: _string_ (hash)

#### eth\_getBlockReceipts

Get receipts from all transactions from particular block, more efficient than fetching the receipts one-by-one.

1. `blockParameter`: _string_ (block number or hash or either of `earliest`, `finalized`, `latest`, `pending`, or `safe`)

```bash
curl localhost:8545 \
  -X POST \
  -H "Content-Type: application/json" \
  --data '{
      "jsonrpc": "2.0",
      "id": 0,
      "method": "eth_getBlockReceipts",
      "params": [blockParameter]
    }'
```

```json
{
  "jsonrpc": "2.0",
  "id": 0,
  "result": result
}
```

`result`: array of _object_

* `blobGasPrice`: _string_ (hex integer)
* `blobGasUsed`: _string_ (hex integer)
* `blockHash`: _string_ (hash)
* `blockNumber`: _string_ (hex integer)
* `contractAddress`: _string_ (address)
* `cumulativeGasUsed`: _string_ (hex integer)
* `effectiveGasPrice`: _string_ (hex integer)
* `error`: _string_
* `from`: _string_ (address)
* `gasUsed`: _string_ (hex integer)
* `logs`: array of _object_
  * `address`: _string_ (address)
  * `blockHash`: _string_ (hash)
  * `blockNumber`: _string_ (hex integer)
  * `blockTimestamp`: _string_ (hex integer)
  * `data`: _string_ (hex data)
  * `logIndex`: _string_ (hex integer)
  * `removed`: _boolean_
  * `topics`: array of _string_ (hash)
  * `transactionHash`: _string_ (hash)
  * `transactionIndex`: _string_ (hex integer)
* `logsBloom`: _string_ (hex data)
* `root`: _string_ (hash)
* `status`: _string_ (hex integer)
* `to`: _string_ (address)
* `transactionHash`: _string_ (hash)
* `transactionIndex`: _string_ (hex integer)
* `type`: _integer_

#### eth\_getBlockTransactionCountByHash

Returns number of transactions in the block block hash

1. `blockHash`: _string_ (hash)

```bash
curl localhost:8545 \
  -X POST \
  -H "Content-Type: application/json" \
  --data '{
      "jsonrpc": "2.0",
      "id": 0,
      "method": "eth_getBlockTransactionCountByHash",
      "params": [blockHash]
    }'
```

```json
{
  "jsonrpc": "2.0",
  "id": 0,
  "result": result
}
```

`result`: _string_ (hex integer)

#### eth\_getBlockTransactionCountByNumber

Returns number of transactions in the block by block number

1. `blockParameter`: _string_ (block number or hash or either of `earliest`, `finalized`, `latest`, `pending`, or `safe`)

```bash
curl localhost:8545 \
  -X POST \
  -H "Content-Type: application/json" \
  --data '{
      "jsonrpc": "2.0",
      "id": 0,
      "method": "eth_getBlockTransactionCountByNumber",
      "params": [blockParameter]
    }'
```

```json
{
  "jsonrpc": "2.0",
  "id": 0,
  "result": result
}
```

`result`: _string_ (hex integer)

#### eth\_getCode

Returns account code at given address and block

1. `address`: _string_ (address)
2. `blockParameter`: _string_ (block number or hash or either of `earliest`, `finalized`, `latest`, `pending`, or `safe`)

```bash
curl localhost:8545 \
  -X POST \
  -H "Content-Type: application/json" \
  --data '{
      "jsonrpc": "2.0",
      "id": 0,
      "method": "eth_getCode",
      "params": [address, blockParameter]
    }'
```

```json
{
  "jsonrpc": "2.0",
  "id": 0,
  "result": result
}
```

`result`: _string_ (hex data)

#### eth\_getFilterChanges

Reads filter changes

1. `filterId`: _string_ (hex integer)

```bash
curl localhost:8545 \
  -X POST \
  -H "Content-Type: application/json" \
  --data '{
      "jsonrpc": "2.0",
      "id": 0,
      "method": "eth_getFilterChanges",
      "params": [filterId]
    }'
```

```json
{
  "jsonrpc": "2.0",
  "id": 0,
  "result": result
}
```

`result`: array of _object_

#### eth\_getFilterLogs

Reads filter changes

1. `filterId`: _string_ (hex integer)

```bash
curl localhost:8545 \
  -X POST \
  -H "Content-Type: application/json" \
  --data '{
      "jsonrpc": "2.0",
      "id": 0,
      "method": "eth_getFilterLogs",
      "params": [filterId]
    }'
```

```json
{
  "jsonrpc": "2.0",
  "id": 0,
  "result": result
}
```

`result`: array of _object_

* `address`: _string_ (address)
* `blockHash`: _string_ (hash)
* `blockNumber`: _string_ (hex integer)
* `blockTimestamp`: _string_ (hex integer)
* `data`: _string_ (hex data)
* `logIndex`: _string_ (hex integer)
* `removed`: _boolean_
* `topics`: array of _string_ (hash)
* `transactionHash`: _string_ (hash)
* `transactionIndex`: _string_ (hex integer)

#### eth\_getLogs

Reads logs

1. `filter`: _object_
   * `address`: array of _object_
     * `value`: _string_ (address)
   * `fromBlock`: _string_ (block number or hash or either of `earliest`, `finalized`, `latest`, `pending`, or `safe`)
   * `toBlock`: _string_ (block number or hash or either of `earliest`, `finalized`, `latest`, `pending`, or `safe`)
   * `topics`: array of array of _string_ (hash)
   * `useIndex`: _boolean_

```bash
curl localhost:8545 \
  -X POST \
  -H "Content-Type: application/json" \
  --data '{
      "jsonrpc": "2.0",
      "id": 0,
      "method": "eth_getLogs",
      "params": [filter]
    }'
```

```json
{
  "jsonrpc": "2.0",
  "id": 0,
  "result": result
}
```

`result`: array of _object_

* `address`: _string_ (address)
* `blockHash`: _string_ (hash)
* `blockNumber`: _string_ (hex integer)
* `blockTimestamp`: _string_ (hex integer)
* `data`: _string_ (hex data)
* `logIndex`: _string_ (hex integer)
* `removed`: _boolean_
* `topics`: array of _string_ (hash)
* `transactionHash`: _string_ (hash)
* `transactionIndex`: _string_ (hex integer)

#### eth\_getProof

https://github.com/ethereum/EIPs/issues/1186

1. `accountAddress`: _string_ (address)
2. `storageKeys`: array of _string_ (hex integer)
3. `blockParameter`: _string_ (block number or hash or either of `earliest`, `finalized`, `latest`, `pending`, or `safe`)

```bash
curl localhost:8545 \
  -X POST \
  -H "Content-Type: application/json" \
  --data '{
      "jsonrpc": "2.0",
      "id": 0,
      "method": "eth_getProof",
      "params": [accountAddress, storageKeys, blockParameter]
    }'
```

```json
{
  "jsonrpc": "2.0",
  "id": 0,
  "result": result
}
```

`result`: _object_

* `address`: _string_ (address)
* `balance`: _string_ (hex integer)
* `codeHash`: _string_ (hash)
* `nonce`: _string_ (hex integer)
* `proof`: array of _string_ (hex data)
* `storageProofs`: array of _object_
  * `key`: _string_
  * `proof`: array of _string_ (hex data)
  * `value`: _object_
    * `hasValue`: _boolean_
    * `value`: _object_
      * `isEmpty`: _boolean_
      * `length`: _string_ (hex integer)
      * `span`: _object_
        * `isEmpty`: _boolean_
        * `item`: _object_
        * `length`: _string_ (hex integer)
* `storageRoot`: _string_ (hash)

#### eth\_getRawTransactionByHash

Retrieves a transaction RLP by hash

1. `transactionHash`: _string_ (hash)

```bash
curl localhost:8545 \
  -X POST \
  -H "Content-Type: application/json" \
  --data '{
      "jsonrpc": "2.0",
      "id": 0,
      "method": "eth_getRawTransactionByHash",
      "params": [transactionHash]
    }'
```

```json
{
  "jsonrpc": "2.0",
  "id": 0,
  "result": result
}
```

`result`: _string_

#### eth\_getStorageAt

Returns storage data at address. storage\_index

1. `address`: _string_ (address)
2. `positionIndex`: _string_ (hex integer)
3. `blockParameter`: _string_ (block number or hash or either of `earliest`, `finalized`, `latest`, `pending`, or `safe`)

```bash
curl localhost:8545 \
  -X POST \
  -H "Content-Type: application/json" \
  --data '{
      "jsonrpc": "2.0",
      "id": 0,
      "method": "eth_getStorageAt",
      "params": [address, positionIndex, blockParameter]
    }'
```

```json
{
  "jsonrpc": "2.0",
  "id": 0,
  "result": result
}
```

`result`: _string_ (hex data)

#### eth\_getTransactionByBlockHashAndIndex

Retrieves a transaction by block hash and index

1. `blockHash`: _string_ (hash)
2. `positionIndex`: _string_ (hex integer)

```bash
curl localhost:8545 \
  -X POST \
  -H "Content-Type: application/json" \
  --data '{
      "jsonrpc": "2.0",
      "id": 0,
      "method": "eth_getTransactionByBlockHashAndIndex",
      "params": [blockHash, positionIndex]
    }'
```

```json
{
  "jsonrpc": "2.0",
  "id": 0,
  "result": result
}
```

`result`: _object_

* `blockHash`: _string_ (hash)
* `blockNumber`: _string_ (hex integer)
* `blockTimestamp`: _string_ (hex integer)
* `gas`: _string_ (hex integer)
* `hash`: _string_ (hash)
* `transactionIndex`: _string_ (hex integer)
* `type`: _integer_

#### eth\_getTransactionByBlockNumberAndIndex

Retrieves a transaction by block number and index

1. `blockParameter`: _string_ (block number or hash or either of `earliest`, `finalized`, `latest`, `pending`, or `safe`)
2. `positionIndex`: _string_ (hex integer)

```bash
curl localhost:8545 \
  -X POST \
  -H "Content-Type: application/json" \
  --data '{
      "jsonrpc": "2.0",
      "id": 0,
      "method": "eth_getTransactionByBlockNumberAndIndex",
      "params": [blockParameter, positionIndex]
    }'
```

```json
{
  "jsonrpc": "2.0",
  "id": 0,
  "result": result
}
```

`result`: _object_

* `blockHash`: _string_ (hash)
* `blockNumber`: _string_ (hex integer)
* `blockTimestamp`: _string_ (hex integer)
* `gas`: _string_ (hex integer)
* `hash`: _string_ (hash)
* `transactionIndex`: _string_ (hex integer)
* `type`: _integer_

#### eth\_getTransactionByHash

Retrieves a transaction by hash

1. `transactionHash`: _string_ (hash)

```bash
curl localhost:8545 \
  -X POST \
  -H "Content-Type: application/json" \
  --data '{
      "jsonrpc": "2.0",
      "id": 0,
      "method": "eth_getTransactionByHash",
      "params": [transactionHash]
    }'
```

```json
{
  "jsonrpc": "2.0",
  "id": 0,
  "result": result
}
```

`result`: _object_

* `blockHash`: _string_ (hash)
* `blockNumber`: _string_ (hex integer)
* `blockTimestamp`: _string_ (hex integer)
* `gas`: _string_ (hex integer)
* `hash`: _string_ (hash)
* `transactionIndex`: _string_ (hex integer)
* `type`: _integer_

#### eth\_getTransactionCount

Returns account nonce (number of transactions from the account since genesis) at the given block number

1. `address`: _string_ (address)
2. `blockParameter`: _string_ (block number or hash or either of `earliest`, `finalized`, `latest`, `pending`, or `safe`)

```bash
curl localhost:8545 \
  -X POST \
  -H "Content-Type: application/json" \
  --data '{
      "jsonrpc": "2.0",
      "id": 0,
      "method": "eth_getTransactionCount",
      "params": [address, blockParameter]
    }'
```

```json
{
  "jsonrpc": "2.0",
  "id": 0,
  "result": result
}
```

`result`: _string_ (hex integer)

#### eth\_getTransactionReceipt

Retrieves a transaction receipt by tx hash

1. `txHashData`: _string_ (hash)

```bash
curl localhost:8545 \
  -X POST \
  -H "Content-Type: application/json" \
  --data '{
      "jsonrpc": "2.0",
      "id": 0,
      "method": "eth_getTransactionReceipt",
      "params": [txHashData]
    }'
```

```json
{
  "jsonrpc": "2.0",
  "id": 0,
  "result": result
}
```

`result`: _object_

* `blobGasPrice`: _string_ (hex integer)
* `blobGasUsed`: _string_ (hex integer)
* `blockHash`: _string_ (hash)
* `blockNumber`: _string_ (hex integer)
* `contractAddress`: _string_ (address)
* `cumulativeGasUsed`: _string_ (hex integer)
* `effectiveGasPrice`: _string_ (hex integer)
* `error`: _string_
* `from`: _string_ (address)
* `gasUsed`: _string_ (hex integer)
* `logs`: array of _object_
  * `address`: _string_ (address)
  * `blockHash`: _string_ (hash)
  * `blockNumber`: _string_ (hex integer)
  * `blockTimestamp`: _string_ (hex integer)
  * `data`: _string_ (hex data)
  * `logIndex`: _string_ (hex integer)
  * `removed`: _boolean_
  * `topics`: array of _string_ (hash)
  * `transactionHash`: _string_ (hash)
  * `transactionIndex`: _string_ (hex integer)
* `logsBloom`: _string_ (hex data)
* `root`: _string_ (hash)
* `status`: _string_ (hex integer)
* `to`: _string_ (address)
* `transactionHash`: _string_ (hash)
* `transactionIndex`: _string_ (hex integer)
* `type`: _integer_

#### eth\_getUncleByBlockHashAndIndex

Retrieves an uncle block header by block hash and uncle index

1. `blockHashData`: _string_ (hash)
2. `positionIndex`: _string_ (hex integer)

```bash
curl localhost:8545 \
  -X POST \
  -H "Content-Type: application/json" \
  --data '{
      "jsonrpc": "2.0",
      "id": 0,
      "method": "eth_getUncleByBlockHashAndIndex",
      "params": [blockHashData, positionIndex]
    }'
```

```json
{
  "jsonrpc": "2.0",
  "id": 0,
  "result": result
}
```

`result`: _object_

* `author`: _string_ (address)
* `baseFeePerGas`: _string_ (hex integer)
* `blobGasUsed`: _string_ (hex integer)
* `blockAccessList`: _object_
  * `accountChanges`: array of _object_
    * `address`: _string_ (address)
    * `balanceChanges`: array of _object_
      * `blockAccessIndex`: _object_
      * `postBalance`: _string_ (hex integer)
    * `codeChanges`: array of _object_
      * `blockAccessIndex`: _object_
      * `newCode`: _string_ (hex data)
    * `nonceChanges`: array of _object_
      * `blockAccessIndex`: _object_
      * `newNonce`: _string_ (hex integer)
    * `storageChanges`: array of _object_
      * `changes`: map of _object_
        * `blockAccessIndex`: _object_
        * `newValue`: _string_ (hex integer)
      * `slot`: _string_ (hex integer)
    * `storageReads`: array of _object_
      * `key`: _string_ (hex integer)
* `blockAccessListHash`: _string_ (hash)
* `difficulty`: _string_ (hex integer)
* `excessBlobGas`: _string_ (hex integer)
* `extraData`: _string_ (hex data)
* `gasLimit`: _string_ (hex integer)
* `gasUsed`: _string_ (hex integer)
* `hash`: _string_ (hash)
* `logsBloom`: _string_ (hex data)
* `miner`: _string_ (address)
* `mixHash`: _string_ (hash)
* `nonce`: _string_ (hex data)
* `number`: _string_ (hex integer)
* `parentBeaconBlockRoot`: _string_ (hash)
* `parentHash`: _string_ (hash)
* `receiptsRoot`: _string_ (hash)
* `requestsHash`: _string_ (hash)
* `sha3Uncles`: _string_ (hash)
* `signature`: _string_ (hex data)
* `size`: _string_ (hex integer)
* `slotNumber`: _string_ (hex integer)
* `stateRoot`: _string_ (hash)
* `step`: _string_ (hex integer)
* `timestamp`: _string_ (hex integer)
* `totalDifficulty`: _string_ (hex integer)
* `transactions`: array of _object_
* `transactionsRoot`: _string_ (hash)
* `uncles`: array of _string_ (hash)
* `withdrawals`: array of _object_
  * `address`: _string_ (address)
  * `amountInGwei`: _string_ (hex integer)
  * `amountInWei`: _string_ (hex integer)
  * `index`: _string_ (hex integer)
  * `validatorIndex`: _string_ (hex integer)
* `withdrawalsRoot`: _string_ (hash)

#### eth\_getUncleByBlockNumberAndIndex

Retrieves an uncle block header by block number and uncle index

1. `blockParameter`: _string_ (block number or hash or either of `earliest`, `finalized`, `latest`, `pending`, or `safe`)
2. `positionIndex`: _string_ (hex integer)

```bash
curl localhost:8545 \
  -X POST \
  -H "Content-Type: application/json" \
  --data '{
      "jsonrpc": "2.0",
      "id": 0,
      "method": "eth_getUncleByBlockNumberAndIndex",
      "params": [blockParameter, positionIndex]
    }'
```

```json
{
  "jsonrpc": "2.0",
  "id": 0,
  "result": result
}
```

`result`: _object_

* `author`: _string_ (address)
* `baseFeePerGas`: _string_ (hex integer)
* `blobGasUsed`: _string_ (hex integer)
* `blockAccessList`: _object_
  * `accountChanges`: array of _object_
    * `address`: _string_ (address)
    * `balanceChanges`: array of _object_
      * `blockAccessIndex`: _object_
      * `postBalance`: _string_ (hex integer)
    * `codeChanges`: array of _object_
      * `blockAccessIndex`: _object_
      * `newCode`: _string_ (hex data)
    * `nonceChanges`: array of _object_
      * `blockAccessIndex`: _object_
      * `newNonce`: _string_ (hex integer)
    * `storageChanges`: array of _object_
      * `changes`: map of _object_
        * `blockAccessIndex`: _object_
        * `newValue`: _string_ (hex integer)
      * `slot`: _string_ (hex integer)
    * `storageReads`: array of _object_
      * `key`: _string_ (hex integer)
* `blockAccessListHash`: _string_ (hash)
* `difficulty`: _string_ (hex integer)
* `excessBlobGas`: _string_ (hex integer)
* `extraData`: _string_ (hex data)
* `gasLimit`: _string_ (hex integer)
* `gasUsed`: _string_ (hex integer)
* `hash`: _string_ (hash)
* `logsBloom`: _string_ (hex data)
* `miner`: _string_ (address)
* `mixHash`: _string_ (hash)
* `nonce`: _string_ (hex data)
* `number`: _string_ (hex integer)
* `parentBeaconBlockRoot`: _string_ (hash)
* `parentHash`: _string_ (hash)
* `receiptsRoot`: _string_ (hash)
* `requestsHash`: _string_ (hash)
* `sha3Uncles`: _string_ (hash)
* `signature`: _string_ (hex data)
* `size`: _string_ (hex integer)
* `slotNumber`: _string_ (hex integer)
* `stateRoot`: _string_ (hash)
* `step`: _string_ (hex integer)
* `timestamp`: _string_ (hex integer)
* `totalDifficulty`: _string_ (hex integer)
* `transactions`: array of _object_
* `transactionsRoot`: _string_ (hash)
* `uncles`: array of _string_ (hash)
* `withdrawals`: array of _object_
  * `address`: _string_ (address)
  * `amountInGwei`: _string_ (hex integer)
  * `amountInWei`: _string_ (hex integer)
  * `index`: _string_ (hex integer)
  * `validatorIndex`: _string_ (hex integer)
* `withdrawalsRoot`: _string_ (hash)

#### eth\_getUncleCountByBlockHash

Returns number of uncles in the block by block hash

1. `blockHash`: _string_ (hash)

```bash
curl localhost:8545 \
  -X POST \
  -H "Content-Type: application/json" \
  --data '{
      "jsonrpc": "2.0",
      "id": 0,
      "method": "eth_getUncleCountByBlockHash",
      "params": [blockHash]
    }'
```

```json
{
  "jsonrpc": "2.0",
  "id": 0,
  "result": result
}
```

`result`: _string_ (hex integer)

#### eth\_getUncleCountByBlockNumber

Returns number of uncles in the block by block number

1. `blockParameter`: _string_ (block number or hash or either of `earliest`, `finalized`, `latest`, `pending`, or `safe`)

```bash
curl localhost:8545 \
  -X POST \
  -H "Content-Type: application/json" \
  --data '{
      "jsonrpc": "2.0",
      "id": 0,
      "method": "eth_getUncleCountByBlockNumber",
      "params": [blockParameter]
    }'
```

```json
{
  "jsonrpc": "2.0",
  "id": 0,
  "result": result
}
```

`result`: _string_ (hex integer)

#### eth\_newBlockFilter

Creates an update filter

```bash
curl localhost:8545 \
  -X POST \
  -H "Content-Type: application/json" \
  --data '{
      "jsonrpc": "2.0",
      "id": 0,
      "method": "eth_newBlockFilter",
      "params": []
    }'
```

```json
{
  "jsonrpc": "2.0",
  "id": 0,
  "result": result
}
```

`result`: _string_ (hex integer)

#### eth\_newFilter

Creates an update filter

1. `filter`: _object_
   * `address`: array of _object_
     * `value`: _string_ (address)
   * `fromBlock`: _string_ (block number or hash or either of `earliest`, `finalized`, `latest`, `pending`, or `safe`)
   * `toBlock`: _string_ (block number or hash or either of `earliest`, `finalized`, `latest`, `pending`, or `safe`)
   * `topics`: array of array of _string_ (hash)
   * `useIndex`: _boolean_

```bash
curl localhost:8545 \
  -X POST \
  -H "Content-Type: application/json" \
  --data '{
      "jsonrpc": "2.0",
      "id": 0,
      "method": "eth_newFilter",
      "params": [filter]
    }'
```

```json
{
  "jsonrpc": "2.0",
  "id": 0,
  "result": result
}
```

`result`: _string_ (hex integer)

#### eth\_newPendingTransactionFilter

Creates an update filter

```bash
curl localhost:8545 \
  -X POST \
  -H "Content-Type: application/json" \
  --data '{
      "jsonrpc": "2.0",
      "id": 0,
      "method": "eth_newPendingTransactionFilter",
      "params": []
    }'
```

```json
{
  "jsonrpc": "2.0",
  "id": 0,
  "result": result
}
```

`result`: _string_ (hex integer)

#### eth\_pendingTransactions

Returns the pending transactions list

```bash
curl localhost:8545 \
  -X POST \
  -H "Content-Type: application/json" \
  --data '{
      "jsonrpc": "2.0",
      "id": 0,
      "method": "eth_pendingTransactions",
      "params": []
    }'
```

```json
{
  "jsonrpc": "2.0",
  "id": 0,
  "result": result
}
```

`result`: array of _object_

* `blockHash`: _string_ (hash)
* `blockNumber`: _string_ (hex integer)
* `blockTimestamp`: _string_ (hex integer)
* `gas`: _string_ (hex integer)
* `hash`: _string_ (hash)
* `transactionIndex`: _string_ (hex integer)
* `type`: _integer_

#### eth\_protocolVersion

Returns ETH protocol version

```bash
curl localhost:8545 \
  -X POST \
  -H "Content-Type: application/json" \
  --data '{
      "jsonrpc": "2.0",
      "id": 0,
      "method": "eth_protocolVersion",
      "params": []
    }'
```

```json
{
  "jsonrpc": "2.0",
  "id": 0,
  "result": result
}
```

`result`: _string_

#### eth\_sendRawTransaction

Send a raw transaction to the tx pool and broadcasting

1. `transaction`: _string_ (hex data)

```bash
curl localhost:8545 \
  -X POST \
  -H "Content-Type: application/json" \
  --data '{
      "jsonrpc": "2.0",
      "id": 0,
      "method": "eth_sendRawTransaction",
      "params": [transaction]
    }'
```

```json
{
  "jsonrpc": "2.0",
  "id": 0,
  "result": result
}
```

`result`: _string_ (hash)

#### eth\_sendTransaction

Send a transaction to the tx pool and broadcasting

1. `rpcTx`: _object_
   * `blockHash`: _string_ (hash)
   * `blockNumber`: _string_ (hex integer)
   * `blockTimestamp`: _string_ (hex integer)
   * `gas`: _string_ (hex integer)
   * `hash`: _string_ (hash)
   * `transactionIndex`: _string_ (hex integer)
   * `type`: _integer_

```bash
curl localhost:8545 \
  -X POST \
  -H "Content-Type: application/json" \
  --data '{
      "jsonrpc": "2.0",
      "id": 0,
      "method": "eth_sendTransaction",
      "params": [rpcTx]
    }'
```

```json
{
  "jsonrpc": "2.0",
  "id": 0,
  "result": result
}
```

`result`: _string_ (hash)

#### eth\_simulateV1

Executes a simulation across multiple blocks (does not create a transaction or block)

1. `payload`: _object_
   * `blockStateCalls`: array of _object_
     * `blockOverrides`: _object_
       * `baseFeePerGas`: _string_ (hex integer)
       * `blobBaseFee`: _string_ (hex integer)
       * `feeRecipient`: _string_ (address)
       * `gasLimit`: _string_ (hex integer)
       * `number`: _string_ (hex integer)
       * `prevRandao`: _string_ (hash)
       * `time`: _string_ (hex integer)
     * `calls`: array of _object_
       * `blockHash`: _string_ (hash)
       * `blockNumber`: _string_ (hex integer)
       * `blockTimestamp`: _string_ (hex integer)
       * `gas`: _string_ (hex integer)
       * `hash`: _string_ (hash)
       * `transactionIndex`: _string_ (hex integer)
       * `type`: _integer_
     * `stateOverrides`: map of _object_
       * `balance`: _string_ (hex integer)
       * `code`: _string_ (hex data)
       * `movePrecompileToAddress`: _string_ (address)
       * `nonce`: _string_ (hex integer)
       * `state`: map of _string_ (hash)
       * `stateDiff`: map of _string_ (hash)
   * `returnFullTransactionObjects`: _boolean_
   * `returnFullTransactions`: _boolean_
   * `traceTransfers`: _boolean_
   * `validation`: _boolean_
2. `blockParameter`: _string_ (block number or hash or either of `earliest`, `finalized`, `latest`, `pending`, or `safe`)

```bash
curl localhost:8545 \
  -X POST \
  -H "Content-Type: application/json" \
  --data '{
      "jsonrpc": "2.0",
      "id": 0,
      "method": "eth_simulateV1",
      "params": [payload, blockParameter]
    }'
```

```json
{
  "jsonrpc": "2.0",
  "id": 0,
  "result": result
}
```

`result`: array of _object_

* `calls`: array of _object_
  * `error`: _object_
    * `code`: _string_ (hex integer)
    * `data`: _string_ (hex data)
    * `evmException`: _integer_
    * `message`: _string_
  * `gasUsed`: _string_ (hex integer)
  * `logs`: array of _object_
    * `address`: _string_ (address)
    * `blockHash`: _string_ (hash)
    * `blockNumber`: _string_ (hex integer)
    * `blockTimestamp`: _string_ (hex integer)
    * `data`: _string_ (hex data)
    * `logIndex`: _string_ (hex integer)
    * `removed`: _boolean_
    * `topics`: array of _string_ (hash)
    * `transactionHash`: _string_ (hash)
    * `transactionIndex`: _string_ (hex integer)
  * `returnData`: _string_ (hex data)
  * `status`: _string_ (hex integer)
* `traces`: array of _object_
  * `error`: _object_
    * `code`: _string_ (hex integer)
    * `data`: _string_ (hex data)
    * `evmException`: _integer_
    * `message`: _string_
  * `gasUsed`: _string_ (hex integer)
  * `logs`: array of _object_
    * `address`: _string_ (address)
    * `blockHash`: _string_ (hash)
    * `blockNumber`: _string_ (hex integer)
    * `blockTimestamp`: _string_ (hex integer)
    * `data`: _string_ (hex data)
    * `logIndex`: _string_ (hex integer)
    * `removed`: _boolean_
    * `topics`: array of _string_ (hash)
    * `transactionHash`: _string_ (hash)
    * `transactionIndex`: _string_ (hex integer)
  * `returnData`: _string_ (hex data)
  * `status`: _string_ (hex integer)

#### eth\_subscribe

Starts a subscription to a particular event over WebSockets. A JSON-RPC notification with event payload and subscription id is sent to a client for every event matching the subscription topic.

:::info This method is enabled by adding `subscribe` to [`JsonRpc.EnabledModules`](../../developers/fundamentals/configuration.md#jsonrpc-enabledmodules). :::

1. `subscriptionName`: _string_
2. `filter`: _object_
   * `address`: _string_ (address)
   * `fromBlock`: _string_ (block number or hash or either of `earliest`, `finalized`, `latest`, `pending`, or `safe`)
   * `toBlock`: _string_ (block number or hash or either of `earliest`, `finalized`, `latest`, `pending`, or `safe`)
   * `topics`: array of _string_ (hex data)

```bash
wscat -c localhost:8545
```

```json
{
  "jsonrpc": "2.0",
  "id": 0,
  "method": "eth_subscribe",
  "params": [subscriptionName, args]
}
```

```json
{
  "jsonrpc": "2.0",
  "id": 0,
  "result": "0x..." // subscription id
}
```

`result`: _string_

```json
{
  "jsonrpc": "2.0",
  "method": "eth_subscription",
  "params": {
    "subscription": "0x...", // subscription id
    "result": payload
  }
}
```

See specific subcription topic below for `payload` details.

**Subscription topics**

<details>

<summary><strong>newHeads</strong></summary>

Subscribes to incoming block headers. Fires a notification each time a new header is appended to the chain, including chain reorganizations.

Notification `payload`: _object_

* `author`: _string_ (address)
* `baseFeePerGas`: _string_ (hex integer)
* `blobGasUsed`: _string_ (hex integer)
* `difficulty`: _string_ (hex integer)
* `excessBlobGas`: _string_ (hex integer)
* `extraData`: _string_ (hex data)
* `gasLimit`: _string_ (hex integer)
* `gasUsed`: _string_ (hex integer)
* `hash`: _string_ (hash)
* `logsBloom`: _string_ (hex data)
* `miner`: _string_ (address)
* `mixHash`: _string_ (hash)
* `nonce`: _string_ (hex data)
* `number`: _string_ (hex integer)
* `parentBeaconBlockRoot`: _string_ (hash)
* `parentHash`: _string_ (hash)
* `receiptsRoot`: _string_ (hash)
* `sha3Uncles`: _string_ (hash)
* `signature`: _string_ (hex data)
* `size`: _string_ (hex integer)
* `stateRoot`: _string_ (hash)
* `step`: _string_ (hex integer)
* `timestamp`: _string_ (hex integer)
* `totalDifficulty`: _string_ (hex integer)
* `transactions`: array of _object_
* `transactionsRoot`: _string_ (hash)
* `uncles`: array of _string_ (hash)
* `withdrawals`: array of _object_
  * `address`: _string_ (address)
  * `amount`: _string_ (hex integer)
  * `index`: _string_ (hex integer)
  * `validatorIndex`: _string_ (hex integer)
* `withdrawalsRoot`: _string_ (hash)

</details>

<details>

<summary><strong>logs</strong></summary>

Subscribes to incoming logs filtered by the given options. In case of a chain reorganization, previously sent logs on the old chain will be re-sent with the `removed` field set to `true`.

Notification `payload`: _object_

* `address`: _string_ (address)
* `blockHash`: _string_ (hash)
* `blockNumber`: _string_ (hex integer)
* `data`: _string_ (hex data)
* `logIndex`: _string_ (hex integer)
* `removed`: _boolean_
* `topics`: array of _string_ (hash)
* `transactionHash`: _string_ (hash)
* `transactionIndex`: _string_ (hex integer)
* `transactionLogIndex`: _string_ (hex integer)

</details>

<details>

<summary><strong>newPendingTransactions</strong></summary>

Subscribes to incoming pending transactions. Returns the transaction hash.

Notification `payload`: _string_ (hash)

</details>

<details>

<summary><strong>droppedPendingTransactions</strong></summary>

Subscribes to transactions evicted from the transaction pool. Returns the transaction hash.

Notification `payload`: _string_ (hash)

</details>

<details>

<summary><strong>syncing</strong></summary>

Subscribes to syncing events. Returns `false` (once) if the node is synced or an object with statistics (once) when the node starts syncing.

Notification `payload`:

* if synced: _boolean_
* if syncing: _object_
  * `currentBlock`: _string_ (hex integer)
  * `highestBlock`: _string_ (hex integer)
  * `isSyncing`: _boolean_
  * `startingBlock`: _string_ (hex integer)

</details>

\### eth\_syncing

Returns syncing status

```bash
curl localhost:8545 \
  -X POST \
  -H "Content-Type: application/json" \
  --data '{
      "jsonrpc": "2.0",
      "id": 0,
      "method": "eth_syncing",
      "params": []
    }'
```

```json
{
  "jsonrpc": "2.0",
  "id": 0,
  "result": result
}
```

`result`: _object_

* `currentBlock`: _string_ (hex integer)
* `highestBlock`: _string_ (hex integer)
* `isSyncing`: _boolean_
* `startingBlock`: _string_ (hex integer)
* `syncMode`: _integer_

#### eth\_uninstallFilter

Creates an update filter

1. `filterId`: _string_ (hex integer)

```bash
curl localhost:8545 \
  -X POST \
  -H "Content-Type: application/json" \
  --data '{
      "jsonrpc": "2.0",
      "id": 0,
      "method": "eth_uninstallFilter",
      "params": [filterId]
    }'
```

```json
{
  "jsonrpc": "2.0",
  "id": 0,
  "result": result
}
```

`result`: _boolean_

#### eth\_unsubscribe

Unsubscribes from a subscription.

:::info This method is enabled by adding `subscribe` to [`JsonRpc.EnabledModules`](../../developers/fundamentals/configuration.md#jsonrpc-enabledmodules). :::

1. `subscriptionId`: _string_

```bash
wscat -c localhost:8545
```

```json
{
  "jsonrpc": "2.0",
  "id": 0,
  "method": "eth_unsubscribe",
  "params": [subscriptionId]
}
```

```json
{
  "jsonrpc": "2.0",
  "id": 0,
  "result": result
}
```

`result`: _boolean_ (`true` if unsubscribed successfully; otherwise, `false`)
