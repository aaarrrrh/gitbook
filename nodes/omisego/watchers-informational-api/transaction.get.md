---
description: Gets a transaction with the given id.
---

# /transaction.get

### Example

```javascript
// Request
curl -H "Content-Type: application/json"  -d '{"id": "0x4a4411a8700da32d2a9c8b923f3cfc8063e5d9a513a7d761bfc6e789e0c9ef81"}' http://<your-app-id>.ankr.com/transaction.get

// Result
{
  "service_name": "watcher_info",
  "version": "1.0.0+abcdefa",
  "success": true,
  "data": {
    "txindex": 5113,
    "txtype": 1,
    "txhash": "0x5df13a6bf96dbcf6e66d8babd6b55bd40d64d4320c3b115364c6588fc18c2a21",
    "metadata": "0x00000000000000000000000000000000000000000000000000000048656c6c6f",
    "txbytes": "0x5df13a6bee20000...",
    "inserted_at": "2020-02-10T12:07:32Z",
    "updated_at": "2020-02-15T04:07:57Z",
    "block": {
      "timestamp": 1540365586,
      "hash": "0x0017372421f9a92bedb7163310918e623557ab5310befc14e67212b660c33bec",
      "eth_height": 97424,
      "blknum": 68290000,
      "inserted_at": "2020-02-10T12:07:32Z",
      "updated_at": "2020-02-15T04:07:57Z"
    },
    "inputs": [
      {
        "blknum": 1000,
        "txindex": 111,
        "oindex": 0,
        "otype": 1,
        "utxo_pos": 1000001110000,
        "owner": "0xb3256026863eb6ae5b06fa396ab09069784ea8ea",
        "currency": "0x0000000000000000000000000000000000000000",
        "amount": 10,
        "creating_txhash": "0x40d65df1c3b1156d813d6bf96d5bd3b5bcf6e6588fc18c2a2ba564c6a64d4320",
        "spending_txhash": "0x5df13a6bf96dbcf6e66d8babd6b55bd40d64d4320c3b115364c6588fc18c2a21",
        "inserted_at": "2020-02-10T12:07:32Z",
        "updated_at": "2020-02-15T04:07:57Z"
      }
    ],
    "outputs": [
      {
        "blknum": 68290000,
        "txindex": 5113,
        "oindex": 0,
        "otype": 1,
        "utxo_pos": 68290000051130000,
        "owner": "0xae8ae48796090ba693af60b5ea6be3686206523b",
        "currency": "0x0000000000000000000000000000000000000000",
        "amount": 2,
        "creating_txhash": "0x5df13a6bf96dbcf6e66d8babd6b55bd40d64d4320c3b115364c6588fc18c2a21",
        "spending_txhash": null,
        "inserted_at": "2020-02-10T12:07:32Z",
        "updated_at": "2020-02-15T04:07:57Z"
      },
      {
        "blknum": 68290000,
        "txindex": 5113,
        "oindex": 1,
        "otype": 1,
        "utxo_pos": 68290000051130000,
        "owner": "0xb3256026863eb6ae5b06fa396ab09069784ea8ea",
        "currency": "0x0000000000000000000000000000000000000000",
        "amount": 7,
        "creating_txhash": "0x5df13a6bf96dbcf6e66d8babd6b55bd40d64d4320c3b115364c6588fc18c2a21",
        "spending_txhash": null,
        "inserted_at": "2020-02-10T12:07:32Z",
        "updated_at": "2020-02-15T04:07:57Z"
      }
    ]
  }
}
```
