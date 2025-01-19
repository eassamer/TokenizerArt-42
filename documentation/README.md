# **KOUPISS FOUFISS NFT Documentation**

## **Overview**
This document provides detailed information about the KOUPISS FOUFISS NFT collection, including its specifications, features, and functionality. The KOUPISS FOUFISS NFT is an ERC-721 compliant token deployed on the Ethereum blockchain, designed to create unique, non-fungible tokens with associated metadata stored on IPFS.

## **Token Details**
- **Name**: KOUPISS FOUFISS
- **Symbol**: KPS
- **Token Standard**: ERC-721
- **Storage**: IPFS via Pinata
- **Visualization**: Rarible Testnet
- **Contract Address**: `0xAff2d2526981eb6E8395956AbBd1d6A72F66602C`

## **Features**

### **ERC-721 Compliance**
KOUPISS FOUFISS follows the ERC-721 token standard, ensuring compatibility with NFT marketplaces, wallets, and decentralized applications (dApps) in the Ethereum ecosystem.

### **Token Functions**
The NFT implements standard ERC-721 functions and additional features:

- **`safeMint(address to, uint256 tokenId, string memory uri)`**
  - **Description**: Safely mints a new NFT to the specified address with metadata URI
  - **Access**: Only contract owner
  - **Example**:
    ```solidity
    function safeMint(address to, uint256 tokenId, string memory uri) public onlyOwner
    ```

- **`tokenURI(uint256 tokenId)`**
  - **Description**: Returns the URI for a given token's metadata
  - **Example**:
    ```solidity
    function tokenURI(uint256 tokenId) public view returns (string memory)
    ```

- **`supportsInterface(bytes4 interfaceId)`**
  - **Description**: Checks if the contract supports specific interfaces
  - **Example**:
    ```solidity
    function supportsInterface(bytes4 interfaceId) public view returns (bool)
    ```

### **Extensions and Inheritance**
The contract inherits from multiple OpenZeppelin contracts:
- **ERC721**: Base NFT functionality
- **ERC721URIStorage**: Metadata storage capabilities
- **Ownable**: Access control for minting

### **Metadata Structure**
Each NFT contains metadata stored on IPFS with the following structure:
```json
{
    "name": "NFT Name",
    "description": "NFT Description",
    "image": "ipfs://[CID]/image",
}
```

## **How It Works**

1. **Deployment**
   - The contract is deployed with an initial owner address
   - NFTs can be minted only by the contract owner

2. **Minting Process**
   - Upload NFT asset to IPFS via Pinata
   - Upload metadata JSON to IPFS
   - Call `safeMint` with:
     - Recipient address
     - Token ID
     - IPFS metadata URI

3. **Viewing NFTs**
   - NFTs can be viewed on Rarible testnet
   - Compatible with standard NFT wallets like MetaMask
   - Metadata and images are served from IPFS

4. **Security Features**
   - Implements OpenZeppelin's secure contract standards
   - Owner-only minting control
   - Safe transfer mechanisms
   - Standard ERC-721 security features


## **Conclusion**
The KOUPISS FOUFISS NFT (KPS) is a fully-featured ERC-721 token implementing current best practices for NFT development. Its compliance with the ERC-721 standard and integration with IPFS ensures compatibility with the broader NFT ecosystem while maintaining decentralized storage of assets and metadata.