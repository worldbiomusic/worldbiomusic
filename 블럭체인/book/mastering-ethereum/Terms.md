# 단어
- `obfuscation`: reverse engineering 힘들게 하는 작업 (e.g. 변수 이름 의미없는것으로 바꾸기)
- `brute force attack`: 무차별 대입 공격
- `dictionary attack`: brute-force의 유형으로, 차이점은 존재하는 단어, 의미있는 숫자등을 가지고 대입 공격 (사람들은 단어를 가지고 비번만드는 경우가 많아 효율적)
- `rainbow table attack`: 미리 plain-text, hash(pain-text) table을 만들어놓고 hash가 일치하는것이 있으면 바로 plain-text로 비밀번호를 알수 있는 방법 > 막기 위해 salting 기술 사용됨
- `chain code`: child key를 extends할 때 parent가 child와 연결된걸 증명할 수 있는 chained 된 키 ([참고](http://52.78.94.176/en/glossary/chain-code.html))
- `key chain`: 프로그램(OS) 비밀번호 관리 시스템
- `type-0 wallet`: Non-deterministic wallet
- `type-1 wallet`: Deterministic wallet
- `type-2 wallet`: HD wallet
- `zero-knowledge`: prover가 verifer에게 지식을 밝히지 않고 알고있다는것을 증명하는 방법론 [링크](http://wiki.hash.kr/index.php/%EC%98%81%EC%A7%80%EC%8B%9D%EC%A6%9D%EB%AA%85), [블럭체인의 영지식 증명](https://medium.com/decipher-media/blockchain-zkp-series-1-%EB%B8%94%EB%A1%9D%EC%B2%B4%EC%9D%B8%EC%9D%98-%EC%98%81%EC%A7%80%EC%8B%9D-%EC%A6%9D%EB%AA%85-%ED%99%9C%EC%9A%A9%EC%84%B1-%EB%85%BC%EC%9D%98-9c73cc5c2c9) (관찰하는 제3는 이 증명의 결과를 알 수 없는 특징도 있다 (hash value 증명도 영지식 증명 아닌가?)
- `fallback`: 컨트랙트가 잘못받은 이더를 송신자한테 다시 되돌려주는 함수 ([참고](https://goodgid.github.io/Ethereum-Basic-Solidity-(14)/))
```
- contract에 명시되어있지 않으면 오류와 함께 이더가 sender에게 반송됨
- contract의 지갑에 돈을 들어가게 하려면 fallback function을 payable로 선언해야 함
- data없이 ether만 받거나, 잘못된 function 호출할 때 호출되는 함수
- 2300 gas만 사용 가능
```
- `data-payload`: 컴퓨터 패킷 전송단에서 볼때 header와 같은 네트워크에서 길찾는 용도같은것이 아닌, sender가 보낸 전송될 순수한 데이터 부분만을 의미 [참고](https://www.tutorialspoint.com/what-is-payload-in-computer-network)
- `nonce highest value`: 최대값은 protocol에 정의되어있지 않아 무한대라고 볼 수 있음 (현대 컴퓨터가 64-bit 이므로 64 이상의 숫자가 나오면 client에서 대응 업그레이드가 필요)
- `nonce`: nonce는 일반적으로 계정당 영구적으로 계속 증가 (nonce가 계정에 저장되어있는것은 아니므로 `getTransactionCount`으로 transaction 기록으로 구해야 함)
- `EOA vs Contract`: 둘다 계정의 의미(주소, 보유금액 등을 가짐), 하지만 차이점이 존재 > [차이점](https://www.oreilly.com/library/view/mastering-blockchain-programming/9781839218262/00403615-d0ec-4c80-94a0-dc1d24fd3246.xhtml)
- `ECDSA의 r, s, v`: `r`과`s`는 서명 함수에서 나온 결과값이고 `v`는 서명을 복구, 빠른 검증 속도를 위해 존재하는 값
- `Chain ID`: 블럭체인에서 트랜잭션에 들어간 자신의 chain id 데이터로 하드포크 된 다른 네트워크에서 자신이 보내는 트랜잭션이 또 사용되어 버리는 이중사용을 방지함
- `정지문제`: 프로그램을 실행해서 멈출지 영원히 계속 계산할지 정할 수 있는가?
- `stack-based`: 구현이 간단 / 컴파일이 간단 / 메모리에 값 저장 ([참고](https://s2choco.tistory.com/13))
- `register-based`: 디자인이 효율적 / 빠름 / 스택 오버헤드 x / 적은 명령어로 구현 용이 / CPU 레지스터에 값 저장
- `dispatcher`: account가 tx를 보내서 컨트랙트를 실행시킬 때 처음에 컨트랙트 함수를 호출해주는 도구 ([참고](https://chainsecurity.com/the-dispatcher-first-line-of-defense-in-any-eos-smart-contract/#:~:text=A%20dispatcher%20is%20the%20function,to%20invoke%20the%20intended%20function.))
- ``: 
- ``: 
- ``: 
- ``: 
- ``: 
- ``: 
- ``: 
- ``: 
- ``: 
- ``: 

