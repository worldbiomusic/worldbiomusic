# 보안
- transparency: 사용자 몰래 (성능영향 없이)
- visibility: 데이터 보이기 좋게 저장
- 데이터의 처리, 가공, 저장의 주체가 시대의 흐름에 따라 기업과 사용자사이에서 계속 반복됨
- 엔드포인트(핸드폰, 컴퓨터)를 보통 엣지 컴퓨팅이라고 부름 (상반되는건 클라우드) (중간에는 fog라고 연결매게체라고 함)
- Malware (Malicious software): virus, worm, ransonware, trojan horse
- 보통 root쪽 (최대 bias)으로 해킹하려고 노력함 (백신보다 먼저 실행되려고 (RootKit)) (백신도 동시에 앞쪽으로 가려고 함 (ELAM))

**공격방법**  
- Phising: 이메일, 보이스 등
- Pharming: DNS poisioning (url에 매핑된 ip 위조) (hosts 파일 변조)

- 시그니처(signature): 각 멀웨어의 특징을 정형화 해서 탐지 (rule-based)
- 난독화를 분석하는것은 불가능하지 않고 어려운것 뿐
- 행위 기반(behavior): 프로그램이 하는 행위를 추상화해서 탐지 (시그니처를 보완)
- malware 관련 도구: Themida, VMProtect, upx
- sandbox: 가상환경에서 바이러스인지 테스트
- cloud(reputation): 

- vulnerbility life cycle: 0day보다 1day 공격이 더 많음 (많이 알려지기도 했고, 패치가 완벽히 안나와서 알고 당해야하는 경우가 많음)


# 기타
- 해킹과 보안은 race condition
- 백신은 진단에서 오진이 되게 중요함 (시스템 관련 파일 삭제해버리면 안되므로)
- 보안과 해킹중 보통 해킹이 우세
- 네트워크가 발전 -> 시스템이 발전 -> 서비스 어플리케이션 발전 -> 보안 -> 다시 네트워크...
- 보안은 기술이 새로 나옴에 따라 적용되는 방식이 달라서 서비스 어플리케이션이 발전된 다음에 발전하는 경우가 많음 (기술 트렌드에 민감하게 반응해야 함)
- 결국은 보안은 데이터 보호
- 컴퓨터 관련 용어들은 사회학자들이 정의하는 경우가 많음

- pareto 법칙: 20%가 80%를 책임진다
- long tali: 기술을 잘 활용하면 80%가 20%를 능가할 수 있다 (예. 아마존은 인터넷이란 도구로 80%책을 많이 팜, 네이버는 80%의 약한 집단지성으로 지식인서비스로 많이 알려짐)
- 기술은 사회의 필요성(사람)에 영향을 많이 받음 (예. 공인인증서 기술 자체는 뛰어나지만 편의성등의 문제로 없어짐. 하지만 비트코인도 똑같은 기술이지만 더 불편해도 잘 씀): 인간사회와 합의할 수 있는 시간이 필요함 (예. 코로나는 IT서비스를 인간사회와의 격차를 반강제적으로 줄여줌) (기술쪽 사람들도 자신의 직업이 AI에게 위협받을것 같으면 변화하기 싫은 자연스러운 방어기제가 발생)

- 백신을 무료로 배포하는 이유: 멀웨어 관련 데이터 수집 (나중에 더 강한 백신을 만들어서 팔려고)
- 폐쇠네트워크에는 아직도 옛날 멀웨어가 잔존하는 경우가 있다
- 안랩에서 매일 80만개정도 파일을 수집한다고 함 (20만개가 멀웨어 관련)
- decision tree가 가장 성능 잘나왔다고 함
- 기존 도메인에 AI적용할 조건 정해본것: 기존에 풀기 어려운 것, 이미 있지만 성능을 향상시키는 것
- 보안을 위한 AI도 있지만 AI를 위한 보안도 있음
- 미국의 `mitre`는 세계적으로 보안 기준
- 강사의 개인적 경험으로, 도메인 관련 기술자가 AI를 도입하는것이 AI전문가가 특정 도메인에 가는것보다 효율적 (AI모델도 이미 쉽게 사용가능하므로)
- virustotal 사이트에 PE 파일 그대로 올리면 개인정보 유출 됨


---

 # 2일차

