# 데이터 타입

## 원시 (primitive)
- bool: 참 거짓
- uint: 부호 없는 정수 (0과 양수) (기본 uint256이고 8비트 간격으로 조절가능) (type(uint).min으로 최소값 확인 가능)
- int: 부호 있는 정수 (기본 int256이고 8비트 간격으로 조절가능)
- address: 이더리움 계정 주소 (20bytes)
- byte: 고정된 크기 바이트 배열 (bytes1~32 가능)
- enum: 상수값 열겨형


## 참조 (reference)
- array: 고정 or 동적배열
- struct: 사용자 정의 자료형
- string: 문자열. 바이트로 저장됨
- mapping: key-value 쌍


## 리터럴(literal)
- 주소: 0x로 시작하는 주소
- 유리수와 정수
- 문자열: "로 감싼 문자

```sol
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.26;

contract Primitives {
    bool public boo = true;

    /*
    uint stands for unsigned integer, meaning non negative integers
    different sizes are available
        uint8   ranges from 0 to 2 ** 8 - 1
        uint16  ranges from 0 to 2 ** 16 - 1
        ...
        uint256 ranges from 0 to 2 ** 256 - 1
    */
    uint8 public u8 = 1;
    uint256 public u256 = 456;
    uint256 public u = 123; // uint is an alias for uint256

    /*
    Negative numbers are allowed for int types.
    Like uint, different ranges are available from int8 to int256
    
    int256 ranges from -2 ** 255 to 2 ** 255 - 1
    int128 ranges from -2 ** 127 to 2 ** 127 - 1
    */
    int8 public i8 = -1;
    int256 public i256 = 456;
    int256 public i = -123; // int is same as int256

    // minimum and maximum of int
    int256 public minInt = type(int256).min;
    int256 public maxInt = type(int256).max;

    address public addr = 0xCA35b7d915458EF540aDe6068dFe2F44E8fa733c;

    /*
    In Solidity, the data type byte represent a sequence of bytes. 
    Solidity presents two type of bytes types :

     - fixed-sized byte arrays
     - dynamically-sized byte arrays.
     
     The term bytes in Solidity represents a dynamic array of bytes. 
     It’s a shorthand for byte[] .
    */
    bytes1 a = 0xb5; //  [10110101]
    bytes1 b = 0x56; //  [01010110]

    // Default values
    // Unassigned variables have a default value
    bool public defaultBoo; // false
    uint256 public defaultUint; // 0
    int256 public defaultInt; // 0
    address public defaultAddr; // 0x0000000000000000000000000000000000000000
}
```