---
description: How to integrate via libraries and command line
---

# Integrate Code

## Binance Smart Chain

## web3.js library

### ![](<../../../.gitbook/assets/Screenshot 2021-11-01 at 13.26.10.png>)clientVersion

```
https://rpc.ankr.com/bsc
```

### Example Request

```javascript
curl https://rpc.ankr.com/bsc \
  -X POST \
  -H "Content-Type: application/json" \
  --data '{"jsonrpc":"2.0","method":"web3_clientVersion","params":[],"id":1}'
```

### Example Response

```javascript
{"jsonrpc":"2.0","id":1,"result":"Geth/v1.1.7-74f6b613/linux-amd64/go1.16.10"}
```
