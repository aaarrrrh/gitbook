# Info API

This API can be used to access basic information about the node.

## Endpoint <a href="endpoint" id="endpoint"></a>

## API Methods <a href="api-methods" id="api-methods"></a>

### info.getNodeVersion <a href="infogetnodeversion" id="infogetnodeversion"></a>

Get the version of this node.

## **Example Call** <a href="example-call" id="example-call"></a>

```javascript
//Request
curl -X POST --data '{
    "jsonrpc":"2.0",    
    "id" :1,    
    "method" :"info.getNodeVersion"
    }' -H 'content-type:application/json;' http:///<your-node-id>.ankr.com/ext/info
    
​//Reponse
{    
    "jsonrpc": "2.0",    
    "result": {        
        "version": "avalanche/0.7.0"    
        },    
    "id": 1
    }
```
