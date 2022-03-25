# Glossary

#### BAS

Framework for creating sidechains in the BSC ecosystem.&#x20;

#### BAS Modules

Configurable and programmable modules that extend the base BAS functionality that is obtained applying the BAS template. Internally, BAS implements the following modules: Parlia consensus engine, staking pools, governance, dynamic runtime upgrades, reward management, manageable blockchain params, EVM hooks, deployment proxy.&#x20;

#### Template

A ready-made blockchain solution that is already integrated into the BSC infrastructure. A template defines the primary structure and configuration of the blockchain, using special templates. With the BSC integration, developers automatically get access to such useful products as a ready-made staking system, block explorer, SDK, API gateways, interfaces for governance, etc. \
Right now, we offer a single BSC-based template. In the future, the list of templates will be extended.

#### BAS Validator Hub

A smart contract that adds to cross-chain functionality to the BAS applications. It registers the BAS application in the BSC smart contract.

See this code example for technical details:

```
interface BASValidatorHub {
  function registerBAS(string projectName, address[] initialValidatorSet, IBlockHeaderVerificationFunction bhvf) external;
```

####

#### Block header verification (BHVF)

A Solidity function that verifies block headers from BAS applications, thus ensuring the validators are not compromised. Also, BHVF is responsible for verifying transaction receipt from blockchain that allows to prove the correctness of cross-chain transfer from BAS to BSC chain.

#### BLS cryptography

Boneh–Lynn–Shacham cryptography for signature verification and more. For more detail, refer to [CryptoWiki](https://cryptography.fandom.com/wiki/BLS\_\(cryptography\)).

#### BSC

BNB Chain, formerly known as Binance Smart Chain. The Binance chain with smart contracts support.&#x20;

#### BSC Infrastructure

BSC brings with it a ready-made staking system, block explorer, SDK, API gateways, interfaces for governance, etc. All that is easily accessible to BAS developers, as creating a BAS they apply a BAS template that includes integration with this infrastructure.

#### EVM

A powerful, sandboxed virtual stack embedded within each full Ethereum node, responsible for executing contract bytecode. It controls smart contract deployment and execution.

#### **Governance**

On-chain governance in each BAS to let users vote for the new proposal on the chain. Voting power is distributed based on the total delegated amount to the validator. Once ⅔ of the quorum is reached and >51% of votes are for the proposal then it can be executed by anyone on the chain. Governance is able to manage staking parameters like felony threshold or jail period.

#### Native asset bridge

A cross-chain bridge that is embedded to BAS as a system smart contract. It supports deposits (BAS -> BSC) and withdrawals (BSC -> BAS).

#### Parlia Consensus Engine

A Proof-of-Staked Authority (PoSA) consensus algorithm for BSC. It incorporates elements from both Proof-of-Stake and Proof-of-Authority. Parlia is similar to [clique](https://ethereum-magicians.org/t/eip-225-clique-proof-of-authority-consensus-protocol/1853).

For more detail, read about Parlia on [Binance docs](https://docs.binance.org/smart-chain/guides/concepts/consensus.html#consensus-protocol).

#### System Smart Contracts

A predefined set of system smart contracts that a BAS provides for platform operation.&#x20;

Predefined BSC-compatible system smart contracts:

* Staking (`0x0000000000000000000000000000000000001000`) - for managing validator delegations and active validator set.
* SlashingIndicator (`0x0000000000000000000000000000000000001001`) - for slashing not active validators.
* SystemReward (`0x0000000000000000000000000000000000001002`) - treasury for the system rewards to cover relay fees and others.

BAS-defined smart contracts:

* Governance (`0x0000000000000000000000000000000000007002`) - default on-chain implementation by Compund’s Alpha governance.
* ChainConfig (`0x0000000000000000000000000000000000007003`) - configuration for the consensus that is managed by on-chain governance.
* NativeAssetBridge (`0x0000000000000000000000000000000000007004`) - cross-chain bridge for native assets between BAS and BSC.