# 설명
- nft거래소

# API
- opensea에 올릴 작품이 많은 경우 opensea에서 제공하는 API로 스크립트를 작성해서
빠르게 등록시킬 수 있다
- 튜토리얼: https://docs.opensea.io/docs
- github: https://github.com/ProjectOpenSea/opensea-creatures

# NFT 데이터 저장방식
1. centralized server
2. decentralized storage system `or` other blockchain
3. same blockchain as the NFT
- (추측) OpenSea는 기본적으로 1번방식으로 리소스를 저장하고, frozen을 사용하면 2번의 방식을 사용 (IPFS) (Filecoin같은 것)해서 저장해주는것으로 보임 ([filecoin with OpenSea](https://filecoin.io/blog/posts/opensea-decentralizes-and-persists-nft-storage-with-ipfs-and-filecoin/))

# Metadata 분산
- [article](https://opensea.io/blog/announcements/decentralizing-nft-metadata-on-opensea/)

# Minting Bot
- 매크로 봇의 방식이 아닌, 각 API와 contract를 사용해서 근본적인 해결방법을 사용한 영상
- [How to Code an NFT Minting Bot! [ERC-721, OpenSea, Solidity]](https://www.youtube.com/watch?v=94kkXt3AoNA)
