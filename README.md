# Carbon-footprint-analysis-and-mitigation-in-minting-an-ERC-721

## 1. Introduction

NFTs (Non-Fungible Tokens) were introduced in EIP-721 as a standard for Non-Funglble Tokens or Deeds on the Ethereum network. Uploading an image to the Ethereum network would be expensive due to GasFees, which is why EIP-721 has an optional metadata interface [1]. While all owners of NFTs buy them for different reasons, one could state NFTs are valued for authenticity and speculation. While NFTs are most known for their usage in art, they have 

This paper quantitatively analyses the ecological impact of minting an NFT (ERC-721) on different platforms and discussses various mmethods of reducing the Carbon Footprint as well as weighs the pros and cons of these methods. 

## 2. Analysis of the Carbon Footprint of a ERC-721

Please note that this research will hold valid as of 22 March, 2021. The author requests the reader the update themselves using the research methods mentioned or refer to the sources.

### 2.1 Comparing Carbon Footprint of Different Platforms

<br>

<center>

| Name          | Gas             | Transactions | kgCO2      |
|---------------|-----------------|--------------|------------|
| OpenSea       | 146,210,589,984 |      663,946 | 46,882,237 |
| Nifty Gateway |  22,692,781,162 |       82,920 |  8,638,915 |
| Rarible       |  21,336,740,026 |      169,149 |  7,032,924 |
| Makersplace   |  20,254,567,543 |       64,625 |  5,490,208 |
| SuperRare     |  14,816,160,348 |      160,293 |  4,449,347 |

<i>Estimate of total CO<sub>2</sub>  footprint for popular NFT marketplaces as of March 09, 2021</i>. Data provided by [4].

![Environmental Cost per Txn](https://i.imgur.com/9D9MeYs.png)
<i>kgCO<sub>2</sub> released per transaction</i>
</center>

### 2.1.1 Methodology of estimation

If $i$ is the index for all artwork, and $n$ is the total amount of artwork.

$$CarbonFootprint_\text{total} = \sum_{i=0}^{i=n} CarbonFootprint_\text{i}$$ 

McDonald uses Digiconomist and Etherscan to estimate Carbon Footprint of Ethereum Transactions corresponding to popular NFT marketplaces. 

According to [4], it is possible that mining pool locations and thus their correponding emissions intensity may have changed. Readers are suggested to do their own due diligence. 

### 2.1.2 How these platforms store NFT tokens

#### 2.1.2.1 OpenSea



## Off-Chain IPFS data storage

```solidity=
/// @title ERC-721 Non-Fungible Token Standard, optional metadata extension
/// @dev See https://eips.ethereum.org/EIPS/eip-721
///  Note: the ERC-165 identifier for this interface is 0x5b5e139f.
interface ERC721Metadata /* is ERC721 */ {
    /// @notice A descriptive name for a collection of NFTs in this contract
    function name() external view returns (string _name);

    /// @notice An abbreviated name for NFTs in this contract
    function symbol() external view returns (string _symbol);

    /// @notice A distinct Uniform Resource Identifier (URI) for a given asset.
    /// @dev Throws if `_tokenId` is not a valid NFT. URIs are defined in RFC
    ///  3986. The URI may point to a JSON file that conforms to the "ERC721
    ///  Metadata JSON Schema".
    function tokenURI(uint256 _tokenId) external view returns (string);
}
```

`tokenURI` allows for metadata to be stored offchain and the code to refer to the link in the smart contract. This is one of the methods the paper discusses later.

## References

1. [EIP-721: ERC-721 Non-Fungible Token Standard](https://eips.ethereum.org/EIPS/eip-721)
2. [Toward a New Ecology of Crypto Art: A Hybrid Manifesto](https://flash---art.com/2021/02/episode-v-towards-a-new-ecology-of-crypto-art/)
3. [A guide to ecofriendly CryptoArt (NFTs)](https://github.com/memo/eco-nft)
4. [Footprint of Cryptoart](https://github.com/kylemcdonald/cryptoart-footprint)
5. [Bitcoin and other PoW coins are an ESG nightmare](https://www.ofnumbers.com/2021/02/14/bitcoin-and-other-pow-coins-are-an-esg-nightmare/)
6. [Climate-Positive Crypto Art: The Next Big Thing Or NFT Overreach?](https://www.forbes.com/sites/lawrencewintermeyer/2021/03/19/climate-positive-crypto-art-the-next-big-thing-or-nft-overreach/?sh=3cb18142b0e6)
7. [10 Top NFT Artists Making Coin in the Latest Crypto Trend ](https://www.nasdaq.com/articles/10-top-nft-artists-making-coin-in-the-latest-crypto-trend-2021-02-26)
8. [Carbon Footprints of Ethereum Wallets](https://carbon.fyi/)
9. [It’s an NFT Boom. Do You Know Where Your Digital Art Lives?](https://www.coindesk.com/its-an-nft-boom-do-you-know-where-your-digital-art-lives)
10. [IT’S TIME TO CALCULATE THE ENVIRONMENTAL COST OF MOVING ART](https://missionmag.org/gallery-climate-coalition-art-world-sustainability/)
11. [Transactions in Ethereum](https://ethereum.org/en/developers/docs/transactions/)
