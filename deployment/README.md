# **KOUPISS FOUFISS NFT Deployment Guide**

## **Prerequisites**

### **Required Tools**
1. **MetaMask**
   - Install MetaMask browser extension
   - Configure Moonbase Alpha testnet
   - Get test DEV tokens for gas fees

2. **Remix IDE**
   - Web-based development environment
   - No installation required
   - Access at [remix.ethereum.org](https://remix.ethereum.org)

3. **Pinata**
   - Create account for IPFS storage
   - Used for storing NFT images and metadata

4. **Rarible Testnet**
   - For viewing and testing NFTs
   - Compatible with MetaMask

## **Step-by-Step Deployment**

### **1. Prepare NFT Assets**

1. **Create NFT Image**
   - Prepare your image file
   - Supported formats: PNG, JPG, GIF

2. **Upload to Pinata**
   - Log into Pinata
   - Upload your image
   - Save the generated CID

3. **Create Metadata**
   ```json
   {
       "name": "NFT Name",
       "description": "NFT Description",
       "image": "ipfs://[Your-Image-CID]"
   }
   ```

4. **Upload Metadata**
   - Save metadata as JSON file
   - Upload to Pinata
   - Save metadata CID

### **2. Deploy Smart Contract**

1. **Open Remix IDE**
   - Go to [remix.ethereum.org](https://remix.ethereum.org)
   - Create new file `KOUPISSFOUFISS.sol`

2. **Paste Contract Code**
   ```solidity
   // SPDX-License-Identifier: MIT
   pragma solidity ^0.8.22;

   import {ERC721} from "@openzeppelin/contracts/token/ERC721/ERC721.sol";
   import {ERC721URIStorage} from "@openzeppelin/contracts/token/ERC721/extensions/ERC721URIStorage.sol";
   import {Ownable} from "@openzeppelin/contracts/access/Ownable.sol";

   contract KOUPISSFOUFISS is ERC721, ERC721URIStorage, Ownable {
       constructor(address initialOwner)
           ERC721("KOUPISS FOUFISS", "KPS")
           Ownable(initialOwner)
       {}

       function safeMint(address to, uint256 tokenId, string memory uri)
           public
           onlyOwner
       {
           _safeMint(to, tokenId);
           _setTokenURI(tokenId, uri);
       }

       function tokenURI(uint256 tokenId)
           public
           view
           override(ERC721, ERC721URIStorage)
           returns (string memory)
       {
           return super.tokenURI(tokenId);
       }

       function supportsInterface(bytes4 interfaceId)
           public
           view
           override(ERC721, ERC721URIStorage)
           returns (bool)
       {
           return super.supportsInterface(interfaceId);
       }
   }
   ```

3. **Compile Contract**
   - Set compiler version to 0.8.22
   - Click "Compile"

4. **Deploy Contract**
   - Go to "Deploy & Run Transactions"
   - Select "Injected Provider - MetaMask"
   - Enter your address as initialOwner
   - Click "Deploy"
   - Confirm transaction in MetaMask

### **3. Mint NFTs**

1. **Prepare Minting Parameters**
   - `to`: Your wallet address
   - `tokenId`: Start with 1
   - `uri`: `ipfs://[Your-Metadata-CID]`

2. **Execute Minting**
   - Call `safeMint` function
   - Enter parameters
   - Confirm transaction

### **4. Verify on Rarible**

1. **Connect to Rarible Testnet**
   - Use MetaMask to connect
   - Switch to correct network

2. **View Your NFT**
   - Enter contract address
   - Check image and metadata display

## **Troubleshooting**

### **Common Issues**
1. **Transaction Fails**
   - Check DEV token balance
   - Verify correct network
   - Ensure proper gas settings

2. **Image Not Showing**
   - Verify Pinata upload
   - Check metadata format
   - Wait for IPFS propagation

3. **Contract Verification**
   - Double-check contract address
   - Verify owner address

## **Additional Resources**
- [MetaMask Setup Guide](https://metamask.io/download)
- [Pinata Documentation](https://docs.pinata.cloud)
- [Rarible Testnet](https://testnet.rarible.com)
