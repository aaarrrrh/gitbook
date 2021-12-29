# EVM (C-Chain) API

## Deploying a Smart Contract <a href="#deploying-a-smart-contract" id="deploying-a-smart-contract"></a>

For a tutorial on deploying a Solidity smart contract on the C-Chain, see [here.](https://docs.avax.network/build/tutorials/smart-contracts/deploy-a-smart-contract-on-avalanche-using-remix-and-metamask)​

## Methods <a href="#methods" id="methods"></a>

This API is identical to Geth’s API except that it only supports the following services:

* `web3_`
* `net_`
* `eth_`
* `personal_`
* `txpool_`

You can interact with these services the same exact way you’d interact with Geth. See the [Ethereum Wiki’s JSON-RPC Documentation](https://eth.wiki/json-rpc/API) and [Geth’s JSON-RPC Documentation](https://geth.ethereum.org/docs/rpc/server) for a full description of this API.

## JSON-RPC Endpoints <a href="#json-rpc-endpoints" id="json-rpc-endpoints"></a>

To interact with C-Chain (the main EVM instance on Avalanche):

To interact with other instances of the EVM:

## Examples <a href="#examples" id="examples"></a>

### Getting the current client version <a href="#getting-the-current-client-version" id="getting-the-current-client-version"></a>

## **Example Call** <a href="#example-call" id="example-call"></a>

```javascript
//Request
curl -X POST --data '{ 
    "jsonrpc": "2.0",    
    "method": "web3_clientVersion",    
    "params": [],    
    "id": 1
}' -H 'Content-Type: application/json;' http://<your-node-id>.ankr.com/ext/bc/C/rpc 

//Response​
{
    "jsonrpc": "2.0",    
    "id": 1,    
    "result": "Athereum 1.0"
    }  
```
