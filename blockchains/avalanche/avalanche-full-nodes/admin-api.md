# Admin API

This API can be used for measuring node health and debugging. Note that the Admin API is disabled by default for security reasons.

## Endpoint <a href="endpoint" id="endpoint"></a>

## API Methods <a href="api-methods" id="api-methods"></a>

### admin.alias <a href="adminalias" id="adminalias"></a>

Assign an API endpoint an alias, a different endpoint for the API. The original endpoint will still work. This change only affects this node; other nodes will not know about this alias.

* `endpoint` is the original endpoint of the API. `endpoint` should only include the part of the endpoint after `/ext/`.
* The API being aliased can now be called at `ext/alias`.
* `alias` can be at most 512 characters.

## **Example Call** <a href="example-call" id="example-call"></a>

```
//Requestcurl -X POST --data '{    "jsonrpc":"2.0",    "id"     :1,    "method" :"admin.alias",    "params": {        "alias":"myAlias",        "endpoint":"bc/X"    }}' -H 'content-type:application/json;' http://.ankr.com/ext/admin​//Response{    "jsonrpc":"2.0",    "id"     :1,    "result" :{        "success":true    }}
```
