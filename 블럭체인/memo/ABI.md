# ABI (Application Binary Interface)
데이터구조와 함수가 어떻게 기계 코드(machine code)에서 사용되는지 방법을 정의 (API는 고수준 소스코드(source code))

> 이더리움에서는 스마트 컨트랙트와 EVM 사이의 상호작용을 정의하는 인터페이스로 사용됨

## 구성 요소
- 함수 및 이벤트의 이름과 시그니처
- 함수 및 이벤트의 매개변수 및 반환값의 타입
- 함수의 상태 변경 여부
- 컨트랙트의 주소 및 생성자 매개변수

## 역할
- 또한 ABI로 추출된 형식을 RPC를 사용해서 네트워크 상에서 컨트랙트를 호출함
- JSON 형식으로 제공
- ABI를 사용해서 지갑이나 Dapp에서 스마트컨트랙트 함수를 트랜잭션을 생성해서 호출 가능 (필요한 것: ABI와 컨트랙트 주소)

## 예시
**Solidity**  
```js
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract SimpleStorage {
    uint256 private storedData;

    function set(uint256 newValue) public {
        storedData = newValue;
    }

    function get() public view returns (uint256) {
        return storedData;
    }
}
```

**ABI**  
```json
[
    {
        "constant": false,
        "inputs": [
            {
                "name": "newValue",
                "type": "uint256"
            }
        ],
        "name": "set",
        "outputs": [],
        "payable": false,
        "stateMutability": "nonpayable",
        "type": "function"
    },
    {
        "constant": true,
        "inputs": [],
        "name": "get",
        "outputs": [
            {
                "name": "",
                "type": "uint256"
            }
        ],
        "payable": false,
        "stateMutability": "view",
        "type": "function"
    }
]
```

**RPC 호출 예시:**
1. `set` 함수 호출:
   - 메서드: `eth_sendTransaction`
   - 매개변수:
     - `to`: 스마트 컨트랙트의 주소
     - `data`: `set` 함수의 함수 시그니처와 매개변수 값 (예: `0x60fe47b100000000000000000000000000000000000000000000000000000000000002a`)
   - 예시:

     ```json
     {
         "jsonrpc": "2.0",
         "method": "eth_sendTransaction",
         "params": [
             {
                 "from": "0xYOUR_ADDRESS",
                 "to": "0xCONTRACT_ADDRESS",
                 "data": "0x60fe47b100000000000000000000000000000000000000000000000000000000000002a"
             }
         ],
         "id": 1
     }
     ```

2. `get` 함수 호출:
   - 메서드: `eth_call`
   - 매개변수:
     - `to`: 스마트 컨트랙트의 주소
     - `data`: `get` 함수의 함수 시그니처 (예: `0x6d4ce63c`)
   - 예시:

     ```json
     {
         "jsonrpc": "2.0",
         "method": "eth_call",
         "params": [
             {
                 "to": "0xCONTRACT_ADDRESS",
                 "data": "0x6d4ce63c"
             },
             "latest"
         ],
         "id": 1
     }
     ```

위의 예시에서 ABI를 사용하여 함수 호출에 필요한 데이터를 구성하고, RPC를 사용하여 이 데이터를 노드에 전송하여 스마트 컨트랙트와 상호작용할 수 있음 (`ABI`: 함수 호출의 매개변수와 반환값의 형식을 정의, `RPC`: 이러한 함수 호출을 실제로 수행합니다.)