# 요구 모델링
- 문제영역(요구사항)의 솔루션(고객과 개발자의 합의)을 명세화 해놓는 것 

# 5.1 모델링 기초
- 프로젝트의 스케치 (추상화 or 단순화)
- 하는 이유: 최소한의 동작하는 것들을 만들어봐서 고객과 개발자 간의 합의하에 프로젝트를 명세화
## 구조적 설계
- 시스템을 이루는 모듈을 구조적으로 작성하는 방법 (기능 중심)
- Functional Decomposition(함수 분할) + Design Criterion(cohesion, couple 기반 디자인) + Design Heuristics(경험 기반 디자인)
- 데이터 흐름에 중점 (변환분석(입력값이 함수 내부에서 바뀌고 출력되는 것), 처리분석)
- 모듈간의 결합도는 낮게, 모듈 내부의 응집도는 강하게
- 시스템 구조도는 각 노드가 공평하게 비슷한 자식노드를 가져서 전체노드가 둥글게 되야 유지보수가 좋음
## 객체지향 설계
![image](https://user-images.githubusercontent.com/61288262/163580521-33b21fef-b6bb-4957-9dde-22ae90502466.png)
- 자료와 관련 함수의 결합
- `use case diagram`에서 시작해서 `class diagram`으로 끝나는것이 목표
- 객체 = 클래스의 인스턴스
- 프로그램은 단계적으로 세분화해서 구성해야 빈틈없이 탄탄하게 기반이 갖춰짐
- 상속, 다형성, 캡슐화

# 5.2 UML
- Unified Modeling Language: 하나의 표준으로 통합된 그래픽 언어
- 객체지향 모델링 기반
- 개발 모형: 기능적, 정적(객체 모형이라고도 함, 시간에 영향을 안 받음), 동적(시간에 영향을 받음)



# 5.3 정적 모델링
- 클래스 간의 관계 모델
- 시간의 개념이 없음
> 예. 클래스 다이어그램  
- 구현 없이, 변수, 함수의 헤드만 정의

# 5.4 동적 모델링
- 시간의 흐름에 따른 모델
> 예. 인터랙션, 상태, 액티비티 다이어그램(순서도와 비슷)


<!-- # 5.5 제어 모델링
PPT 내용 x
# 5.6 모델 검증 -->

---

# Q&A
1. 모델링을 하는 이유
> 최소한의 동작하는것들을 만들어보아서 고객과 개발자간의 합의하에 프로젝트를 명세화하기 위해
2. 구조적 설계
> 함수 위주의 모듈을 구조적으로 작성하는 방법 (예. C언어)
3. 다음 시스템 구조도를 프로그램으로 변환
![image](https://user-images.githubusercontent.com/61288262/163586585-b87c1468-bd19-4801-bcad-8058b9cfdf6a.png)
4. 객체지향의 3가지 관점의 모델 도해
> 기능적, 정적, 동적
5. 객제지향 분석의 설계과정
> 명확한 방식은 없지만, 주로 use case diagram -> class diagram의 방식을 사용
6. 구조적 방법과 객체지향 방법 도해
![image](https://user-images.githubusercontent.com/61288262/163587135-e4fdede5-20dd-49b6-9844-a92d9c89c664.png)
7. use case, class, sequence 상태 다이어그램 간단하게 그려보기
![use case](https://user-images.githubusercontent.com/61288262/163587729-720a812a-3025-49e0-aead-8b3109d24b35.png)
![class](https://user-images.githubusercontent.com/61288262/163587808-7cf27555-8bfa-4cb5-b9e7-92683dc90a51.png)
![sequence](https://user-images.githubusercontent.com/61288262/163587650-0cb0b228-3036-47a9-ae8b-fe9fc4d54145.png)


---

# 유튜브
## [시나공 정보처리기사] 401504 객체지향 프로그래밍 언어의 구성 요소
- 객체지향의 요소: 객체, 클래스, 메세지
- 객체: 자료(속성)와 함수(메서드)를 결합시킨 실체
- 클래스: 객체의 유형 (틀과 비슷한 개념)
- 메세지: 객체간의 상호작용의 수단 (예. 메서드)

## [시나공 정보처리] 1407300 객체지향
- 객체지향 소프트웨어: 각 요소을 객체로 만든후, 조립해서 소프트웨어를 개발하는 방법
- 구조적 기법의 문제법을 재사용성 등의 경제적인, 유지보수가 쉬운 방법으로 해결한 방법
- 특징: encapsulation, inheritance, polymorphism, relationship
- instance: 클래스에 속한 각각의 객체를 지칭
- encapsulation: 접근을 제한해 인터페이스만 제공해서 세부내용을 은닉 (변경에 강함)
- inheritance: 하위 클래스가 상위 클래스의 속성, 연산을 물려받는 것
- polymorphism: 하나의 클래스를 상속해서 다양한 객체가 각각의 고유한 방법으로 사용할 수 있는 방법
- relationship: 2개 이상의 객체들이 상호참조하는 관계

## [시나공 정보처리] 1401200 UML다이어그램
- diagram: 사물간의 관계를 도형으로 표현한 것
- 소프트웨어를 뷰로 제공해서 더욱 이해가 잘되고 의사소통 하는데 좋음
- 구조적: class, object, component, deployment, composite structure, package
- 행위: use case, sequence, communication, state, activity, interaction, timing 
- stereotype: 추가적인 기능 표현 (`<<>>` 사용 e.g. `<<interface>>` ... )

## 소프트웨어 설계 언어 한방에 부수기 - UML
- UML: 시스템, 업무, 모델링, 산출물을 표현하는 시각적 언어
- 구조, 행위 다이어그램으로 나뉨
- 관계에 따라서 표기법이 다양함

## [시나공 정보처리] 1401800 상태 다이어그램
- 객체들의 이벤트에 의해 변하는 객체의 상태변화의 그림
- 상태변환 과정의 흐름을 표현
![image](https://user-images.githubusercontent.com/61288262/163590168-5eb057e0-1dd9-4367-be9d-b054321023d1.png)

## [시나공 정보처리] 1401600 시퀀스 다이어그램
- 동적 모델링: 시스템의 내부 구성 요소의 상태변화의 상호작용을 표현
- 시퀀스 다이어그램: 객체들이 상호작용 과정을 그림으로 표현한것
- 수행기간, 메세지, 상호작용을 그림으로 쉽게 파악 가능

## [시나공 정보처리] 1401400 활동 다이어그램
- 사용자 관점에서 시스템이 수행하는 기능의 흐름 표현
- 자료 흐름도와 유사(유즈 케이스의 흐름)
- 알고리즘 처리도와 비슷함


## 정보처리기사 필기 1과목. 소프트웨어 설계_구조적 개발 VS 객체지향 개
- 구조적 개발: 모듈 기반 (장점: 구조가 단순해서 이해, 수정, 정확, 단점: 재사용, 유지보수 어려움)
- 객체지향 개발: 객체 기반 (장점: 재사용, 유지보수 향상, 단점: 객체간의 관계가 너무 얽히면 수정에 복잡해 짐)
- 소프트웨어 위기: 소프트웨어의 대형화


## 절차지향과 객체지향이란?
### 절차지향
- 일련의 처리 절차를 정해진 문법에 따라 순서대로 실행하는 방법
- TOP-DOWN 접근 방식
- 코드가 순차적으로 진행
- 장점: 빠름, 적은 개발비용
- 단점: 디버깅, 변경의 어려움
### 객체지향
- 독립적인 서로 다른 객체들의 상호작용, 실세계를 모델링
- 특징: 추상화, 캡슐화, 다형성, 상속
- 장점: 생산성, 유지보수, 재사용성 좋음
- 단점: 초반의 개발에 많은 비용 요구