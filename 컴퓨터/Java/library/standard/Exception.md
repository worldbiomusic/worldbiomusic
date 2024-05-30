---
title: "자바 라이브러리: Exception"
date: 2020-01-01 00:00:00 +09:00
categories: [컴퓨터, Java]
tags: [Java, library]
---

# Exception
- 예외
- 프로그램에서 예상치 못한 문제가 발생될 때
- `throws new Exception()` 문법으로 해당 메서드 호출하는 메서드에게 위임 가능 (하지만 자체 메서드에서 해결할 수 있는것은 최대한 해결해야 함)
- 더욱 프로그램을 안정되게 만듬
- 큰 프로그램 또는 상용 프로그램에는 필수

## Error vs Exception
![image](https://user-images.githubusercontent.com/61288262/161577981-2d1fc958-b084-4c1b-8416-9d40f8a70712.png)
- Error: 발생하면 처리할 수 없음 (프로그램 중단됨)!
- Exception: 발생해도 처리코드(try-catch 문)가 있으면 처리 가능 

## Exception 종류
![image](https://user-images.githubusercontent.com/61288262/161577906-1faeb3f2-ef5e-44a8-80a4-bf351b46b7e5.png)
- Checked exception: 단순히 Exception을 상속, (compiled exception으로도 불림), IDE에서 체크 됨
- Unchecked exception: RuntimeException 을 상속함, IDE에서 체크 불가능, 실행중에 발생

---

# Fields
- 없음


---

# Methods

## `getMessage()`
- 에러의 내용만 출력


## `toString()`
- 에러의 내용과 원인 출력


## `printStackTrace()`
- 에러의 원인과 이유와 발생근원지를 역순으로 출력 (클래스 + 메서드)


- 코드
```java
public class TestMain {
	public static void main(String[] args) {
		try {
			int a = 1 / 0;
		} catch (Exception e) {
			System.out.println(e.getMessage() + "\n\n");
			System.out.println(e.toString() + "\n\n");
			e.printStackTrace();
		}
	}
}
```

- 결과
```
/ by zero


java.lang.ArithmeticException: / by zero


java.lang.ArithmeticException: / by zero
	at test.wbm.TestMain.main(TestMain.java:6)
```


---

# 예외 만들기
- compile vs runtime
```java
public class TestMain {
	public static void main(String[] args) {
		// compile exception은 강제적으로 try-catch 처리
		// 보통 시스템에 크리티컬한 예외
		try {
			compileException();
		} catch (MyCompileException e) {
			e.printStackTrace();
		}

		// runtime exception은 처리 선택 가능
		runtimeException();

	}

	static void compileException() throws MyCompileException {

	}

	static void runtimeException() throws MyRuntimeException {

	}
}

class MyCompileException extends Exception {

}

class MyRuntimeException extends RuntimeException {

}
```

- 커스텀 예외 만들기
```java
public class TestMain {
	public static void main(String[] args) {
		try {
			throw new MyCompileException();
//			throw new MyRuntimeException();
		} catch (Exception e) {
			System.out.println(e.getMessage() + "\n\n");
			System.out.println(e.toString() + "\n\n");
			e.printStackTrace();
		}
	}

}

class MyCompileException extends Exception {
	public MyCompileException() {
		super("컴파일 예외 메세지");
	}
}

class MyRuntimeException extends RuntimeException {
	public MyRuntimeException() {
		super("런타임 예외 메세지");
	}
}
```
```
런타임 예외 메세지


test.wbm.MyRuntimeException: 런타임 예외 메세지


test.wbm.MyRuntimeException: 런타임 예외 메세지
	at test.wbm.TestMain.main(TestMain.java:7)
```
---

# Ref
- [lnsideout](https://lnsideout.tistory.com/entry/JAVA-etoString-egetMessage-eprintStackTrace-%EC%98%88%EC%99%B8%EC%B2%98%EB%A6%AC)
- [toneyparky](https://toneyparky.tistory.com/40)
- [docs](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/lang/Throwable.html)

- 예외 만들기  
> - [devbox](https://devbox.tistory.com/entry/Java-%EC%98%88%EC%99%B8-%EB%A7%8C%EB%93%A4%EA%B8%B0)
> - [staticclass](https://staticclass.tistory.com/72)
> - [stackoverflow](https://stackoverflow.com/questions/2190161/difference-between-java-lang-runtimeexception-and-java-lang-exception#:~:text=Exceptions%20are%20a%20good%20way,errors%20for%20them%20to%20compile.)



