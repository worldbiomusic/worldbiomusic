# 타입 변환 (Casting)
- primitive type 순위: byte > short, char > int > long > float > double
- 큰 타입 기준으로 연산됨

## up-casting
- widening이라고도 부름
- super class로 타입 변환
- 자동으로 이루어짐

### 예시
- `10 / 3 = 3`: (정수를 정수로 나누기 때문에 소수점은 생략)
- `10.0 / 3 = 3.333333...`: 실수(double)가 정수(int)보다 윗 타입이므로, 자동 up casting 되서 결과값이 실수로 나옴)
- `1 + "반가워" = "1반가워"`: `+` 연산자는 문자열이 피연산자로 있으면 다른 값들을 모두 문자열로 변환하여 결과를 내보낸다
- `'a' + 'b' = 195`: char 타입을 + 연산자로 연결하면 유니코드의 값이 더해져서 결과가 나옴

## down-casting
- narrowing이라고도 부름
- sub class로 타입 변환
- 명시적으로 선언해줘야 함
- 데이터 손실이 발생할 수 있음

### 예시
- `int a = (int) 1.5`: a변수에는 1.5(double)의 값이 down-casting되면서 1(int)로 들어간다 (int는 소수점을 관리하지 않기 때문)


# 증감 연산자
- `++x`: 선 증가후 사용
- `x++`: 사용 후 증가
- `--x`: 선 감소후 사용
- `x--`: 사용 후 감소


# 비교 연산자
- 수학과 비슷함 (등효(=)가 오른쪽에 쓰는것만 다름)
> 예. `<=` = `≤`

# 논리 연산자
- AND, OR, NOT 과 같은 논리 연산자 지원
> 예. AND = `&&`, OR = `||`, NOT = `!`


# 연산자 우선 순위
- 증감 > 산술 > 관계 > 논리
- 계산 일때는 왼쪽 > 오른쪽
- 대입 일때는 오른쪽 > 왼쪽
- 하지만 괄호(`()`)로 묶어 놓는것이 가독성에 좋음


# 식(expression) vs 문(statement)
## 식
- 변수 또는 상수 같이 값을 가지는 것
- 메서드는 문으로 볼수도 있지만, 값을 리턴하는 메서드는 값을 가지므로 식으로 사용될 수 있다
- 뒤에 `;`를 붙이면 식문(expression statement), 즉 해당 식을 실행하는 명령어가 된다
## 문
- 명령어
- 뒤에 `;`를 붙인다
> 식문 (expression statement)  
> 선언문 (declaration statement)  
> 제어문 (control statement)  
> 블럭문 (block statement)  


# 입력
- Scanner class를 사용
- 생성자 인자로 input stream 값을 System.in (기본: 키보드)로 넣어줌
- 기본적으로 `next()`기반 메서드는 공백(` `)을 기준으로 문자열을 token으로 나누어서 입력받음
## Enter의 효력
- enter키는 윈도우에서는 `\r`와 `\n`이 동시에 입력 됨
- `\r`: 커서를 줄 맨 앞으로 이동
- `n`: 공백줄 삽입 (줄 내림)



# Import
- 사용할 class의 경로명을 적어두면 코드 내에서 사용할 때 클래스 이름만 적으면 사용 가능
> 예. `import java.util.Scanner`, `import java.util.*`
- `java.lang` 패키지는 자동 import 됨







# 정리
- 문법을 외워서 배우지 말고, 프로그래밍 하는 **방법**을 배워야 실질적으로 사용할 수 있다
- 실제로 편집기에서 코드를 많이 실행해보면서 익혀야 한다



