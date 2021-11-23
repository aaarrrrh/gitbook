# P-Chain API

This API allows clients to interact with the P-Chain (Platform Chain), which maintains Avalanche’s validator set and handles blockchain creation.

## Endpoint <a href="endpoint" id="endpoint"></a>

## Methods <a href="methods" id="methods"></a>

### platform.createAddress <a href="platformcreateaddress" id="platformcreateaddress"></a>

## **Example Call** <a href="example-call" id="example-call"></a>

```javascript
//Request
curl -X POST --data '{
    "jsonrpc": "2.0",
    "method": "platform.createAddress",    
    "params": {        
        "username":"myUsername",        
        "password":"myPassword"    
    },    
    "id": 1
}' -H 'content-type:application/json;' http://<your-node-id>.ankr.com/ext/bc/P​

//Response​
{
    "jsonrpc": "2.0",
    "result": {
        "address": "P-avax12lqey27sfujqq6mc5a3jr5av56cjsu8hg2d3hx"    
    },    
    "id": 1
}
```

Last updated 11 months ago
