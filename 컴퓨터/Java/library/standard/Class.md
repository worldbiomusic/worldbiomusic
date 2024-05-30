---
title: "자바 라이브러리: Class"
date: 2020-01-01 00:00:00 +09:00
categories: [컴퓨터, Java]
tags: [Java, library]
---

# Class
- 클래스의 정보를 담고 있는 클래스
- 생성불가, JVM에 올라간 객체를 Class로 접근하는데 사용됨
- Constructor, Method, Field, Annotation, Enum, Super class 등에 
- Reflection API 에 사용됨
- 기본 자료형(primitive type)도 사실 모두 class (e.g. int, double, void ...)

---

# Fields
- 없음

---

# Methods


## `forName(String className)`
- className의 클래스 타입을 리턴
- package까지 경로 필요
- 밑의 방식도 사용 가능 (정적)
```java
Class c = String.class
```

## `getDeclaredMethods()`
- 해당 클래스만의 모든 접근 제어자 메서드 객체(Method) 반환 (상위 클래스 미 포함)


## `getMethods()`
- 해당 클래스의 모든 public 메서드 객체 반환 (상위 클래스 포함)


## `getDeclaredFields()`
- 해당 클래스만의 모든 접근 제어자 필드 객체(Field) 반환 (상위 클래스 미 포함)


## `getFields()`
- 해당 클래스의 모든 public 필드 객체 반환 (상위 클래스 포함)


## `getResource(String name)`
- name의 리소스 찾기
- jar파일로 추출하고 나서 같이 포함시킨 리소스를 사용할 때 사용될 수 있음

```java
package test.wbm;

import java.lang.reflect.Field;
import java.lang.reflect.Method;
import java.util.Arrays;

public class TestMain {
	public static void main(String[] args) {
		try {

			Class clazz = Class.forName("test.wbm.B");

			System.out.println("[getDeclaredFields]");
			Arrays.asList(clazz.getDeclaredFields()).forEach(f -> System.out.println(f.getName()));
			System.out.println();

			System.out.println("[getFields]");
			Arrays.asList(clazz.getFields()).forEach(f -> System.out.println(f.getName()));
			System.out.println();

			System.out.println("[getDeclaredMethods]");
			Arrays.asList(clazz.getDeclaredMethods()).forEach(m -> System.out.println(m.getName()));
			System.out.println();

			System.out.println("[getMethods]");
			Arrays.asList(clazz.getMethods()).forEach(m -> System.out.println(m.getName()));
			System.out.println();

			// private field 변경
			System.out.println("private field 변경");
			B b = new B();
			Field field = clazz.getDeclaredField("privateBField");
			field.setAccessible(true);
			System.out.println(b);
			field.set(b, 9);
			System.out.println(b);
			System.out.println();

			// private method 호출
			System.out.println("private method 호출");
			Method method = clazz.getDeclaredMethod("privateBMethod");
			method.setAccessible(true);
			method.invoke(b);

		} catch (Exception e) {
			e.printStackTrace();
		}
	}
}

class A {
	private int privateAField;
	public int publicAField;

	public void publicAMethod() {
		System.out.println("publicAMethod()");
	}

	private void privateAMethod() {
		System.out.println("privateAMethod()");
	}

	@Override
	public String toString() {
		return "A [privateAField=" + privateAField + ", publicAField=" + publicAField + "]";
	}

}

class B extends A {
	private int privateBField;
	public int publicBField;

	public void publicBMethod() {
		System.out.println("publicBMethod()");
	}

	private void privateBMethod() {
		System.out.println("privateBMethod()");
	}

	@Override
	public String toString() {
		return super.toString() + "B [privateBField=" + privateBField + ", publicBField=" + publicBField + "]";
	}

}
```

- 결과
```yaml
[getDeclaredFields]
privateBField
publicBField

[getFields]
publicBField
publicAField

[getDeclaredMethods]
toString
privateBMethod
publicBMethod

[getMethods]
toString
publicBMethod
publicAMethod
wait
wait
wait
equals
hashCode
getClass
notify
notifyAll

private field 변경
A [privateAField=0, publicAField=0]B [privateBField=0, publicBField=0]
A [privateAField=0, publicAField=0]B [privateBField=9, publicBField=0]

private method 호출
privateBMethod()

```

---

# Ref
- [gyrfalcon](https://gyrfalcon.tistory.com/entry/Java-Reflection)
- [codechacha](https://codechacha.com/ko/reflection/)
