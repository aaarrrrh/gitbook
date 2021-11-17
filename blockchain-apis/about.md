# About API Services

Ankr’s API service provides seamless HTTPS and Websocket access to a large selection of chains.

The service is optimized via our load-balanced node clusters and Remote Procedure Call (RPC) Gateway. This robust architecture provides services and APIs with significantly better reliability and performance compared to running an individual node.

## Who are they for? <a href="who-are-they-for" id="who-are-they-for"></a>

API Services are mainly suitable for Developers. The following use cases apply:

* Web 3.0 Developers looking for easy set up without hassle of running a node.
* Market Research & Analytics - exploring data and market opportunities.

## How they work <a href="how-they-work" id="how-they-work"></a>

Ankr Node Clusters sit on top of several nodes and enable node balancing with a Remote Procedure Call (RPC) Gateway. The RPC Gateway automatically redirects requests from a node encountering an error towards a working node. This means that blocks continue to be confirmed even if one or several nodes encounter an error and require a restart. The RPC layer provides a multi-chain protocol and chain endpoints that can be queried.

### Connecting to Chains <a href="connecting-to-chains" id="connecting-to-chains"></a>

Connecting to chains requires using [JSON-RPC API](../resources/articles/json-rpc-api.md) from a client to query smart contract data and submit transactions to a node.

### Architecture <a href="architecture" id="architecture"></a>

​ :one: Chains being validated&#x20;

​ :two: Nodes A, B, C are distinct nodes providing validation of transactions and finality.

​ :three: The Node Cluster ensures the redirection of data from any nodes in an error state to a working node. It provides API Endpoints to interface with the Developer API and automatically syncs in real-time with it.

![](<../.gitbook/assets/API-Architecture-ANKR (1).png>)

## At-a-Glance Comparison <a href="at-a-glance-comparison" id="at-a-glance-comparison"></a>

### One Click Node vs Developer APIs <a href="one-click-node-vs-developer-apis" id="one-click-node-vs-developer-apis"></a>

| Features                  | One-Click Node                                                         | Developer API                                                                                                                               |
| ------------------------- | ---------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------- |
| NODE QUANTITY             | 1 Node                                                                 | Cluster of Nodes                                                                                                                            |
| RELIABILITY               | Less than 98%                                                          | 99.99%                                                                                                                                      |
| SYNC TIME TO LATEST BLOCK | Hours                                                                  | Instant                                                                                                                                     |
| AVAILABILITY ZONES        | Auto-selected by Ankr                                                  | <p>Selected by user:<br>APAC North America<br>Europe (Coming Soon)</p>                                                                      |
| DASHBOARD                 | <p>Basic dashboard</p><ul><li>node status </li><li>endpoints</li></ul> | <p>Detailed dashboard </p><ul><li>request history, </li><li>response time, </li><li>invalid requests </li><li>error log reasoning</li></ul> |
| REQUESTS PER SECOND (TPS) | Up to 300 per second                                                   | Up to 10,000 per second                                                                                                                     |
| PRICING                   | <p>Starting at $49/m USD<br>Payable in Ankr tokens</p>                 | Starting with free plan                                                                                                                     |

