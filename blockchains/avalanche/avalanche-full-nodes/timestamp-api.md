# Timestamp API

The Timestamp Chain is a timestamp server. Each block contains a 32 byte payload and the timestamp when the block was created.

The [genesis data](https://docs.avax.network/v1.0/en/api/platform/#platfrombuildgenesis) for a new instance of the Timestamp Chain is the genesis block’s 32 byte payload.

## Endpoint <a href="endpoint" id="endpoint"></a>

## Methods <a href="methods" id="methods"></a>

### timestamp.getBlock <a href="timestampgetblock" id="timestampgetblock"></a>

Get a block by its ID. If no ID is provided, get the latest block.

* `id` is the ID of the block being retrieved. If omitted from arguments, gets the latest block.
* `data` is the base 58 (with checksum) representation of the block’s 32 byte payload.
* `timestamp` is the Unix when this block was created.
* `parentID` is the block’s parent.

## **Example Call** <a href="example-call" id="example-call"></a>

```
//Requestcurl -X POST --data '{    "jsonrpc": "2.0",    "method": "timestamp.getBlock",    "params":{        "id":"xqQV1jDnCXDxhfnNT7tDBcXeoH2jC3Hh7Pyv4GXE1z1hfup5K"    },    "id": 1}' -H 'content-type:application/json;' http://.ankr.com/ext/bc/timestamp​//Response{    "jsonrpc": "2.0",    "result": {        "timestamp": "1581717416",        "data": "11111111111111111111111111111111LpoYY",        "id": "xqQV1jDnCXDxhfnNT7tDBcXeoH2jC3Hh7Pyv4GXE1z1hfup5K",        "parentID": "22XLgiM5dfCwTY9iZnVk8ZPuPe3aSrdVr5Dfrbxd3ejpJd7oef"    },    "id": 1}
```
