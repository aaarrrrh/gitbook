# Develop on Fantom

Ankr allows users to create their own full Fantom APIs with a variety of options for request call limits, archived data, and more. Ankr’s novel cluster technology allows APIs to draw from multiple nodes, offering a more reliable experience for our users.

### Get started on Fantom

1. Login or set up an account on app.ankr.com
2. [**Create API**](https://app.ankr.com/api)****

### ** Network Types**

* Mainnet
* Testnet

### **Nodes**

* Fantom Full

### Explorers

Official Fantom Explorers: [https://explorer.fantom.network](https://explorer.fantom.network) and [https://ftmscan.com](https://ftmscan.com)

### GraphQL API Methods

GraphQL docs [https://docs.fantom.foundation/api/schema-structure](https://docs.fantom.foundation/api/schema-structure)

REST API docs: [https://www.covalenthq.com/docs/api/#overview](https://www.covalenthq.com/docs/api/#overview)

### JSON RPC Methods

Fantom uses standard JSON RPC methods. \
View [Supported JSON RPC Methods](../../blockchain-apis/making-requests/supported-json-rpc-methods.md).

### Example Calls

#### API (HTTPS) Endpoint

{% tabs %}
{% tab title="Go" %}
```go
package main

import (
    "context"
    "fmt"
    "github.com/ethereum/go-ethereum/ethclient"
)


func main() {
    const url_auth = "https://username:password@apis.ankr.com/xxxxx/xxxxx/fantom/full/main"    // authentication
    const url_token = "https://apis.ankr.com/xxxxx/xxxxx/fantom/full/main"                     // token
    
    rpcClient,err := ethclient.Dial("choose url_auth or url_token by your created type")
    
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


const url_auth = 'https://username:password@apis.ankr.com/xxxxx/xxxxx/fantom/full/main'    // authentication
const url_token = 'https://apis.ankr.com/xxxxx/xxxxx/fantom/full/main'                     // token

const web3 = new Web3(new Web3.providers.HttpProvider('choose url_auth or url_token by your created type'));

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
    url_auth = 'https://username:password@apis.ankr.com/xxxxx/xxxxx/fantom/full/main'  # authentication
    url_token = 'https://apis.ankr.com/xxxxx/xxxxx/fantom/full/main'                   # token
    
    web3 = Web3(HTTPProvider('choose url_auth or url_token by your created type'))
    print(web3.eth.block_number)
```
{% endtab %}

{% tab title="Curl" %}
```bash
# authentication
$ curl -H "Content-Type: application/json" -u "username:password" -d '{"jsonrpc":"2.0","method":"eth_blockNumber","params":[],"id":1}' https://apis.ankr.com/xxxxx/xxxxx/fantom/full/main
$ curl -H "Content-Type: application/json" -d '{"jsonrpc":"2.0","method":"eth_blockNumber","params":[],"id":1}' https://username:password@apis.ankr.com/xxxxx/xxxxx/fantom/full/main

# token
$ curl -H "Content-Type: application/json" -d '{"jsonrpc":"2.0","method":"eth_blockNumber","params":[],"id":1}' https://apis.ankr.com/xxxxx/xxxxx/fantom/full/main
```
{% endtab %}
{% endtabs %}

#### Websocket (WSS) Endpoint&#x20;

{% tabs %}
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
    const url_auth = "wss://username:password@apis.ankr.com/wss/xxxxx/xxxxx/fantom/full/main" // authentication
    const url_token = "wss://apis.ankr.com/wss/xxxxx/xxxxx/fantom/full/main"                  // token
    
    client, err := ethclient.Dial(`choose url_auth or url_token by your created type`)
    
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

{% tab title="Javascript (ethers)" %}
```javascript
const ethers = require("ethers");

const url_auth = 'wss://username:password@apis.ankr.com/wss/xxxxx/xxxxx/fantom/full/main'    // authentication
const url_token = 'wss://d@apis.ankr.com/wss/xxxxx/xxxxx/fantom/full/main'                   // token

const init = function () {

    const wsProvider = new ethers.providers.WebSocketProvider('choose url_auth or url_token by your created type');

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

{% tab title="Javascript (ws)" %}
```javascript
const WebSocket = require('ws');

const url_auth = 'wss://username:password@apis.ankr.com/wss/xxxxx/xxxxx/fantom/full/main'    // authentication
const url_token = 'wss://d@apis.ankr.com/wss/xxxxx/xxxxx/fantom/full/main'                   // token

const request = '{"id": 1, "method": "eth_subscribe", "params": ["newPendingTransactions"]}';  

const ws = new WebSocket('choose url_auth or url_token by your created type');

ws.on('open', function open() {
    ws.send(request);
});
ws.on('message', function incoming(data) {
    res = JSON.parse(data)
    if (res.result != null) {
        console.log(`Subscription: ${res.result}`);
    } else if (res.params != null && res.params["result"] != null) {
        console.log(`New pending transaction: ${res.params["result"]}`);
    } else {
        console.log(`Unexpected: ${data}`);
    }
});
```
{% endtab %}

{% tab title="Curl" %}
```bash
# authentication
$ wscat -c wss://username:password@apis.ankr.com/wss/xxxxx/xxxxx/fantom/full/main

# token
$ wscat -c wss://apis.ankr.com/wss/xxxxx/xxxxx/fantom/full/main

wait connected...

# subscribe
> {"jsonrpc":"2.0","method":"eth_subscribe","params":["newHeads"],"id":1}

# unsubscribe
> {"jsonrpc":"2.0","method":"eth_unsubscribe","params":["0xxxxxxxxxxxxxxx"],"id":1}
```
{% endtab %}
{% endtabs %}
