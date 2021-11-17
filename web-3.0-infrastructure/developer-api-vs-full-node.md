# Developer API vs Full Node

## Developer API&#x20;

API Node Services are an enhanced service with the following features:

* Improved scalability,&#x20;
* Ultra reliable performance.
* INSTANT launching of nodes on demand.&#x20;

**Use Cases**

API Nodes  are useful for building dApps requiring higher throughputs and when full syncing to the highest block is a requirement.&#x20;

* **PROS**
  * Enterprise-grade connectivity to create and configure smart contracts, send and receive transactions, and request data from the blockchain.
  * Super fast, smooth, error-free connectivity to node clusters with RPC
  * Freedom from node management pain
  * Solves sync delays, reliability issues and high accuracy requirements.
* **CONS**
  * Rate Limiting
  * Access currently limited to specific blockchains.

## Full Node

{% hint style="warning" %}
**BE AWARE!**\
\
The Full Node deployment service for a chain will **CEASE** once Ankr launches a Developer API service for it. Current full nodes running will have 30 days to move the service over to the API. For most users, this represents a performance improvement at a cost savings.&#x20;
{% endhint %}

Full Node Deployment gives you the ability to launch nodes to 45+ chains in minutes on-demand.

This service deploys nodes in containers to bare metal servers.&#x20;

#### **Use Cases**

Full Nodes are useful for building dApps without high performance requirements.&#x20;

* PROS
  * Instant deployment and nodes on demand
  * Connect your application to the blockchain without complicated configuration
  * Freedom from node management pain
  * Add nodes on demand
* CONS
  * Sync delays with blockchain after initialization. Syncing can take hours, days, and for archive modes, even weeks.&#x20;
  * Individual nodes aren't optimized for sudden variations in traffic. This can lead to bottlenecks and/or errors.
