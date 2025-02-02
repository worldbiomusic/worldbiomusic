# 상수 선언
- final: 앞으로 변경 불가
- 선언할 때 초기화하지 않으면, 나중에 딱 `1`번 초기화 가능
- `final int a = 1`: 앞으로 변수 a는 변경 불가 (상수로서 사용)
- 영어: `대문자`와 `_` 로 사용
- 한글: 뒤에 `_상수` 사용
- 변수를 상수로 바꿔주는 문법
- 변경될 수 없는 기억장소

## 수학과의 차이점
- 수학에서의 상수를 자바에서는 리터럴(literal)이라고 부름 (데이터 덩어리를 다르게 부르는 것)

## 상수값 vs 변수 vs 리터럴 
- 상수: final 로 선언된 변수
- 변수: 값이 변할 수 있는 그릇
- 리터럴: 값 자체 (예. 1, "반가워", `잉`) (리터럴도 타입으로 나뉨)

# 출력
## println(): 문자열을 출력하고 한줄 내림
## printf(): 문자열 사이에 `%`으로 값을 매핑할 수 있음
- %b: 논리
- %c: 문자
- %d: 정수
- %f: 실수
- %s: 문자열
- 대문자로 사용하면 대문자로 출력
- `%n.m`: 전체 n자리를 출력하고(n자리 값을 넘으면 넘은만큼도 다 출력됨), m자리만큼만 값을 출력(소수점은 없으면 0으로 바뀜)

## 특수문자
- 특수한 기능을 가지는 문자
- \b: backspace
- \t: tab
- \n: line feed
- \f: form feed
- \r: carriage return
- \": double quote
- \': single quote
- \\: backslash

## 예시
```java
System.out.println("학번: " + 학번 + " 학년: " + 학년);
System.out.printf("학번: %s 학년: %d", 학번, 학년);
```

# 타입
- 수학에서 정의역과 개념이 비슷 (각 타입은 변수가 가질 수 있는 값을 정해주는 역할)
- 내부적으로는 메모리의 기억장소의 크기(byte단위)를 정해주는 역할
- **타입에 따라 `값`과 `연산`을 규정**

## 종류
- boolean: 1byte
- char: 2byte
- byte: 1byte
- short: 2byte
- int: 4byte (기본 정수)
- long: 8byte (뒤에 `l`또는 `L` 붙여야 함)
- float: 4byte (뒤에 `f`또는 `F` 붙여야 함)
- double: 8byte (기본 실수)

### 문자
- 자바는 기본적으로 문자를 unicode로 인코딩
- 양수 값으로 이루어짐
- '\u{unicode(hex)}'로 표현가능 (예. '\uAC00' = '가')

### 문자열
- java.lang.String 클래스 타입
- 자바에서 특별한 위치
- 클래스이지만 `""`으로 객체 생성 가능
- 문법적으로 `+` 연산자를 오버로딩하는 클래스
- 문자열은 예외적으로 성능을 위해 같은 값(문자 배열의 값)을 가지게 되면 String pool의 같은 참조 주소를 가리켜서 사용 (new로 만들면 heap memory에 다른 객체로서 생성됨)
- 문자열은 클래스이므로 다양한 문자열 처리 관련 메서드를 제공함


# 식별자 (identifier)
- 이름을 붙이는 것
- 다른 문자 지원 (예. 한글) (**기능적으로 다른 문자도 사용할 수 있게 지원하는것이므로 굳이 영어쓸 필요없음! (배울 때 오히려 독이 될 수 있음)**)
- 띄어쓰기 불가
- 대소문자 구별
- 길이 제한 없음
- 문자로만 시작
- 예약된 키워드 사용 불가
- 의미있는 이름을 지어줘야 함 

## 관례
- 클래스: 대문자로 시작
- 변수, 메소드: 소문자로 시작 (camelCase 방식)
- 상수: 대문자로 구성 (`_`로 구분)




# 정리
- 무조건 외우지 말고 필요할 때 참조하는 방식으로
- 한글 사용 (변수, 메소드, 클래스 등을 자바에서 기능적으로 다른 문자로 쓸 수 있게 지원을 하는데도, 영어권의
 방식을 고집하면서 영어로만 쓰는것은 바람직 하지 못함) (자국어의 힘이 코드에서 약해지는 효과를 가져오게 됨)










