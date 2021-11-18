# How to run an Avalanche Node

## Introduction

This guide will walk you through setting up and launching an Avalanche Node. We will be using the [pre-built binary](how-to-run-an-avalanche-node.md#introduction) from Avalanche as this is the easiest way to run an Avalanche node. &#x20;

### **Set up Flow**

**00 Prerequisites** - Describes recommended and minimum hardware requirements.

**01 Install binary **

**02 Run Avalanche Node**

**03 Make requests**

## **00 Prerequisites**

**Minimum hardware requirements**

* CPU: 2+ cores
* RAM: 16 GB
* Storage: 200 GB
* OS: Ubuntu 18.04/20.04 or MacOS >= Catalina

## 01 Install binary

1. Check out the [ava-labs releases ](https://github.com/ava-labs/avalanchego/releases)page and select the latest release for your OS under **Assets**

![](<../../../.gitbook/assets/Screenshot 2021-11-16 at 14.22.16.png>)

2\. For this guide, we're going to download the latest zip file for **macos**.&#x20;

{% hint style="warning" %}
**Be Aware**

Your browser may not like this download and you may need to explicitly authorize it.&#x20;
{% endhint %}

3\. Unzip the downloaded file and we have a **Build** folder

![](<../../../.gitbook/assets/Screenshot 2021-11-16 at 14.30.47.png>)

## 02 Run an Avalanche Node

&#x20;1\. From the **Build folder** you just unpacked, start a node, by clicking '**avalanchego**' .

* You start to see logs as it initializes a suite of JSON RPCs.&#x20;
* You can see below AvalancheGo initializing a local **KeyStore**, **metrics**, **IPC**, and **Admin** APIs for interacting with the node itself.

![](<../../../.gitbook/assets/Screenshot 2021-11-16 at 14.41.27.png>)

2\. The node starts to catch up with the rest of the network by '**bootstrapping**'.&#x20;

* You can see this process in the screenshot below&#x20;

![](<../../../.gitbook/assets/Screenshot 2021-11-16 at 14.51.20.png>)

3\. Open a separate Terminal window to check if the chain has finished bootstrapping.

* Run the method `"info.isBootstrapped"`

```javascript
curl -X POST --data '{
    "jsonrpc":"2.0",
    "id"     :1,
    "method" :"info.isBootstrapped",
    "params": {
        "chain":"X"
    }
}' -H 'content-type:application/json;' 127.0.0.1:9650/ext/info
```

* If this returns as '`true`' , the chain is ready to receive API calls. If the node is not bootstrapped then you are unable to send API calls.&#x20;

```javascript
{"jsonrpc":"2.0","result":{"isBootstrapped":true},"id":1}
```

* Use `ctrl + C` to stop the node.

## 03 Make Requests

Avalanche uses **Standard Ethereum APIs, Avalanche Specific APIs **and an **Admin API** for debugging. &#x20;

### Standard Ethereum APIs

[Ethereum Wiki’s JSON-RPC Documentation](https://eth.wiki/json-rpc/API) and [Geth’s JSON-RPC Documentation](https://geth.ethereum.org/docs/rpc/server)&#x20;

supporting the following services:

* `web3_`
* `net_`
* `eth_`
* `personal_`
* `txpool_`
* `debug_`

#### Example Request

```javascript
curl '127.0.0.1:9650/ext/bc/C/rpc' \
  --data-raw '{"jsonrpc":"2.0","method":"web3_clientVersion","params":[],"id":0}' \
  --compressed
```

#### Example Response

```javascript
{"jsonrpc":"2.0","id":0,"result":"v0.7.0-rc.14"}
```

### Avalanche Specific APIs

Endpoints are for both the **C-Chain** and the **EVM AVAX **endpoints.

Read more in [Avalanche Docs](https://docs.avax.network/build/avalanchego-apis/contract-chain-c-chain-api#avalanche-specific-apis)

### Admin API

This is the API for debugging. To activate it
