# Covalent

API Documentation: https://www.covalenthq.com/docs/api/

The Covalent API has two classes of endpoints:

* Class A - endpoints that return enriched blockchain data applicable to all blockchain networks, eg: balances, transactions, log events, etc.
* Class B - endpoints that are for a specific protocol on a blockchain, eg: AAVE is Ethereum-only and is not applicable to other blockchain networks.

The Covalent API is RESTful. The API is designed around the main resources that are available through the web interface. All requests are done over HTTPS (calls over plain HTTP will fail). The default return format for all endpoints is JSON. The root URL of the API is [https://api.covalenthq.com/v1/](https://api.covalenthq.com/v1/) We classify the Refresh rate of the APIs as real-time: 30s or 2 blocks, and batch 10m or 40 blocks.

This is an informational guide on how Covalent can serve as the go to tool for ANKR in querying Blockchain data across all supported Networks. This guide focuses on the REST protocol to query data. We will discuss 4 example cases and how Covalent APIs is the best solution for ANKR to crawl through the networks.
