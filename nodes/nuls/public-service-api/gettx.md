---
description: Get transaction details
---

# getTx

## Example

```javascript
// Request
curl -s -X POST -H 'Content-Type: application/json' --data '{"jsonrpc":"2.0","method":"getTx","params":[1,"37d55ef078dae885f1c9c17569592f2aa0123073652f99c04ff56a2cb87ce302"], "id":1234}' http://<your-app-id>.ankr.com

// Result
{
  "jsonrpc": "2.0",
  "id": "1234",
  "result": {
    "hash": "37d55ef078dae885f1c9c17569592f2aa0123073652f99c04ff56a2cb87ce302",
    "type": 1,
    "height": 37,
    "size": 12,
    "fee": {
      "chainId": 1,
      "assetId": 1,
      "symbol": "NULS",
      "value": 0
    },
    "createTime": 1568209860,
    "remark": null,
    "txDataHex": null,
    "txData": {
      "roundIndex": 1574,
      "packageIndex": 2,
      "agentId": "b87ce302"
    },
    "txDataList": null,
    "coinFroms": [],
    "coinTos": [],
    "value": 0,
    "status": 1
  }
}
```

