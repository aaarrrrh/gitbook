# Ethereum Based Examples

{% hint style="info" %}
**NOTE: The following examples are based on calls to Binance Smart Chain and are for reference only. **
{% endhint %}

### **API Endpoint Examples**

{% tabs %}
{% tab title="Curl" %}
```bash
# basic authentication
$ curl -H "Content-Type: application/json" -u "username:password" https://apis.ankr.com/xxxxx/xxxxx/binance/full/main -d '{"jsonrpc":"2.0","method":"eth_blockNumber","params":[],"id":1}'

# basic authentication way two
$ curl -H "Content-Type: application/json" https://username:password@apis.ankr.com/xxxxx/xxxxx/binance/full/main -d '{"jsonrpc":"2.0","method":"chain_geeth_blockNumbertBlock","params":[],"id":1}'


# token
$ curl -H "Content-Type: application/json" -d '{"jsonrpc":"2.0","method":"eth_blockNumber","params":[],"id":1}' https://apis.ankr.com/xxxxx/xxxxx/binance/full/main
```
{% endtab %}

{% tab title="Go" %}
```go
package main

import (
    "context"
    "fmt"
    "github.com/ethereum/go-ethereum/ethclient"
)


func main() {
    const url_basic = "https://username:password@apis.ankr.com/xxxxx/xxxxx/binance/full/main"    // basic authentication
    const url_token = "https://apis.ankr.com/xxxxx/xxxxx/binance/full/main"                      // token
    
    rpcClient,err := ethclient.Dial("choose url_basic or url_token by your created type")
    
    if err != nil {
        panic(err)
    }
    
    blockNumber, err := rpcClient.BlockNumber(context.Background())
    
    if err != nil {
        panic(err)
    }
    
    fmt.Println(blockNumber)
}
```
{% endtab %}

{% tab title="Javascript" %}
```javascript
const Web3 = require('web3');


let url_basic = 'https://username:password@apis.ankr.com/xxxxx/xxxxx/binance/full/main'  // basic authentication
let url_token = 'https://apis.ankr.com/xxxxx/xxxxx/binance/full/main'                    // token

const web3 = new Web3(new Web3.providers.HttpProvider('choose url_basic or url_token by your created type'));

web3.eth.getBlockNumber((error, blockNumber) => {
    if(!error){
        console.log(blockNumber);
    }else{
        console.log(error);
    }
})

```
{% endtab %}

{% tab title="Python" %}
```python
from web3 import Web3


def test_block_number(self):
    url_basic = 'https://username:password@apis.ankr.com/xxxxx/xxxxx/binance/full/main'  # basic authentication
    url_token = 'https://apis.ankr.com/xxxxx/xxxxx/binance/full/main'                    # token
    
    web3 = Web3(HTTPProvider('choose url_basic or url_token by your created type'))
    print(web3.eth.block_number)
```
{% endtab %}
{% endtabs %}

