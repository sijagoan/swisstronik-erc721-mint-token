# Swisstronik Testnet 2.0 (Deploy ERC-721 Token).

Link : [Click!](https://www.swisstronik.com/testnet2/dashboard)

## Steps

### 1. Clone Repository

```bash
git clone https://github.com/sijagoan/swisstronik-erc721-mint-token.git
```

```
cd swisstronik-erc721-mint-token
```

### 2. Install Dependency

```bash
npm install
```

### 3. Set .env File

create .env file in root project

```bash
touch .env
```

add this to your .env file
```bash
PRIVATE_KEY="your private key"
```

### 4. Update Smart Contract (Skipp if you won't modify NFT name)

- Open contracts folder
- Open Nft.sol file
- Feel free to modify token name and token symbol

```
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

import "@openzeppelin/contracts/token/ERC721/ERC721.sol";

contract TestNFT is ERC721 {
    uint256 private _currentTokenId = 0;

    event NFTMinted(address recipient, uint256 tokenId);

    constructor() ERC721("DogsNFT", "DOGS") {}

    function mintNFT(address recipient) public returns (uint256) {
        _currentTokenId += 1;
        uint256 newItemId = _currentTokenId;
        _mint(recipient, newItemId);

        emit NFTMinted(recipient, newItemId);

        return newItemId;
    }

    function burnNFT(uint256 tokenId) public {
        _burn(tokenId);
    }
}

```

### 5. Compile Smart Contract

```bash
npm run compile
```

### 6. Deploy Smart Contract

```bash
npm run deploy
```

### 7. Mint Token

```bash
npm run mint
```

### Finished.

Address Testnet 0xE07E1B83d974E90EE489D2aFa227B676D2a43B3F
