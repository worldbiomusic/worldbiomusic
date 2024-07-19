# RPC (Remote Procedure Call)
분산 시스템에서 다른 컴퓨터 또는 프로세스에 있는 함수를 네트워크를 통해 통신하는 메커니즘 프로토콜

## RPC의 역할
RPC를 사용하면 클라이언트가 원격 서버에게 요청을 보내고 응답을 받는 원격 프로시저 호출을 수행. 이더리움에서 RPC는 이더리움 클라이언트와 상호작용하기 위한 프로토콜로, JSON-RPC를 사용

> - 예. `web3.js`는 ethereum client와 통신하기 위해 JSON-RPC 프로토콜 사용
> - 예. 단순 curl로 HTTP 프로토콜 데이터를 보내서 상호작용도 가능
```sh
curl -X POST -H "Content-Type: application/json" --data '{"jsonrpc":"2.0", "method":"web3_clientVersion", "params":[],"id":1}' http://localhost:8545

{"jsonrpc":"2.0","id":1,"result":"Geth/v1.8.0-~~~"}
```

## RPC 예시
```json
{
    "jsonrpc": "2.0",
    "method": "eth_getBalance",
    "params": ["0x0fBd0BaB64cE0740Bc1CF1f4D7a87C191AE3E652", "latest"],
    "id": 1
}
```

위의 RPC 요청은 `eth_getBalance` 메서드를 사용하여 지정된 주소의 계정 잔액을 조회
> 클라이언트가 이 요청을 이더리움 노드에게 보내고, 노드는 해당 주소의 잔액을 응답으로 반환