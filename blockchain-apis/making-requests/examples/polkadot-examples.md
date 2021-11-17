# Polkadot Examples

The following simple usage examples are to support you to get started.

For more details, please refer to the [official documentation](https://polkadot.js.org/docs/)

### Simple Example <a href="simple-example" id="simple-example"></a>

#### API HTTPS Endpoint <a href="https-endpoint" id="https-endpoint"></a>

{% tabs %}
{% tab title="Go" %}
```go
package main

import (
    "fmt"
    "github.com/centrifuge/go-substrate-rpc-client/client"
    "github.com/centrifuge/go-substrate-rpc-client/rpc/author"
    "github.com/centrifuge/go-substrate-rpc-client/rpc/chain"
    "github.com/centrifuge/go-substrate-rpc-client/rpc/state"
    "github.com/centrifuge/go-substrate-rpc-client/rpc/system"
)


func main() {
    const url_basic = "https://username:password@apis.ankr.com/xxxxx/xxxxx/polkadot/full/main"    // basic authentication
    const url_token = "https://apis.ankr.com/xxxxx/xxxxx/polkadot/full/main"                      // token
    
    cl,err := client.Connect("choose url_basic or url_token by your created type")
    
    if err != nil {
        panic(err)
    }

    newRPC, err := NewRPC(cl)
    if err != nil {
        panic(err)
    }

    hash, err := newRPC.Chain.GetFinalizedHead()
    if err != nil {
        panic(err)
    }

    fmt.Println(hash.Hex())

}

type RPC struct {
    Author *author.Author
    Chain *chain.Chain
    State *state.State
    System *system.System
    Client *client.Client
}

func NewRPC(cl client.Client) (*RPC, error) {
    st := state.NewState(cl)
    return &RPC{
        Author: author.NewAuthor(cl),
        Chain: chain.NewChain(cl),
        State: st,
        System: system.NewSystem(cl),
        client: cl,
    }, nil
}
```
{% endtab %}

{% tab title="Javascript" %}
```javascript
const { HttpProvider } = require('@polkadot/api');

const url_basic = "https://username:password@apis.ankr.com/xxxxx/xxxxx/polkadot/full/main"    // basic authentication
const url_token = "https://apis.ankr.com/xxxxx/xxxxx/polkadot/full/main"                      // token

const provider = new HttpProvider('choose url_basic or url_token by your created type')

provider.send("chain_getFinalizedHead", []).then(hash => {
    console.log(`the finalized block hash is ${hash}`)
})
provider.send("chain_getBlockHash", []).then(hash => {
    console.log(`the block hash is ${hash}`)
    provider.send("chain_getBlock", [hash]).then(value => {
        console.log(`the block number is ${value.block.header.number}`)
        console.log(`the block detail is ${JSON.stringify(value)}`)
    })
})
```
{% endtab %}

{% tab title="Python" %}
```python
import json

import requests


def create_req_body(r_id, method, params):
    data = {
        "jsonrpc": "2.0",
        "id": r_id,
        "method": method,
        "params": params
    }
    return json.dumps(data)


class TestDot:
    def test_dot_basic_auth(self):
        """
        basic auth example
        """
        headers = {"Content-Type": "application/json"}
        url = 'https://apis.ankr.com/xxxxx/xxxxx/polkadot/full/main'
        auth = ("your username", "your password")

        req_finalized_head = create_req_body(1, "chain_getFinalizedHead", [])
        r = requests.post(url=url, headers=headers, auth=auth, data=req_finalized_head)
        res_hash = r.json()['result']
        print('the finalized block hash is ' + res_hash)

        req_block = create_req_body(2, "chain_getBlock", [res_hash])
        r = requests.post(url=url, headers=headers, auth=auth, data=req_block)
        block_number = r.json()['result']['block']['header']['number']
        print('the block number is ' + block_number)
        print('the block detail is ' + r.text)

    def test_dot_token(self):
        """
        token example
        """
        headers = {"Content-Type": "application/json"}
        url = 'https://apis.ankr.com/xxxxx/xxxxx/polkadot/full/main'

        req_finalized_head = create_req_body(1, "chain_getFinalizedHead", [])
        r = requests.post(url=url, headers=headers, data=req_finalized_head)
        res_hash = r.json()['result']
        print('the finalized block hash is ' + res_hash)

        req_block = create_req_body(2, "chain_getBlock", [res_hash])
        r = requests.post(url=url, headers=headers, data=req_block)
        block_number = r.json()['result']['block']['header']['number']
        print('the block number is ' + block_number)
        print('the block detail is ' + r.text)
```
{% endtab %}

{% tab title="Curl" %}
```bash
# basic authentication
$ curl -H "Content-Type: application/json" -u "username:password" https://apis.ankr.com/xxxxx/xxxxx/polkadot/full/main -d '{"jsonrpc":"2.0","method":"chain_getBlock","params":[],"id":1}'

# basic authentication way two
$ curl -H "Content-Type: application/json" https://username:password@apis.ankr.com/xxxxx/xxxxx/polkadot/full/main -d '{"jsonrpc":"2.0","method":"chain_getBlock","params":[],"id":1}'

# token
$ curl -H "Content-Type: application/json" https://apis.ankr.com/xxxxx/xxxxx/polkadot/full/main -d '{"jsonrpc":"2.0","method":"chain_getBlock","params":[],"id":1}'
```
{% endtab %}
{% endtabs %}

#### Websocket (WSS) endpoint <a href="wss-endpoint" id="wss-endpoint"></a>

{% tabs %}
{% tab title="Curl (wscat)" %}
```bash
# basic authentication
$ wscat -c wss://username:password@apis.ankr.com/wss/xxxxx/xxxxx/polkadot/full/main

# token
$ wscat -c wss://apis.ankr.com/wss/xxxxx/xxxxx/polkadot/full/main

wait connected...

# subscribe
> {"jsonrpc": "2.0", "id": 1, "method": "chain_subscribeNewHeads", "params": []}

# unsubscribe
> {"jsonrpc": "2.0", "id": 2, "method": "chain_unsubscribeNewHeads", "params": ["The result value returned after successful subscription"]}
```
{% endtab %}

{% tab title="Go" %}
```go
package main

import (
    "fmt"
    "github.com/centrifuge/go-substrate-rpc-client/client"
    "github.com/centrifuge/go-substrate-rpc-client/rpc/author"
    "github.com/centrifuge/go-substrate-rpc-client/rpc/chain"
    "github.com/centrifuge/go-substrate-rpc-client/rpc/state"
    "github.com/centrifuge/go-substrate-rpc-client/rpc/system"
    "time"
)


func main() {
    const url_basic = "wss://username:password@apis.ankr.com/wss/xxxxx/xxxxx/polkadot/full/main"    // basic authentication
    const url_token = "wss://apis.ankr.com/wss/xxxxx/xxxxx/polkadot/full/main"                      // token
    
    cl,err := client.Connect("choose url_basic or url_token by your created type")
    
    if err != nil {
        panic(err)
    }

    newRPC, err := NewWebsocket(cl)
    if err != nil {
        panic(err)
    }

    sub, err := newRPC.Chain.SubscribeNewHeads()
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
        for c := range sub.Chan {
            fmt.Println(c.Number)
        }
    }()

    <-sub.Err()

}

type Websocket struct {
    Author *author.Author
    Chain *chain.Chain
    State *state.State
    System *system.System
    Client *client.Client
}

func NewWebsocket(cl client.Client) (*Websocket, error) {
    st := state.NewState(cl)
    return &Websocket{
        Author: author.NewAuthor(cl),
        Chain: chain.NewChain(cl),
        State: st,
        System: system.NewSystem(cl),
        client: cl,
    }, nil
}
```
{% endtab %}

{% tab title="Javascript" %}
```javascript
const {ApiPromise, WsProvider} = require('@polkadot/api');

async function main() {

    const url_token = "wss://apis.ankr.com/wss/xxxxx/xxxxx/polkadot/full/main"            // Only the token authentication method is supported here
    const provider = new WsProvider(url);

    const api = await ApiPromise.create({ provider });

    const [chain, nodeName, nodeVersion] = await Promise.all([
        api.rpc.system.chain(),
        api.rpc.system.name(),
        api.rpc.system.version()
    ]);

    console.log(`You are connected to chain ${chain} using ${nodeName} v${nodeVersion}`);

    let count = 0;

    await api.rpc.chain.subscribeNewHeads((header) => {
        console.log(`Chain is at block: #${header.number}`);

        if (++count === 5) {
            process.exit(0);
        }
    });
}

