---
description: How to obtain the Ankr End-Point and execute a simple request.
---

# Ankr Json-RPC Endpoint

### Obtain Ankr Endpoint <a href="#obtain-ankr-endpoint" id="obtain-ankr-endpoint"></a>

After successfully deploying an Ankr Full node, the End-point can be found on the application details, on the left side of the screen:

![](https://gblobscdn.gitbook.com/assets%2F-MF6NYa65t3TUvQZ0zRX%2F-MJ6xQ3VGp7S6yd5qUet%2F-MJ6ypO880HcrNABT4Ud%2FOmiseGo%20gitbook.jpg?alt=media\&token=13bbcb1a-5e7f-46f8-9836-713598badcfd)

The RPC endpoint will have the following format:

**http://\<your-app-id>.ankr.com**

Example (as shown in the image above):

app-36563e5b-a1f5-4e44-8b47-796734c5bf04.cls-a91a7dbc-1a23-42f6-a66f-876094349f03.ankr.com

### Simple **JSON**-RPC Request <a href="#simple-json-rpc-request" id="simple-json-rpc-request"></a>

```
// Request
curl -X POST "http://<your-app-id>.ankr.com/status.get" -H "accept: application/json"​// Result{  "data": {    "byzantine_events": [      {        "details": {          "available_inputs": [            {              "address": "0x0dc8e240d90f3b0d511b6447543b28ea2471401a",              "index": 0            }          ],          "available_outputs": [            {              "address": "0x0dc8e240d90f3b0d511b6447543b28ea2471401a",              "index": 1            }          ],          "name": "piggyback_available",          "txbytes": "0xf8b101e1a00000000000000000000000000000000000000000000000000000bc44dfe31800f86af401f2948b63bb2b829813ece5c2f378d47b2862be271c6c9400000000000000000000000000000000000000008711c37937e08000f401f2940dc8e240d90f3b0d511b6447543b28ea2471401a9400000000000000000000000000000000000000008711a8304c88a00080a00000000000000000000000000000000000000000000000000000000000000000"        },        "event": "piggyback_available"      }    ],    "contract_addr": {      "erc20_vault": "0x18e15c2cdc003b845b056f8d6b6a91ab33d3f182",      "eth_vault": "0x895cc6f20d386f5c0deae08b08ccfec9f821e7d9",      "payment_exit_game": "0x08c569c5774110eb84a80b292e6d6f039e18915a",      "plasma_framework": "0x96d5d8bc539694e5fa1ec0dab0e6327ca9e680f9"    },    "eth_syncing": false,    "in_flight_exits": [      {        "eth_height": 7907328,        "piggybacked_inputs": [],        "piggybacked_outputs": [          0        ],        "txbytes": "0xf8b101e1a00000000000000000000000000000000000000000000000000000bc44dfe31800f86af401f2948b63bb2b829813ece5c2f378d47b2862be271c6c9400000000000000000000000000000000000000008711c37937e08000f401f2940dc8e240d90f3b0d511b6447543b28ea2471401a9400000000000000000000000000000000000000008711a8304c88a00080a00000000000000000000000000000000000000000000000000000000000000000",        "txhash": "0xb4e8d1b7a04bf49753a0bf757e4f2b9f3c06b5ef628f99e30892a209da6455ec"      }    ],    "last_mined_child_block_number": 4089000,    "last_mined_child_block_timestamp": 1602153779,    "last_seen_eth_block_number": 8836677,    "last_seen_eth_block_timestamp": 1602156853,    "last_validated_child_block_number": 4089000,    "last_validated_child_block_timestamp": 1602153779,    "services_synced_heights": [      {        "height": 8836673,        "service": "block_getter"      },      {        "height": 8836661,        "service": "challenges_responds_processor"      },      {        "height": 8836663,        "service": "competitor_processor"      },      {        "height": 8836663,        "service": "depositor"      },      {        "height": 8836663,        "service": "exit_challenger"      },      {        "height": 8836663,        "service": "exit_finalizer"      },      {        "height": 8836663,        "service": "exit_processor"      },      {        "height": 8836661,        "service": "ife_exit_finalizer"      },      {        "height": 8836663,        "service": "in_flight_exit_processor"      },      {        "height": 8836659,        "service": "piggyback_challenges_processor"      },      {        "height": 8836661,        "service": "piggyback_processor"      },      {        "height": 8836675,        "service": "root_chain_height"      }    ]  },​
```

### API Documentation​ <a href="#apis-official-documentation" id="apis-official-documentation"></a>

In the next sections, we will describe some of the RPC requests, most of them can be found in the [Official Documentation.](https://docs.omg.network)

[API Docs](https://docs.omg.network/resources/api-references)
