# Deploy ERC20 token

Deployment of ERC20 token can be done though Remix IDE of locally using truffle. Since BAS has EVM & Web3 support, it is compatible with Ethereum development toolsets. Remix is the easiest way to deploy ERC20 smart contract into BAS network.

To deploy an ERC20 token using Remix IDE go to remix page [https://remix.ethereum.org/](https://remix.ethereum.org) and on the deploy section choose `Injected Web3` (make sure your MetaMask is connected to one of the BAS networks). To get connected to the BAS network go to one of the BAS devnet's staking pages and it create new MetaMask network automatically (for example, [https://staking.dev-01.bas.ankr.com/](https://staking.dev-01.bas.ankr.com)). Or you can configure your MetaMask manually.

Use next snippet of ERC20 smart contract:

```
// SPDX-License-Identifier: GPL-3.0
pragma solidity >=0.7.0 <0.9.0;

import "@openzeppelin/contracts/token/ERC20/ERC20.sol";

contract MyERC20Token is ERC20 {

    constructor() ERC20("My Test Token", "MTT") {
        _mint(msg.sender, 1000 ether);
    }
}
```

Now you can go to the \`Solidity Compiler\` section to compile your smart contract and deploy it to the BAS network via \`Deploy & Run Transaction\` section.&#x20;

P.S: Make sure you choose \`MyERC20Token\` smart contract on deployment stage.
