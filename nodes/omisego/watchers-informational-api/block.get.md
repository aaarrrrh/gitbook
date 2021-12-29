# /block.get

### Example

```
// Request
curl -H "Content-Type: application/json" -d '{"blknum":3721000}' http://<your-app-id>.ankr.com/block.get

// Result
{
  "service_name": "watcher_info",
  "version": "1.0.0+abcdefa",
  "success": true,
  "data": {
    "timestamp": 1540365586,
    "hash": "0x0017372421f9a92bedb7163310918e623557ab5310befc14e67212b660c33bec",
    "eth_height": 97424,
    "blknum": 68290000,
    "tx_count": 2,
    "inserted_at": "2020-02-10T12:07:32Z",
    "updated_at": "2020-02-15T04:07:57Z"
  }
}
```
