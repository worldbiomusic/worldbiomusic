---
title: "자바 라이브러리: System"
date: 2020-01-01 00:00:00 +09:00
categories: [컴퓨터, Java]
tags: [Java, library]
---

# System
- 현재 프로그램을 실행하는 사용자의 시스템 환경의 값을 가지고 있는 클래스

---

# Fields
- `in`: 기본 입력 스트림
- `out`: 기본 출력 스트림
- `err`: 기본 에러 출력 스트림

---

# Methods
## `console()`
- 현재 JVM과 연결된 콘솔 리턴
- Console은 command창을 더 다양하게 다룰 수 있음
```java
public class A {
	public static void main(String[] args) {
		Console c = System.console();
		c.writer().printf("Enter your id: ");
		String id = c.readLine();

		c.writer().printf("Enter your password: ");
		char[] pw = c.readPassword();

		c.writer().println("ID: " + id + ", PW: " + String.valueOf(pw));
	}
}
```
```cmd
C:\Users\world\Desktop>java A
Enter your id: wbm
Enter your password:
ID: wbm, PW: 123123
```
- [zzdd1558](https://zzdd1558.tistory.com/156)

## `currentTimeMillis()`
- 1970-01-01 부터 현재 시간까지의 차이를 milli sec 단위로 리턴
- `1648476543466`


## `exit(int status)`
- 프로그램 종료
- status는 종료 시 이유를 구분하기 위해 사용
- `0`: 정상종료


## `gc()`
- JVM의 garbage collector를 실행시켜서 ram에서 사용하지 않는 자바 객체를 정리



## `getEnv()`
- 사용자의 환경 변수 리턴
> 예> Path 값들...


## `getLogger()`
- 로거 리턴



## `getProperties()`
- 사용자의 환경들을 리턴
> 예. OS, CPU 종류, 사용자 국가, java version 등



## `lineSeparator()`
- 각 os에 맞는 줄 변경 string 값 리턴
```yaml
- Unix: \n
- Windows: \r\n
```



## `nanoTime()`
- 1970-01-01 부터 현재 시간까지의 차이를 nano sec 단위로 리턴
- `currentTimeMillis()`보다 정확해서, 주로 시간 관련 작업할 때 사용


---

# Ref
- [geeksforgeeks](https://www.geeksforgeeks.org/java-lang-system-class-java/)
