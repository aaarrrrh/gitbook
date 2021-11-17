# AVM (X-Chain) API

## Endpoints <a href="endpoints" id="endpoints"></a>

`/ext/bc/X` to interact with the X-Chain.

`/ext/bc/blockchainID` to interact with other AVM instances, where `blockchainID` is the ID of a blockchain running the AVM.

## Example Method <a href="example-method" id="example-method"></a>

### avm.createAddress <a href="avmcreateaddress" id="avmcreateaddress"></a>

Create a new address controlled by the given user.

## Example Call <a href="example-call" id="example-call"></a>

```javascript
//Request
curl -X POST --data '{
    "jsonrpc": "2.0",
    "method": "avm.createAddress",
    "params": {
        "username":"User",
        "password":"PassPass"
    },
    "id": 1
}' -H 'content-type:application/json;' http://<your-node-id>.ankr.com/ext/bc/X

//Response
{
    "jsonrpc": "2.0",
    "result": {
        "address": "X-avax12c6n252g5v3w6a6v69f0mnnzwr77jxzr3q3u7d"
    },
    "id": 1
}
```
