# 자바 책
- 단순한 자바 문법책이 아닌, 실제 사용될 수 있는 기법들을 배워보는 책

# 설명
- 언어: 인간이 컴퓨터에게 전달하는 언어 (컴퓨터는 특정한 언어만 알아먹을 수 있기 때문에)
- 언어를 배우는 이유: 초기에는 컴퓨터는 계산을 위한 도구였지만, 시간이 지나면서 실생활의 여러 다양한 문제들을 해결하기
위해서 

| C | Java |
| - | ---- |
| 절자지향 | 객체지향 |
| 빠른 속도, 효율성 | 플랫폼 독립적, 생산성 |

- 현대는 하드웨어가 많이 발전해서 요즘은 Java가 많이 쓰임

# 자바 특성
- 자바는 클래스들의 모임이고 클래스는 데이터와 메서드의 모임이다, 이러한 클래스가 모여서 자바프로그램을 구성한다
- 사용법: 클래스 틀 제작 > 클래스 인스턴스 생성 > 인스턴스 사용
- 자바 구성요소

| Application |
| - |
| API |
| JVM |
| OS |
| H/W |

- API: Application Programing Interface (라이브러리에서 제공하는 책 같은 것)
- 자바는 기본 라이브러리들을 제공해서 우리가 사용함
#### 플랫폼 독립성
- Java: JVM이 각 OS나 HW에 대한 상황을 미리 처리해놓았기 때문에 Java가 플랫폼 독립적으로 동작할 수 있음 (하지만 JVM은 각 
환경에 맞게 제작되어야 하므로 플랫폼 종속적)
- C: 각 운영체제, HW에 맞는 컴파일러를 사용해서 실행파일을 실행해야 하므로 플랫폼 종속적이다
---
- java실행 과정: .java > javac로 컴파일 > .class 생성 > jvm(interpreter, JIT)이 bytecode를 실행시킴

# JDK
- JDK(Java Development Kit): 자바 개발 관련 도구
- JRE(Java Runtime Environment): 자바 실행 관련 도구
- 요즘은 JDK를 다운로드 받으면 JRE이가 JDK안으로 같이 배포됨
- `bin`: binary의 줄임말 (실행가능한 파일) (보통 env path로 등록시켜서 사용)
- `include`: 프로그램에서 포함할 파일
- `lib`: 자바 기본 라이브러리들 (예. jrt-fs.jar(Java Run Time File System) 에 들어있는 기본 libs)
- Java SE(Standard Edition): 

# IDE
- Integrated Development Environment
- 통합 개발 환경
- 주로 Eclipse, IntelliJ 사용
## Eclipse
- font 변경, perspective view 등의 자신에 맞게 적용해서 사용하는것이 좋음
- ctrl + spacebar: 목록 추천
- ctrl + shift + R: class이름으로 찾아서 열수 있음 (Type 또는 Resource)
- ctrl + H: 검색 기능 (주로 File, Java)

---

# 2. 프로그램 작성
- 문법만을 배우는것이 아닌, 프로그램을 잘 만들 수 있는 방법들 위주로 배움

# 프로젝트 구성
- Workspace: project들을 모아놓은 공간
- Project: src내의 Pakcage를 모아놓은 공간 
- Package: java파일을 모아놓은 공간
- src: 소스파일(java) 모아놓은 공간
- bin: 실행파일(class) 모아놓은 공간 (eclipse가 자동 생성)
- workspace는 기본적으로 `eclipse-workspace`라고 만들어져 있음
- `프로젝트`: 시작할 것들이 있고, 끝 지점이 있는 기간내에 주어진 일을 마치는 것

## 중요한 것
- **`package`, `public class`, `public static void main` 등은 초반에 외워놓아서 사용하는것이 좋음 ** (시험)
- eclipse에서 run버튼을 누르면 java파일을 class파일로 컴파일해서 만들어준 후, jvm이 실행까지 시켜준다


# 컴파일러
- javac.exe: java파일을 java파일을 class파일로 변환해주는 도구
- java.exe: jvm을 실행해서 class파일들을 실행시켜주는 도구
- 컴파일러는 컴퓨터가 이해하는 언어이기 때문에 사소한 것이라도 규칙에 어긋나면 안된다
- 런타임 에러: RunTimeError: 컴파일러가 잡아내지 못하는 오류로 무조건 실행시켜봐서 실제 동작에 나오는 에러를 확인할 수 밖에 없다 (예. divide by zero)

# 클래스
- package는 class들이 포함된 디렉터리 구조를 나타내고, import할 때 편하게 찾을 수 있는 기능이다
- static이 붙은 메서드나 변수는 클래스의 인스턴스를 만들지 않아도 사용가능한 것이다 (예. 자바 프로그램을 외부에서 실행하기 위해 쓰이는 `public static void main()`)
- public class는 java파일의 이름과 같은 이름으로 선언되어야 하고, 하나의 java파일에는 1개만 존재해야 한다

# 주석
- `//`: 1줄 주석
- `/* */`: 블락 주석
- `/** */`: 요소 주석
- 주석은 코드와 함꼐 설명이므로 거의 필수적으로 필요하지만, 또 너무 많으면 혼란스럽기 떄문에 적절하게 사용해야 한다

# 출력
- `System.out.print()`: 출력만 한다
- `System.out.println()`: 출력과 마지막 줄바꿈을 한다
- 자바는 `+` 연산자를 이용해서 문자열들과 문자열들이 아닌것들도 같이 연결해서 출력할 수 있다
```java
package hello;

```

# 변수
- 수학의 변수와 같은 여러 값을 가질 수 있는 것
- 수학의 정의역은 자바에서는 타입이라고 볼 수 있다
- 내부는 변수는 사실 메모리 주소를 가리키는 껍데이이고, 해당 메모리 주소에 값을 저장하는 것이다
- `=`는 자바에서 오른쪽에 있는 값을 왼쪽의 변수에 저장하라는 뜻
- 변수는 항상 어떤 값을 소지하고 있어야 한다 (안그러면 오류 발생)
- 변수명은 변수를 가장 잘 소개해줄 수 있는 이름으로 작성
## 선언
- <타입> <변수명> = <값>
- 타입에 맞는 값만을 할당할 수 있다
- 타입을 사용하면 변수를 여러군데에서 사용할 때 헷갈리지 않는 효과도 준다
- `변수` vs `필드`: 변수란 메서드 내에서 생성되는것은 메서드를 탈출하면 바로 사라지기 때문에 변수라하고, class의 변수는 class의 instance가 존재하는한 같이 있기 때문에 필드라고 부른다












