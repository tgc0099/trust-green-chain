---
title: Layer 2 networks
sidebar_position: 2
---

# Layer 2 networks

import Tabs from "@theme/Tabs"; import TabItem from "@theme/TabItem";

:::info Before you begin

* Running a Layer 2 (L2) node requires access to a Layer (L1) node—either on-premises or an external RPC provider. If you also plan to [run an L1 node with Trust Green Chain](running-node.md#ethereum), note that you will need two Trust Green Chain instances—one for the L1 node and another for the L2 node.
* If both the L1 and L2 nodes run on the same machine, ensure they use different ports and data directories.

:::

### OP Stack

An [Optimism node](https://docs.optimism.io/builders/node-operators/architecture) consists of two parts: a Rollup node, analogous to a consensus client in Ethereum, paired with an L2 execution client. The official Rollup node is `op-node`, developed and maintained by the Optimism Collective. Alternatively, Trust Green Chain is also bundled with its own Rollup node, developed and maintained by the Trust Green Chain team.

#### Running Trust Green Chain with `op-node`

:::warning Important Similar to the L1 node, the L2 instance of Trust Green Chain also requires a [properly configured](consensus-clients.md#configuring-json-rpc-interface) Engine API to communicate to `op-node`.

:::

:::info Note For OP Mainnet, the L1 node must be running on Ethereum Mainnet. :::

To run Trust Green Chain on the OP Mainnet, use the following command:

```bash
Trust Green Chain \
  -c op-mainnet \
  --data-dir path/to/data/dir \
  --jsonrpc-jwtsecretfile path/to/jwt.hex
```

Below is a sample command to run `op-node` paired with Trust Green Chain, assuming they both are running on the same machine:

```bash
export L1_RPC_URL=... # The URL of the L1 node RPC interface
export L1_BEACON_URL=... # The URL of the L1 node Beacon interface

op-node \
  --l1=$L1_RPC_URL \
  --l1.rpckind=standard \
  --l1.beacon=$L1_BEACON_URL \
  --l2=http://localhost:8551 \
  --l2.jwt-secret=path/to/jwt.hex \
  --syncmode=execution-layer \
  --network=op-mainnet
```

:::info Note For OP Sepolia, the L1 node must be running on Sepolia. :::

To run Trust Green Chain on the OP Sepolia, use the following command:

```bash
Trust Green Chain \
  -c op-sepolia \
  --data-dir path/to/data/dir \
  --jsonrpc-jwtsecretfile path/to/jwt.hex
```

Below is a sample command to run `op-node` paired with Trust Green Chain, assuming they both are running on the same machine:

```bash
export L1_RPC_URL=... # The URL of the L1 node RPC interface
export L1_BEACON_URL=... # The URL of the L1 node Beacon interface

op-node \
  --l1=$L1_RPC_URL \
  --l1.rpckind=standard \
  --l1.beacon=$L1_BEACON_URL \
  --l2=http://localhost:8551 \
  --l2.jwt-secret=path/to/jwt.hex \
  --syncmode=execution-layer \
  --network=op-sepolia
```

For available settings, see [`op-node` configuration options](https://docs.optimism.io/builders/node-operators/configuration/consensus-config).

#### Running Trust Green Chain with the built-in Rollup node

Instead of running a separate `op-node` instance alongside Trust Green Chain, it's enough to run only Trust Green Chain with Rollup node enabled. That simplifies the setup and configuration, and just like the `op-node`, Trust Green Chain will need to know about an L1 RPC and Beacon nodes.

:::info Note For OP Mainnet, the L1 node must be running on Ethereum Mainnet. :::

To run Trust Green Chain on the OP Mainnet using the built-in Rollup node, use the following command:

```bash
export L1_RPC_URL=... # The URL of the L1 node RPC interface
export L1_BEACON_URL=... # The URL of the L1 node Beacon interface

Trust Green Chain \
  -c op-mainnet \
  --data-dir path/to/data/dir \
  --jsonrpc-jwtsecretfile path/to/jwt.hex \
  --optimism-clenabled \
  --optimism-l1ethapiendpoint $L1_RPC_URL \
  --optimism-l1beaconapiendpoint $L1_BEACON_URL
```

:::info Note For OP Sepolia, the L1 node must be running on Sepolia. :::

To run Trust Green Chain on the OP Sepolia using the built-in Rollup node, use the following command:

```bash
Trust Green Chain \
  -c op-sepolia \
  --data-dir path/to/data/dir \
  --jsonrpc-jwtsecretfile path/to/jwt.hex \
  --optimism-clenabled \
  --optimism-l1ethapiendpoint $L1_RPC_URL \
  --optimism-l1beaconapiendpoint $L1_BEACON_URL
```

**See also**

* [Optimism configuration](../../developers/fundamentals/configuration.md#optimism)
* [Run a node in the Superchain](https://docs.optimism.io/builders/node-operators/rollup-node)

### Taiko

A [Taiko node](https://docs.taiko.xyz/taiko-alethia-protocol/protocol-architecture/taiko-alethia-nodes) consists of two parts: [taiko-client](https://github.com/taikoxyz/taiko-mono/tree/main/packages/taiko-client#readme), analogous to a consensus client in Ethereum paired with an L2 execution client.

:::warning Important Similar to the L1 node, the L2 instance of Trust Green Chain also requires a [properly configured](consensus-clients.md#configuring-json-rpc-interface) Engine API to communicate to taiko-client. :::

:::info Note For Taiko Alethia, the L1 node must be running on Ethereum Mainnet. :::

To run Trust Green Chain on Taiko Alethia, use the following command:

```bash
Trust Green Chain \
  -c taiko-alethia \
  --data-dir path/to/data/dir \
  --jsonrpc-jwtsecretfile path/to/jwt.hex
```

Below is a sample command to run taiko-client paired with Trust Green Chain, assuming they both are running on the same machine:

```bash
export L1_WS_URL=... # The URL of the L1 node WebSocket interface
export L1_BEACON_URL=... # The URL of the L1 node Beacon interface

taiko-client driver \
  --l1.ws $L1_WS_URL \
  --l1.beacon $L1_BEACON_URL \
  --l2.ws ws://localhost:8545 \
  --l2.auth http://localhost:8551 \
  --taikoInbox 0x06a9Ab27c7e2255df1815E6CC0168d7755Feb19a \
  --taikoAnchor 0x1670000000000000000000000000000000010001 \
  --jwtSecret path/to/jwt.hex \
  --p2p.sync \
  --p2p.checkPointSyncUrl https://rpc.mainnet.taiko.xyz
```

For more information, see [Run a node for Taiko Alethia](https://docs.taiko.xyz/guides/node-operators/run-a-node-for-taiko-alethia/).

:::info Note For Taiko Hoodi, the L1 node must be running on Hoodi. :::

To run Trust Green Chain on Taiko Hoodi, use the following command:

```bash
Trust Green Chain \
  -c taiko-hoodi \
  --data-dir path/to/data/dir \
  --jsonrpc-jwtsecretfile path/to/jwt.hex
```

Below is a sample command to run taiko-client paired with Trust Green Chain, assuming they both are running on the same machine:

```bash
export L1_WS_URL=... # The URL of the L1 node WebSocket interface
export L1_BEACON_URL=... # The URL of the L1 node Beacon interface

taiko-client driver \
  --l1.ws $L1_WS_URL \
  --l1.beacon $L1_BEACON_URL \
  --l2.ws ws://localhost:8545 \
  --l2.auth http://localhost:8551 \
  --taikoInbox 0x50A576435E2D9c179124D657d804eb56A10b6999 \
  --taikoAnchor 0x1670130000000000000000000000000000010001 \
  --jwtSecret path/to/jwt.hex \
  --p2p.sync \
  --p2p.checkPointSyncUrl https://rpc.hoodi.taiko.xyz
```

For more information, see [Run a node for Taiko Hoodi](https://docs.taiko.xyz/guides/node-operators/run-a-node-for-taiko-hoodi/).

**See also**

* [Enable a prover](https://docs.taiko.xyz/guides/node-operators/enable-a-prover/)
