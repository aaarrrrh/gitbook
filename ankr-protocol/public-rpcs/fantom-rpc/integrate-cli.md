---
description: Below are examples of requests that can made via the Command Line Interface
---

# Integrate CLI

## Fantom

## web3

### ![](<../../../.gitbook/assets/Screenshot 2021-11-01 at 13.26.10.png>) clientVersion

```
https://rpc.ankr.com/fantom
```

Returns the current client versions

### Parameters

none

### Returns

`String` - The current client version

#### HEADERS

**Content-Type** application/json

**BODY** raw

```json
{
	"jsonrpc":"2.0",
	"method":"web3_clientVersion",
	"params":[],
	"id":1
} 
```

### Example Request

### Example Request

```
curl https://rpc.ankr.com/fantom \
  -X POST \
  -H "Content-Type: application/json" \
  --data '{"jsonrpc":"2.0","method":"web3_clientVersion","params":[],"id":1}'
```

### Example Response

```javascript
{"jsonrpc":"2.0","id":1,"result":"v0.7.2-rc.1"}
```