- 강의는 windows 32bit 기준
 - [mitre attack](https://attack.mitre.org/): cyber attack chain보다 더 구체적인 공격/방어 기법
 - mitre attack은 실제로 가상환경에서 직접 procedure따라해보는게 좋음 (버전 중요)
 - [attack-navigator](https://mitre-attack.github.io/attack-navigator/): 관련된 attack 연결된 페이지

 - 멀웨어는 사용자를 대상으로 하므로 사용자가 많이 사용하는 OS와 network를 많이 알아야 함
 - 블루스크린 대부분은 백신이 실수해서 나타나는경우 많음
 - 구조나 그래프볼 때 가운데부터 위 아래로 보는게 좋음
 - windows는 user mode, system mode로 격리되서 동작 (user mode에서는 sub system DLL을 사용해서 system mode에 요청)
 - subsystem dll 알아둬야 좋음 (대부분의 system call 전달하는 용도)
 - 그래픽 관련은 계산이 많아서 system call 안 거치고 실행
- 가상 메모리 총 4GB 제공: 2GB는 OS가, 2GB는 user가 사용

- hooking: 함수 호출같은 요청을 가로채서 로그를 남기는거 (요청을 정상적으로 처리해주기도 함)
- 모든 프로세스는 최소 1개의 쓰레드 보유
- 프로세스는 집같은 존재고, 실제 실행은 쓰레드가 한다
- 프로세스끼리는 double linked list로 구현되있다
- 프로세스는 숨길 수 있어도 쓰레드는 스케쥴링에서 계속 실행되고 있기때문에 탐지 가능
- disk의 최소단위: sector, memory의 최소단위: page
- sector 최소 단위: 512KB

- IA-32 Register: AX(16bit), EAX(32bit), RAX(64bit)
- reversing할려면 assembly 알아야 좋음

- 컴퓨터는 기본적으로 논리연산 기반으로 작동하므로 논리관련(AND, XOR...) 연산이 수칙연산(PLUS, SUB...)보다 빠름 (수칙연산은 논리연산의 합으로 만들어지므로)
- 16진수로 보는것에 익숙해지면 좋음 (2개의 16진수 = 1byte)

- 엔디안: intel과 최근(M1) MAC은 리틀엔디안, 모토로라과 네트워크는 빅엔디안 (그래서 intel cpu에서 네트워크 관련 다룰 때 엔디포인트에서 엔디안 변환 필요)

**OPCODE 분석**  
프로그램 사용하면 더 편하게 가능

1. 2진수 코드 얻기
```
0101 0011 0110 1010 0111 0000 0110
1000 1001 1000 0001 1000 0000 0000
0000 0001 0011 0011 1101 1011 1000
1011 0100 1000 0011 1100 1000 0001
0011 1001 0111 1000 0101 0110 0011
0100 0001 0010 …
```
2. 16진수로 변환
```
53 6A 70 68 98 18 00 01
33 DB 8B 48 3C 81 39
78 56 34 12 ….
```

3. 해당 CPU의 OPCODE MAP에서 opcode찾으면서 해석
```
53: PUSH EBX -> 까먹음(code map에서 세로축에서 `5`를 찾고, 가로축에서 `3`을 찾아서 opcode를 찾고 opcode가 args를 가지면 해당 것들을 뒤도 분석한다)
6A 70: PUSH d64 Ib -> 바로 뒤에 나오는 arg 1byte를 stack에 push
...
```

- 파일은 PE(Portable Executable)와 Non-PE로 구분
> - PE: 실행파일 자체 (exe, dll, com, sys, scr)
> - Non-PE: 실행파일이 해당 파일을 여는 파일 (jpg, txt, bat, doc)

- 32bit -> 64bit로 업그레이드 되어도 호환성을 위해 ms와 intel은 int를 여전히 4byte로 하기로 함
- 각 Non-PE 파일은 자신을 실행할 파일을 선택하기 위해 파일 head에 magic string을 붙임
> 예. 아무 파일을 메모장에 드래그 앤 드롭하면 앞에 MZ, PK 등 있음

- PE파일을 메모리에 로드된 떄와 disk에 로드된 때 메모리 주소들이 다름 (메모리 최소 크기 단위는 page(보통 4096bytes), disk 최소 크기 단위는 sector(512bytes) 이므로 메모리가 더 부피가 크게 주소가 설정되어 있음) 


## 도구
- [PEview](http://wjradburn.com/software/): PE 프로그램을 binary, hex값으로 볼 수 있음
- [ollydbg](https://www.ollydbg.de/): 디버깅, 스택 관련 reverse engineering
- [peframe](): 
- [virustotal](): 