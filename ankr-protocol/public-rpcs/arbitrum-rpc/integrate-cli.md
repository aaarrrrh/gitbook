---
description: Below are examples of requests that can made via the Command Line Interface
---

# Integrate Code

## Arbitrum

## web3 library

### ![](<../../../.gitbook/assets/Screenshot 2021-11-01 at 13.26.10.png>)clientVersion

```
https://rpc.ankr.com/arbitrum
```



### Example Request

```shell
curl https://rpc.ankr.com/arbitrum \
  -X POST \
  -H "Content-Type: application/json" \
  --data '{"jsonrpc":"2.0","method":"web3_clientVersion","params":[],"id":1}'
```

### Example Response

```javascript
{"jsonrpc":"2.0","id":1,"result":"arb-rpc-node/v0.8.0"}
```
