# Copy of Deploy ERC721 token

Deployment of ERC721 token is similar to ERC20 that is why we're skipping Remix preparation text here, but you still can find in \`Deploy ERC20 token\` section.&#x20;

Use next snippet of ERC721 smart contract:

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

MetaData URI is a link (usually on ipfs) that returns JSON object with information about your NFT token.

P.S: You can read more about NFT's (EIP-721) metadata in the official EIP page ([https://github.com/ethereum/EIPs/blob/master/EIPS/eip-721.md](https://github.com/ethereum/EIPs/blob/master/EIPS/eip-721.md)).&#x20;