The easiest way to test out your WebSocket endpoint is to install a command line tool such as [`wscat`](https://github.com/websockets/wscat)

Use `wscat` to send Curl requests as in the Curl example below

### Websocket Endpoint Examples

{% tabs %}
{% tab title="Curl (wscat)" %}
```bash
# basic authentication
$ wscat -c wss://username:password@apis.ankr.com/wss/xxxxx/xxxxx/binance/full/main

# token
$ wscat -c wss://apis.ankr.com/wss/xxxxx/xxxxx/binance/full/main

wait connected...

# subscribe
> {"jsonrpc": "2.0", "id": 1, "method": "eth_subscribe", "params": ["newHeads"]}

# unsubscribe
> {"jsonrpc": "2.0", "id": 2, "method": "eth_unsubscribe", "params": ["The result value returned after successful subscription"]}
```
{% endtab %}

{% tab title="Go" %}
```go
package main

import (
    "context"
    "fmt"
    "github.com/ethereum/go-ethereum/core/types"
    "github.com/ethereum/go-ethereum/ethclient"
    "time"
)


func main() {
    const url_basic = "wss://username:password@apis.ankr.com/wss/xxxxx/xxxxx/binance/full/main" // basic authentication
    const url_token = "wss://apis.ankr.com/wss/xxxxx/xxxxx/binance/full/main"                   // token
    
    client, err := ethclient.Dial(`choose url_basic or url_token by your created type`)
    
    if err != nil {
        panic(err)
    }
    
    ch := make(chan *types.Header, 1024)
    sub, err := client.SubscribeNewHead(context.Background(), ch)
    
    if err != nil {
        panic(err)
    }
    
    fmt.Println("---subscribe-----")

    go func() {
        time.Sleep(10 * time.Second)
        fmt.Println("---unsubscribe-----")
        sub.Unsubscribe()
    }()

    go func() {
        for c := range ch {
            fmt.Println(c.Number)
        }
    }()

    <-sub.Err()

}
```
{% endtab %}

{% tab title="Javascript (Ethers)" %}
```javascript
const ethers = require("ethers");

const url_basic = 'wss://username:password@apis.ankr.com/wss/xxxxx/xxxxx/binance/full/main'    // basic authentication
const url_token = 'wss://apis.ankr.com/wss/xxxxx/xxxxx/binance/full/main'                      // token

const init = function () {

    const wsProvider = new ethers.providers.WebSocketProvider('choose url_basic or url_token by your created type');

    wsProvider.on("pending", (tx) => {
        console.log("tx", tx)
        setTimeout(function () {
            wsProvider.destroy()
        }, 1000);

    });

};

init();
```
{% endtab %}

{% tab title="Javascript (WS)" %}
```javascript
const WebSocket = require('ws');

const url_basic = 'wss://username:password@apis.ankr.com/wss/xxxxx/xxxxx/binance/full/main'    // basic authentication
const url_token = 'wss://d@apis.ankr.com/wss/xxxxx/xxxxx/binance/full/main'                    // token

const request = '{"jsonrpc": "2.0", "id": 1, "method": "eth_subscribe", "params": ["newPendingTransactions"]}';  

const ws = new WebSocket('choose url_basic or url_token by your created type');

ws.on('open', function open() {
    ws.send(request);
});

let count = 0;

ws.on('message', function incoming(data) {
    const res = JSON.parse(data)
    console.log(JSON.stringify(res));
    if (++count === 5) {
        process.exit(0);
    }
});
```
{% endtab %}

{% tab title="Python" %}
```python
import asyncio
import json
import time

import websockets


def create_req_body(r_id, method, params):
    data = {
        "jsonrpc": "2.0",
        "id": r_id,
        "method": method,
        "params": params
    }
    return json.dumps(data)


async def do_wss(url):
    req_json = create_req_body(1, "eth_subscribe", ["newHeads"])
    async with websockets.connect(url) as wss:
        await wss.send(req_json)
        subscription_response = await wss.recv()
        print(subscription_response)
        subscribe_result = json.loads(subscription_response)['result']
        req_json = create_req_body(2, "eth_unsubscribe", [subscribe_result])

        start_time = int(time.time())
        end_time = start_time + 5
        while end_time > int(time.time()):
            recv_data = await wss.recv()
            print(recv_data)
            print('\n')
        await wss.send(req_json)
        unsubscription_response = await wss.recv()
        print(unsubscription_response)


class TestWSS:

    def test_wss(self):
        url_basic = 'wss://username:password@apis.ankr.com/wss/xxxxx/xxxxx/binance/full/main'  # basic authentication
        url_token = 'wss://apis.ankr.com/wss/xxxxx/xxxxx/binance/full/main'                    # token
        asyncio.get_event_loop().run_until_complete(do_wss('choose url_basic or url_token by your created type'))
```
{% endtab %}

{% tab title="" %}
```
```
{% endtab %}
{% endtabs %}



