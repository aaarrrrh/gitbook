# getInfo

```
// Requestcurl -s -X POST -H 'Content-Type: application/json' --data '{"jsonrpc":"2.0","method":"getInfo","params":[1], "id":1234}' http://.ankr.com​// Result{  "jsonrpc": "2.0",  "id": "1234",  "result": {    "networkHeight": 41493,    "isRunSmartContract": true,    "chainId": 1,    "agentAsset": {      "symbol": "NULS",      "chainId": 1,      "assetId": 1,      "decimals": 8    },    "localHeight": 41493,    "magicNumber": 20191222,    "defaultAsset": {      "symbol": "NULS",      "chainId": 1,      "assetId": 1,      "decimals": 8    },    "isRunCrossChain": true  }}
```
