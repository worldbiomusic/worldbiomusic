# 아키텍쳐와 패턴
- 뼈대

# 7.1 아키텍쳐 기초
- 소프트웨어의 기본 설계
- 하나의 디자인으로도 볼 수 있음
- 소프트웨어공학의 각 단계를 대부분 설계
- 아키텍쳐를 설계하면 사용자, 개발자 등 상호간의 소통이 원활

## 4+1 관점
- 사물은 관점에 따라서 다르게 인식됨 (예. 개발자 vs 엔지니어)

- `유스케이스 관점`: 사용자 관점, 전체 아키텍쳐의 기반
- `논리적 관점`: 클래스(컴포넌트)간의 관계
- `구현 관점`: 모듈의 구조화
- `프로세스 관점`: 
- `배치 관점`: 




# 7.2 아키텍쳐 스타일
- 모델(스타일)은 아키텍쳐의 **핵심**만을 추출한 것 -> 의사소통, 시스템의 뼈대를 위한 것
- 모델의 적용은 각 상황마다 적절하게 적용되야 좋음 (예. 전체적인 모델은 p2p모델이지만, 세부 모델은 client-server 사용)

## client-server
- client: 사용자, server: 제공자
- 역할 위치는 절대적인 것이 아닌, 상황에 따라 상대적
- 분산 아키텍쳐 종류: 각 역할에 맞게 작업(데이터 전송 or 처리)을 분할하면 좋을 때 주로 사용
- `장점(장점이라기 보단 특징)`: 중앙화, 보안
- `단점`: 병목, 비용, 비강인성

## layering
- 기능을 수직으로 구분해서 계층상으로 작동하는 구조
- 각 층은 서로 메세지를 통해 소통 (소통은 인접한 층끼리만 소통 가능)
- `장점`: 추상화, 캡슐화, 응집도, 재사용
- `단점`: 각 계층은 인접한 계층끼리만 소통이 가능

## event-based
- 이벤트 발생 시점 기준으로 일을 처리하는 모델 (event handler)
- `장점`: 구조가 단순해짐
- `단점`: 이벤트 핸들러가 항시 대기해야 해서 리소스를 계속 사용해야 함

## MVC
- 중앙 데이터 구조
- 하나의 시스템을 여러 방식으로 사용할 수 있는 장점
- Model은 다양하게 사용되기 위해서는 일반적으로 제작되야 함
- `장점`: 디자인과 로직을 분리해서 모듈성 증가
- `단점`: 복잡도 증가, 속도가 상대적으로 느림(계층간의 소통이 많기 때문)

## pipe and filter
- 데이터가 `한 방향으로`만 흐르며 처리되는 구조 (layering모델은 양방향)
- 예. 컴파일러
- 장단점은 layering모델과 비슷

## repository
- 중앙화 데이터베이스 접근 방식

## p2p
- 각 위치가 동등한 노드간의 소통으로 운영되는 모델
- 대칭적 시스템

# 7.3 디자인 패턴
- 각 상황에 맞게 자주 사용되는 설계 형태를 정형화한 설계 패턴 (주로 경험에 기반해서 만들어진 것)
- 저비용으로 빠르게 만들 수 있음
- 아키텍쳐 설계의 `모듈`로서 사용하게 하기 좋은 것

## 장점
- 재사용
- 확실한 설계(OOP) 작업, 지식 
- 의사소통

## Singleton
- 어떤 클래스가 단 하나의 객체만을 가지도록 하는 패턴
- 생성자를 private으로 설정, 클래스를 정적변수로 설정

## Iterator
- 요소들을 동일한 인터페이스로 삽입, 삭제, 검색 등의 작업을 가능하게 해주는 패턴

## Adapter
- 서로 맞지 않는 부품들을 동일한 인터페이스를 사용해서 사용할 수 있게 만드는 것

## Factory
- 객체생성 을 메서드 혹은 클래스로 분리해서 캡슐화하는 패턴
- 객체생성에 중복되는 부분은 줄이고, 또는 옵션을 사용해서 다양한 객체를 생성가능

# 7.4 아키텍쳐 평가

---

# Q&A
1. 소프트웨어 아키텍처가 무엇인가?
> 소프트웨어의 각 모듈간의 관계 및 전체적인 구조

2. Client-server 모델을 설명하세요.
> 분산 아키텍쳐중 하나로, 제공자와 사용자로 나뉘는 구조 (역할의 위치는 상황에 따라 다름)

3. 계층형 모델을 설명하세요.
> 기능을 수직적으로 구분해서 계층간의 메세지를 통해 동작하는 구조
> 추상화, 캡슐화 등이 좋지만, 인접한 계층끼리만 소통이 가능한 단점

4. MVC 모델을 설명하세요.
> 중앙 데이터 구조로 하나의 시스템을 여러가지 방식으로 사용할 수 있는 설계
> Model: 데이터 관련, Controller: View, 데이터 처리 관련, View: user UI/UX 관련

5. 디자인 패턴이 무엇인가요?
> 각 상황에서 자주 쓰이는 패턴들을 정형화해 놓은 설계 디자인

6. Gof 디자인 패턴의 유용성을 도해하세요.
![image](https://user-images.githubusercontent.com/61288262/166875089-569dab78-4925-444e-aaf9-aa4b8613b826.png)

7. iterator 패턴이란?
> 여러 데이터를 동일한 interface로 loop를 돌면서 쉽게 접근할 수 있게 해주는 패턴
> 예. java의 Iterator<>

8. 팩토리 메소드 패턴이란?
> 객체생성 을 메서드 혹은 클래스로 분리해서 캡슐화하는 패턴
> 객체생성에 중복되는 부분은 줄이고, 또는 옵션을 사용해서 다양한 객체를 생성가능


---

# 유튜브
## 개발자 아키텍트 역할 차이 그리고 아키텍트가 되려면 (feat. 개발자에서 아키텍트로 도서 내용 중에서)
- 개발자: 세부적인 기능을 구현하는 사람
- 아키텍트: 전체 시스템 설계, 구조를 설계하는 사람

## [SW공학 동영상 5화] 소프트웨어 아키텍처 개론
- 일단 설계를 하는 주된 목적은 `크기` 때문
- 기간, 비용
- 작은 프로젝트에는 오히려 독
- SW아키텍쳐의 `뷰`(관점)을 여러가지로 분석하면 좋은 품질 가능

## 개발자 vs 엔지니어 | 프론트엔드 백엔드 차이 | front-end vs back-end
- 개발자: app제작하는 사람
- 엔지니어: app운영, 유지보수 하는 사람

## WEB1 - 17. 인터넷을 여는 열쇠 : 서버와 클라이언트
- web browser: 웹 리소스 요청자 (client)
- web server: 웹 리소스 제공자 (server)

## 웹애플리케이션 만들기 - 서버와 클라이언트
- server: 제공자
- client: 사용자 (browser)
- 기본적으로 client의 request에 대한 server의 response로 구성됨 
- Apache가 서버 sw로는 가장 많이 쓰임)

## 알아두면 좋은 디자인 패턴 (Design Pattern) [ 스프링 부트 (Spring Boot) ]
- 특정상황에서 공통적으로 쓰일수 있는(재사용가능한) 설계 디자인
- 디자인: 이미지쪽뿐만 아니라 설계 계념쪽으로도 쓰임
- 정적인것이 아니라, 각 상황에 맞게 변경되어 사용될 경우가 많음
- 패턴: 생성(객체 생성 관련), 구조(자료구조, 인터페이스 관련), 행위(객체사이의 관계 패턴 관련)
