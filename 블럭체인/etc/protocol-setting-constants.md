# 설명
- [litecoin protocol](https://github.com/litecoin-foundation/loafwallet-core/tree/2ea83a2abb82c208900cd098dcb4239cd5a90d7d) 설정값 분석 문서
- 암호화폐 관련된 세팅값만 중점적으로 분석함

# BRAddress.c
- 


# BRAddress.h
- 


# BRArray.h
- C에서 사용할 배열 유틸 함수 파일


# BRBIP32Sequence.c
- 


# BRBIP32Sequence.h
- 


# BRBIP38Key.c
- 


# BRBIP38Key.h
- BRBIP38Key.c 헤더 파일



# BRBIP39Mnemonic.c
- 암호화폐 지갑을 니모닉(Mnemonic)방식(=Seed방식)으로 개인키를 증명할 떄 사용되는 기법
- "Mnemonic Phase"이란 단어보다는 "[Seed Phrase](https://en.bitcoin.it/wiki/Seed_phrase)"가 맞는 단어라고 함
> 정리: https://github.com/worldbiomusic/CryptoCurrency_INFO/blob/main/Seed%20Phrase.md


# BRBIP39Mnemonic.h
- BRBIP39Mnemonic.c 헤더 파일
- `BIP39_CREATION_TIME`: Mnemonic Phrase(Seed Phrase)는 버전이 맞는(?) 소프트웨어에서만 돌아가기 때문에, 생성시간을 저장해둬서 최신버전 phrase만 통과가 가능하게 하는 용도로 쓰이는것 같음
- `BIP39_WORDLIST_COUNT`: 니모닉 시드의 총 단어 개수


# BRBIP39WordsEn.h
- 니모닉 시드 2048개가 들어있는 배열을 가지고있는 헤더 파일


# BRBase58.c
- 암호화폐 내의 byte값들을 사람이 읽을 수 있는 문자열로 인코딩(encoding)하는 역할을 하는 파일
- 문자열로 봤을 때 구분하기 힘든 `0`, `O`, `I`, `l`을 제거한 58개의 문자로 변환하는 인코딩 규칙
- base58chars[]라는 변수에 58개의 char값이 들어있음
- [참고 링크](https://en.bitcoin.it/wiki/Base58Check_encoding)


# BRBase58.h
- BRBase58.c 헤더파일


# BRBloomFilter.c
- BloomFilter 알고리즘 사용 관련 파일
- `BLOOM_MAX_HASH_FUNCS`: bloom filter 알고리즘에서 사용할 해쉬 함수 최대 개수
> 정리: https://github.com/worldbiomusic/CryptoCurrency_INFO/blob/main/Bloom%20Filter.md


# BRBloomFilter.h
- BRBloomFilter.c 헤더 파일
- `BLOOM_DEFAULT_FALSEPOSITIVE_RATE`: bloom filter알고리즘의 거짓 긍정(false positive)의 기본 제한 수치
- `BLOOM_REDUCED_FALSEPOSITIVE_RATE`: bloom filter알고리즘의 거짓 긍정(false positive)의 감소된(더 강한) 제한 수치
- `BLOOM_UPDATE_NONE`: bloom filter 알고리즘 업데이트 관련 변수
- `BLOOM_UPDATE_ALL`: bloom filter 알고리즘 업데이트 관련 변수
- `BLOOM_UPDATE_P2PUBKEY_ONLY`: bloom filter 알고리즘 업데이트 관련 변수
- `BLOOM_MAX_FILTER_LENGTH`: bloom filter의 필터 최대 길이(bitmap의 bit 개수)(길이 = 크기)


# BRCrypto.c
- 해시 함수 암호화 관련 파일(일반 해시 함수와 cryptographic 해시 함수들이 구현되어 있음)
- [hash function VS cryptographic hash function 차이](https://security.stackexchange.com/questions/11839/what-is-the-difference-between-a-hash-function-and-a-cryptographic-hash-function)
- `C1`: 특정 단순한 해시 함수에서 암호화할 때 사용하는 상수, 별로 안중요 한 거 같음
- `C2`: 특정 단순한 해시 함수에서 암호화할 때 사용하는 상수, 별로 안중요 한 거 같음


# BRCrypto.h
- BRCrypto.c 헤더 파일


# BRInt.h
- int 형 관련 보조 기능들 포함 헤더 파일


# BRKey.c
- key(public, private) 관련 파일
- 'BITCOIN_PRIVKEY': WIP방법에서 mainnet일 때 앞에 붙이는 주소(network 성격 식별 용도)
- 'BITCOIN_PRIVKEY_TEST': WIP방법에서 testnet일 때 앞에 붙이는 주소(network 성격 식별 용도)
- 'WORDS_BIGENDIAN': 보통 네트워크에서는 big endian방법을 주로 사용하는것과 관련있는 값인듯 (변경할 필요 없어보임) ([little/big endian](https://genesis8.tistory.com/37))
- 'DETERMINISTIC': 암호화폐 관련 x
- 'USE_BASIC_CONFIG': 암호화폐 관련 x
- 'ENABLE_MODULE_RECOVERY': 암호화폐 관련 x
> 참고
> - [WIP개념](https://github.com/worldbiomusic/CryptoCurrency_INFO/blob/main/WIF.md)


# BRKey.h
- BRKey.c 헤더 파일


# BRMerkleBlock.c
- Merkle Tree와 관련된 파일
- `MAX_PROOF_OF_WORK`: 채굴의 최고 난이도 상수 값 (코드에선 target변수가 난이도를 나타냄)
- `TARGET_TIMESPAN`: 난이도를 조정할 떄 최소(`1/4배`)/최대(`4배`) 조정 비율을 정해주는 값 
- 난이도의 정도를 조절하는 알고리즘(difficulty target algorithm) 코드가 포함되 있음
> 참고
> - https://en.bitcoin.it/wiki/Protocol_documentation#Merkle_Trees
> - https://github.com/bitcoin/bips/blob/master/bip-0037.mediawiki#Partial_Merkle_branch_format


# BRMerkleBlock.h
- BRMerkleBlock.c 헤더 파일
- `BLOCK_DIFFICULTY_INTERVAL`: 블럭의 채굴 난이도가 변경되는 간격 개수(`2016`)
- `BLOCK_UNKNOWN_HEIGHT`: 블럭의 최대 높이(int 자료형의 최대 값 표현때문에 나중을 위한 체크로 사용되는 듯)
- `BLOCK_MAX_TIME_DRIFT`: 새로운 블럭의 timestamp 시간이 암호화폐 네트워크의 중간값과의 최대 허용 차이 상수 (`2 * 60 * 60`)(2시간)
> 참고
> - difficulty: https://en.bitcoin.it/wiki/Difficulty
> - timestamp: https://blog.bitmex.com/bitcoins-block-timestamp-protection-rules/


# BRPaymentProtocol.c


# BRPaymentProtocol.h


# BRPeer.c


# BRPeer.h



# BRPeerManager.c
- 


# BRPeerManager.h
- 


# BRSet.c
- 


# BRSet.h
- 


# BRTransaction.c
- 


# BRTransaction.h
- 


# BRWallet.c
- 


# BRWallet.h
- 













