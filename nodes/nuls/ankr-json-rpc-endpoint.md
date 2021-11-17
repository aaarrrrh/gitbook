---
description: >-
  This is a guide on how to obtain the Nuls Ankr End-Point and execute a simple
  request.
---

# Ankr JSON-RPC Endpoint

### Obtain Ankr End-point <a href="obtain-ankr-end-point" id="obtain-ankr-end-point"></a>

After successfully deploying an Ankr Full node, the End-point can be found on the application details, on the left side of the screen:

![](https://gblobscdn.gitbook.com/assets%2F-MF6NYa65t3TUvQZ0zRX%2F-MGbfqNPPstsrGONN5jZ%2F-MGbspZnFYIEb7GqCuoA%2FNULS\_gitbook.jpg?alt=media\&token=8c75564e-564b-4391-aa2a-62a9fee2b224)

The RPC endpoint will have the following format:

**http://\<your-app-id>.ankr.com**

Example (as shown in the image above):

**https://app.ankr.com/apps/details/app-17f65f75-b04e-4eb7-b133-703394258d86**

### Simple Json-RPC Request <a href="simple-json-rpc-request" id="simple-json-rpc-request"></a>

```javascript
// Request:
curl -s -X POST -H 'Content-Type: application/json' --data '{"jsonrpc":"2.0","method":"getInfo","params":[1], "id":1234}' http://<your-app-id>.ankr.com

// Result:

{
  "jsonrpc": "2.0",
  "id": "1234",
  "result": {
    "networkHeight": 41493,
    "isRunSmartContract": true,
    "chainId": 1,
    "agentAsset": {
      "symbol": "NULS",
      "chainId": 1,
      "assetId": 1,
      "decimals": 8
    },
    "localHeight": 41493,
    "magicNumber": 20191222,
    "defaultAsset": {
      "symbol": "NULS",
      "chainId": 1,
      "assetId": 1,
      "decimals": 8
    },
    "isRunCrossChain": true
  }
}

```

In the next sections, we will describe some of the RPC requests. Most of them can be found in the official documentation for [NULS API Service](https://docs.nuls.io/Docs/i\_nuls-api\_JSONRPC.html) or [Public service API](https://docs.nuls.io/Docs/i\_public\_service.html), both of which we currently support.&#x20;
