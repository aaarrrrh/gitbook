---
description: >-
  Get information about the chain, where the consensus asset is the asset that
  needs to be used when creating a consensus node transaction and creating a
  delegation consensus transaction for this chain.
---

# info

## **Example** <a href="example" id="example"></a>

```javascript
// Request
curl -s -X POST -H 'Content-Type: application/json' --data '{"jsonrpc":"2.0","method":"info","params":[], "id":1234}' http://<your-app-id>.ankr.com/jsonrpc

// Result
{
    "jsonrpc": "2.0",
    "id": "1234",
    "result": {
        "agentChainId": 1,
        "inflationAmount": 41095890410959,
        "agentAssetId": 1,
        "commissionMin": 20000000000000,
        "chainId": 1,
        "assetId": 1,
        "addressPrefix": "NULS",
        "symbol": "NULS"
    }
}
```
