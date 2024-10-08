# 설계 원리
- 설계 원리는 소프트웨어공학뿐만 아니라, 다른 분야데도 넓게 적용시켜서 생각해볼 수 있음
---

# 6.1 설계 기본 개념
- 요구분석: 무엇(what)을 만들 지
- 설계: 어떻게(how) 만들 지 
```yaml
- 기본설계(상위설계): 아키텍쳐 설계
- 상세설계(하위설계): 내부 알고리즘, 데이터
```
- 요구 분석 한것을 토대로 기술적으로 구현하기위해 시스템 구조를 만드는 것
- 문제에 설계 원리와 제약조건들을 만족시키는 작업

## 상위 설계
- 상위: 아키텍쳐 (클래스간의 상호작용), UI, 데이터, 인터페이스, 시스템
> 예. 구조도 설계
## 하위 설계
- 하위: 모듈 구조(클래스 구조), 알고리즘, 자료구조
> 예. 모듈 알고리즘 코딩
# 6.2 품질 목표



# 6.3 전통적인 설계 원리
## `효율성`(efficiency)
- 처리 시간, 기억 공간 (요즘은 H/W가 많이 발전함에 따라 특정 경우를 제외하고는 비중이 단순성으로 더 커짐)

## `단순성`(simplicity)
- 명작의 필요조건은 단순성이다
- 간단할 수록 미래에 유지보수, 사용성이 좋음

## `분할화`(계층화)
- 큰 문제를 작은 문제로 분할(구체화)해서 해결하는 방식
- 분할정복 기법

## `추상화`
- 특정한 것에 대해서 간단하게 표현하는 것
- 종류: 기능, 자료, 제어
- `추상화`: **_현실_ 객체들의 공통점을 추출해서 만드는 클래스 틀**
- `인스턴스화`: **_자바_의 클래스로부터 객체를 생성하는 과정**

## `모듈화`
- 프로그램을 `작고`, `독립적`인 모듈로 분할하는 것 (모듈: 독립적으로 동작하는 단위)
- **모듈 내부의 높은 응집도(cohesion)**
- **모듈 간의 낮은 결합도(coupling)**
- 모듈이 작을 수록 재사용성이 높다
- 모듈이 클수록 사용성이 좋다 (세부작업을 알아서 처리해주므로)
- 모듈의 크기는 프로그램의 특성에 알맞게 알맞은 크기로 구성되야 좋다

## `캡슐화`
- 추상화된 것의 필요한 정보만 노출
- 정보 은닉(information hiding)
- Java에서는 접근제한자로 설정됨

# 6.4 객체지향 설계 원리
- 모듈의 조합으로 시스템을 만드는 아키텍쳐 기반 설계 방법을 사용
- 아키텍쳐: 시스템들을 모아서 설계하는 방식
- 컴포넌트 < 서브시스템 < 시스템


# 6.5 설계 매트릭
- pass

---

# Q&A
1. 아키텍처 설계와 상세설계를 설명하세요
> 아키텍쳐 설계: 상위설계로 전체적인 시스템을 설계하는 것  
> 상세 설계: 하위 설계로 각 프로그램의 알고리즘과 같은 구현부분을 제작하는 것  

2. 설계의 원리를 나열하고, 각각을 간단히 설명하세요
> 효율성: 처리 시간과 공간을 적게 들일수록 비용이 적게들어 효율적  
> 단순성: 단순해야 사용하기 쉽고, 유지보수에 좋다  
> 모듈성: 각 부품을 모듈화해놓아야 재사용에 좋다  
> 추상화: 핵심적인 특징 위주로 인터페이스 설계로 개발, 유지보수에 좋음  
> 캡슐화: 필요한 정보만 보여줘서 사용성, 보안성에 좋음  
> 분할화: 큰 프로그램을 작은 문제로 쪼개서 해결하는 방식(분할-정복)  

3. 추상화와 인스턴스화를 설명하세요
> 추상화: 현실세계의 객체들의 특징을 토대로 틀(클래스)를 만드는 것  
> 인스턴스화: 자바세계(개념적)의 클래스 틀을 토대로 객체를 만드는 것  

4. 모듈이란?
> 크기와 상관없이 독자적으로 기능을 할 수 있는 단위  

