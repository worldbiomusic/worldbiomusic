# genesis.json
네트워크 초기설정(chainId, concensus algorithm, accounts)에 사용됨

```json
{
    "config": {
        "chainId": 1515,
        "homesteadBlock": 0,
        "eip150Block": 0,
        "eip155Block": 0,
        "eip158Block": 0,
        "byzantiumBlock": 0,
        "constantinopleBlock": 0,
        "petersburgBlock": 0,
        "istanbulBlock": 0,
        "berlinBlock": 0,
        "clique": {
            "period": 5,
            "epoch": 30000
        }
    },
    "difficulty": "1",
    "gasLimit": "8000000",
    "extradata": "0x0000000000000000000000000000000000000000000000000000000000000000c01b38c3f016e4d751a20002c35b099392414bf20000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000",
    "alloc": {
        "fd25933599c5a5c72eaa70f53b071a9ee2889835": {
            "balance": 300000
        },
        "add25cd93d3f60219b9626484ef63d33120a350c": {
            "balance": 400000
        }
    }
}
```
- config에 ~Block 업데이트 블럭이 적힌 이유는 hard fork를 인정했다는 표시로, 노드들끼리 통신할 때 사용됨
- gasLimit: 현재 블럭의 최대 가스 사용량 (너무 적으면 트랜잭션이 안 담기고, 너무 크면 전파에 영향이 감소)