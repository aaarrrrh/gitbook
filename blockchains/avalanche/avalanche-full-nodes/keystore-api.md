# Keystore API

Every node has a built-in keystore. Clients create users on the keystore, which act as identities to be used when interacting with blockchains. A keystore exists at the node level, so if you create a user on a node it exists _only_ on that node. However, users may be imported and exported using this API.

&#x20;**You should only create a keystore user on a node that you operate, as the node operator has access to your plaintext password.**

## Endpoint <a href="endpoint" id="endpoint"></a>

## **Example** Method <a href="methods" id="methods"></a>

### keystore.createUser <a href="keystorecreateuser" id="keystorecreateuser"></a>

Create a new user with the specified username and password.

## **Example Call** <a href="example-call" id="example-call"></a>

```javascript
//Request
curl -X POST --data '{
    "jsonrpc":"2.0",
    "id":1,
    "method" :"keystore.createUser",    
    "params" : {        
        "username":"bob",        
        "password":"creme fraiche"    
        },
}' -H 'content-type:application/json;' http:///<your-node-id>.ankr.com/ext/keystore​

//Response
{    
    "jsonrpc":"2.0",    
    "id":1,    
    "result" :{        
        "success":true    }
        }
```

​
