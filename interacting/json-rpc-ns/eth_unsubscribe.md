# eth\_unsubscribe

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
