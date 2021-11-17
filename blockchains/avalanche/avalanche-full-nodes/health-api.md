# Health API

Get health check on this node.

```
//Requestcurl -X POST --data '{    "jsonrpc":"2.0",    "id"     :1,    "method" :"health.getLiveness"}' -H 'content-type:application/json;' http://.ankr.com/ext/health​//Response{    "jsonrpc": "2.0",    "result": {        "checks": {            "chains.default.bootstrapped": {                "timestamp": "2020-09-14T16:37:18.94094791Z",                "duration": 17731,                "contiguousFailures": 0,                "timeOfFirstFailure": null            },            "network.validators.heartbeat": {                "message": {                    "heartbeat": 1600101438                },                "timestamp": "2020-09-14T16:37:18.939024201Z",                "duration": 8527,                "contiguousFailures": 0,                "timeOfFirstFailure": null            }        },        "healthy": true    },    "id": 1}
```
