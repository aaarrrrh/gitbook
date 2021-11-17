# Nuls

The **Nuls** blockchain development platform divides the blockchain into several modules such as network, account, ledger, storage, consensus, and smart contract. Every module will perform independently, ignoring the change of other modules. The modules of Nuls cooperate through the service bus and event bus. The microkernel manages the service bus and event bus.

![](https://gblobscdn.gitbook.com/assets%2F-MF6NYa65t3TUvQZ0zRX%2F-MGc5VqSuZCzK\_-7BnER%2F-MGc7GafYE7fJdaNisvD%2Fnuls\_blockchain\_freatures.jpg?alt=media\&token=0f2c2bf8-0d26-40fd-949d-50655a9152cc)

The default consensus mechanism of Nuls is Proof-of-Credit (POC). The nodes of the consensus meeting should pack blocks by turns, and every node only packs one block per round. Sub-chains on the Nuls platform can use other mechanisms by replacing the consensus module.

Nuls API Service official endpoint: [https://api.nuls.io/jsonrpc](https://api.nuls.io/jsonrpc)​

Nuls Public Service official endpoint: [https://public1.nuls.io](https://public1.nuls.io)​

In the following subchapters, we will describe how to obtain the End-point from the Ankr platform and how to execute RPC calls.
