# 솔리디티의 기본 개념들

솔리디티 언어를 배우기 전에 알면 좋은 개념들

- 블록체인: 분산된 환경에서 트랜잭션 주고받으며 데이터 무결성을 유지하는 기술
- 트랜잭션: 네트워크에서 데이터 변경을 일으키는 기록
- 블록: 블록체인 관련 데이터를 담고 있는 덩어리
- EVM: 이더리움 가상 머신
- 계정: 이더리움에서 계좌 역할을 담당
- 가스: EVM의 가상 실행 단위
- 스토리지: 블록체인에 기록되는 영구저장공간 (상태 기록)
- 메모리: 함수 실행중 일시적으로 데이터 저장하는 공간 (string혹은 배열)
- 스택: 연산과 함수 호출을 위한 고정된 임시 저장 공간

간단한 코드 미리보기
```sol
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.26;

contract Counter {
    uint256 public count;

    // Function to get the current count
    function get() public view returns (uint256) {
        return count;
    }

    // Function to increment count by 1
    function inc() public {
        count += 1;
    }

    // Function to decrement count by 1
    function dec() public {
        // This function will fail if count = 0
        count -= 1;
    }
}
```