5. 추상화, 캡슐화, 모듈화를 구분하여 설명하세요
> 추상화: 핵심 특징(인터페이스)만 설계  
> 캡슐화: 핵심 정보만 노출시켜 이용  
> 모듈화: 각 부품을 재사용 하기 쉽게 적절한 크기로 모아놓은 것  

6. 시스템, 서브시스템, 컴포넌트, 모듈을 구분해보세요
> 모듈: 크기와 상관없이 독자적으로 기능을 할 수 있는 단위 (컴포넌트, 서브시스템, 시스템 모두 모듈이라고 할 수 있음)  
> 컴포넌트: 서브시스템을 구성하는 단위(**자잘한 것**)  
> 서브시스템: 시스템을 구성하는 단위(**확실한 기능을 가지는 것**)  
> 시스템: 일련의 일을 범용적으로 처리하는 단위  

---

# 유튜브
## 6분 만에 알려주는 소프트웨어 제작 과정
- 컴퓨터는 기계어로 동작
- 소프트웨어 엔지니어는 기계어로 바꿔주는 프로그래밍 언어로 작성
- 프로그래밍 언어는 컴파일러 또는 인터프리터로 기계어로 바꿔줌
- 큰 프로젝트는 버전관리 도구를 사용해서 관리
- 디버깅등을 통해 오류 수정

## 개발자가 프로그램 설계 잘해야 하는 이유와 방법
- 설계는 `개발자의 생각`의 직접적으로 반영되는 부분
- 주로 경험의 양과 설계의 좋은 정도는 비례함
- 설계: `이상적인 설계` + `현실적인 제약(기술, 고객)`
- 소프트웨어의 완성도는 `설계`에 영향을 많이 받음
- 관련 키워드: 인터페이스, 설계, 리팩토링, 디자인패턴, 크로스 플랫폼

## 개발자가 실제로 하는 일은 뭘까?
- 기획, 개발, 테스트, 배포, 유지보수
- 공학이므로 `이론`만이 중요한것이 아니므로, 실제 소프트웨어 제작환경에 맞춰서 제작하는것이 적당함

## 지방대 개발 비전공자가 배달의민족 리드 개발자가 되기까지
- 꾸준함은 좋은 무기
- 현대의 시스템들은 빠르게 변화하므로, 애자일같은 방식의 빠른 생산성을 위해서 주변 동료와의 피드백 핑퐁도 좋다
- 목표도 좋지만, 일단 시작해보면서 중간중간에 얻는 방식도 괜찮다

## SW 설계서 작성가이드
- 구조 설계: 상위 설계, 상황에 따라서 H/W까지도 고려할 수도 있음
- 시퀀스 다이어그램: 객체간의 상호작용을 시간흐름에 따라 나타낸 것

## 프로그래밍에서 추상화 개념 완벽 이해하기!(ft.자바스크립트)
- 추상화(abstraction): 여러사물이나 개념에서 공통적인 `특징`, `속성`을 파악해서 `복잡한것`을 `목적`에 맞게 `단순화`하는 것 (간단하게는 요약, 단순화한것)
- 대화에서도 표현에 필요한 것
- 소프트웨어에서는 `자신, 컴퓨터, 다른 개발자, 사용자`간의 소통이라고도 볼 수 있음

## [SW공학 동영상 10화] SW 아키텍처 설계예시편_Part 1
![image](https://user-images.githubusercontent.com/61288262/163824226-66f134ae-1380-4a08-ae02-4bd03c3975e7.png)
- 수강 신청 시스템 예시
- 소프트웨어 제작 순서: 명세서 -> 기능 모델링 -> 비기능 모델링 -> 아키텍쳐 설계 -> 제작 -> 아키텍쳐 평가 후 다시 설계
- 소프트웨어와 관련된 고객 파악이 중요
- 기능 요구사항은 너무 세부적까지 가지 않고 설계 중심으로 제작
- 실제 소프트웨어를 제작할 때는 `비기능` 요소를 선별하는것이 중요
- 설계에 있어서 최소한의 절대적인 `수치`는 있는것이 좋음
- 설계는 경험에서 좋은 전략이 많이 우러나옴

## 정보처리 실기 | 06. 소프트웨어 설계의 기본원칙
- 설계: 요구 명세서를 참조해 구체적인 설계서를 작성하는 단계
- UML과 같은 이해하기 쉬운 그림같은 도구를 사용하면 좋음
- 협약에 의한 설계: 각 클래스에 대해 특징을 정해두는 설계 (예. 선행조건, 결과조건, 불변조건)