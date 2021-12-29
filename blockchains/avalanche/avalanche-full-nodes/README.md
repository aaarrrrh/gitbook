# About Avalanche Nodes and APIs

## **Avalanche Full Nodes**

Running a full Avalanche node means you can easily interact with the main network without relying on a third party. You can be part of multiple subnets within the Avalanche ecosystem at the same time.

Ankr allows users to create their own Avalanche APIs with a variety of options for request call limits, archived data, and more. Ankr also offers full API capabilities with Ortelius, the Avalanche indexer that provides users with archived information. Ankr’s novel cluster technology allows APIs to draw from multiple nodes, offering a more reliable experience for our users.

### Get started on Avalanche Full Nodes

1. Login or set up an account on app.ankr.com
2. [**Create Full Node**](https://app.ankr.com/apps/nodes)

### Node Types Available on Ankr

* Full Node;
* Ortelius Node;
* Validator Node;

### Explorer links

​[https://avascan.info/](https://avascan.info)​

​[https://explorer.avax.network/](https://explorer.avax.network)

### Avalanche Subnet Node APIs

Avalanche Clients interact with Avalanche through API calls to nodes.

Numeric parameters in API calls may be given as strings (e.g. `"5"` or `5` are both ok for an integer argument). Numeric return values are always given as strings (e.g. `"5"` rather than`5`).

### ​ **** [**X-Chain API**](https://docs.avax.network/build/avalanchego-apis/exchange-chain-x-chain-api)****

The X-Chain, Avalanche’s native platform for creating and trading assets, is an instance of the Avalanche Virtual Machine (AVM). This API allows clients to create and trade assets, including AVAX, on the X-Chain as well as other instances of the AVM.

### [C-Chain API](https://docs.avax.network/build/avalanchego-apis/contract-chain-c-chain-api) <a href="#evm-c-chain-api" id="evm-c-chain-api"></a>

Allows clients to interact with the C-Chain, Avalanche’s main EVM instance, as well as other EVM instances.

### [P-Chain API](https://docs.avax.network/build/avalanchego-apis/platform-chain-p-chain-api) <a href="#p-chain-api" id="p-chain-api"></a>

Allows clients to interact with the P-Chain (Platform Chain), which maintains Avalanche’s validator set and handles blockchain and subnet creation.

### [Keystore API](https://docs.avax.network/build/avalanchego-apis/keystore-api) <a href="#keystore-api" id="keystore-api"></a>

Allows clients to use an Avalanche node’s built-in keystore.

### [Health API](https://docs.avax.network/build/avalanchego-apis/health-api) <a href="#health-api" id="health-api"></a>

Allows client to check a node’s health.

### [Metrics API](https://docs.avax.network/build/avalanchego-apis/metrics-api) <a href="#metrics-api" id="metrics-api"></a>

Allows clients to collect Prometheus metrics about a node.

### [Admin API](https://docs.avax.network/build/avalanchego-apis/admin-api) <a href="#admin-api" id="admin-api"></a>

Allows clients to examine a node’s internal state, set of connections, and similar internal protocol data.

### [Info API](https://docs.avax.network/build/avalanchego-apis/info-api) <a href="#info-api" id="info-api"></a>

Allows clients to examine basic information about a node.

