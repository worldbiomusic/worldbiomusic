## `networkid`
- `networkid`는 특정 이더리움 네트워크를 식별하는 데 사용 
- 하드포크된 네트워크 분리를 위해 사용
- 같은 `networkid`를 가진 노드들만 서로 통신 (서로 물어봄)
- 인자: `--networkid 12345`

**예시**:
- 메인넷: `networkid = 1`
- Ropsten 테스트넷: `networkid = 3`
- Rinkeby 테스트넷: `networkid = 4`
- Goerli 테스트넷: `networkid = 5`
- 프라이빗 네트워크: 사용자 정의 `networkid`

## `chainid`
- 트랜잭션 서명을 네트워크마다 구분하기 위해 사용
- 각 체인마다 고유한 `chainid`를 할당
- 한 체인에서 서명된 트랜잭션이 다른 체인에서 유효하지 않도록 함 (동일 트랜잭션이 다른 체인에서 결제되는 ReplayAttack을 방지)
- 인자: `--chainid 12345`

**예시**:
- 메인넷: `chainid = 1`
- Ropsten 테스트넷: `chainid = 3`
- Rinkeby 테스트넷: `chainid = 4`
- Goerli 테스트넷: `chainid = 5`
- Kovan 테스트넷: `chainid = 42`
- 사용자 정의 체인: 사용자 정의 `chainid`

## 중요한 것
**트랜잭션 포함 여부**  
networkid는 트랜잭션에 포함되지 않고, chainid는 트랜잭션에 포함 됨

**networkid가 같은 경우**  
ETH와 EXP같이 ETH에서 포크된 경우 기존 노드들이 포크 이전의 결제에 대한 작업을 양쪽 네트워크의 노드들이 지원할 수 있으므로 chainid는 다르지만 networkid는 같을 수 있음