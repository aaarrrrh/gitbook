---
description: >-
  In this section, we provide some basic examples for interacting with CKB's
  RPCs via your Command Line or Terminal
---

# Example Calls

## `` `sync_state` `` Method

### _Returns sync state of this node_

### EXAMPLE REQUEST

```bash
curl https://app-<YOUR-API-ENDPOINT>.hk.ankr.com \
-X POST \
-H "Content-Type: application/json" \
-d '{"jsonrpc":"2.0","method":"sync_state","params":[],"id":73}'
```

### EXAMPLE RESPONSE

```javascript
{
  "jsonrpc": "2.0",
  "result": {
    "best_known_block_number": "0x283431",
    "best_known_block_timestamp": "0x17ba113eb9d",
    "fast_time": "0x1c24",
    "ibd": false,
    "inflight_blocks_count": "0x0",
    "low_time": "0x4121",
    "normal_time": "0x3fec",
    "orphan_blocks_count": "0x2"
  },
  "id": 73
}
```

## `` `get_tip_block_number` `` Method

### _Returns the number of blocks in the longest blockchain._

### EXAMPLE REQUEST

```bash
curl --request POST 'https://app-<YOUR-API-ENDPOINT>.hk.ankr.com' \
-H 'content-type: application/json' \
-d'{
"id": 42,
"jsonrpc": "2.0",
"method": "get_tip_block_number",
"params": []
}'

```

### EXAMPLE RESPONSE

```javascript
{
"jsonrpc":"2.0",
"result":"0x4ff2a4",
"id":42
}
```