main().catch(console.error);
```
{% endtab %}

{% tab title="Javascript (ws)" %}
```javascript
const WebSocket = require('ws');

const url_basic = 'wss://username:password@apis.ankr.com/wss/xxxxx/xxxxx/polkadot/full/main'    // basic authentication
const url_token = 'wss://d@apis.ankr.com/wss/xxxxx/xxxxx/polkadot/full/main'                    // token

const request = '{"jsonrpc": "2.0", "id": 1, "method": "chain_subscribeNewHeads"}';

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
    req_json = create_req_body(1, "chain_subscribeNewHeads", [])
    async with websockets.connect(url) as wss:
        await wss.send(req_json)
        subscription_response = await wss.recv()
        print(subscription_response)
        sub_hex = json.loads(subscription_response)['result']
        req_json = create_req_body(2, "chain_unsubscribeNewHeads", [sub_hex])

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
        url_basic = 'wss://username:password@apis.ankr.com/wss/xxxxx/xxxxx/polkadot/full/main'  # basic authentication
        url_token = 'wss://apis.ankr.com/wss/xxxxx/xxxxx/polkadot/full/main'                    # token
        asyncio.get_event_loop().run_until_complete(do_wss('choose url_basic or url_token by your created type'))
```
{% endtab %}
{% endtabs %}
