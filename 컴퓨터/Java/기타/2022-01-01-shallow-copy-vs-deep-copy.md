---
title: "shallow-copy-vs-deep-copy"
date: 2020-01-01 00:00:00 +09:00
categories: ['컴퓨터', 'Java', '기타']
tags: [Java]
---

# Shallow copy
- 겉만 복사하는것과 같이 해당 객체에 대한 참조변수 reference만 복사하는 것
- 같은 객체를 참조중이므로, 객체의 값을 변경하면 다른 곳에서 참조중인 곳에게도 영향을 미친다

# Deep copy
- 내부의 값들까지 모두 복사해버리는걸로, 동일한 객체가 하나 더 생기는 것
- 다른 객체를 참조중이므로, 서로에게 영향을 미치지 않는다
- `Cloneable`을 구현해야 함 (primitive type(immutable: e.g. int, double, String)은 바로 deep-copy가 되지만, 객체(mutable: e.g. Date)들은 다시 구성하고 있는 클래스들까지 recursive하게 모두 clone 구현이 필요하고 호출해야 함)
- [참고](https://howtodoinjava.com/java/collections/arraylist/arraylist-clone-deep-copy/)

# 자바
- 자바에서 지원하는 모든 util(e.g. Collections.copy(), new ArrayList<>(List), ArrayList.copy())은 `shallow copy`를 한다
- `Deep copy`는 객체가 `Cloneable`을 구현하고, 외부에서 `객체.clone()`으로 해야 한다
- primitive type들은 super.clone()으로 단순 복사가 된다 (reference로 작동하지 않기 때문)
- [`clone()` 사용 주의할 점](Cloneable.md)

# 예시
- 코드
```java
class A implements Cloneable {
	int a;
	B b;

	public A(int a, B b) {
		this.a = a;
		this.b = b;
	}

	@Override
	public String toString() {
		return String.format("[a: %d, b: %d] ", this.a, this.b.b);
	}

	@Override
	public Object clone() throws CloneNotSupportedException {
		A a = (A) super.clone();
		a.b = (B) b.clone();
		return a;
	}
}

class B implements Cloneable {
	int b;

	public B(int b) {
		this.b = b;
	}

	@Override
	public Object clone() throws CloneNotSupportedException {
		return (B) super.clone();
	}
}

public class Test {

	public static void main(String[] args) throws Exception {
		B b1 = new B(1);
		B b2 = new B(2);

		A a1 = new A(-1, b1);
		A a2 = new A(-2, b2);

		ArrayList<A> aList = new ArrayList<>();
		aList.add(a1);
		aList.add(a2);
		System.out.println("aList: " + aList);

		ArrayList<A> copied = new ArrayList<>();
		for (A a : aList) {
			copied.add((A) a.clone());
		}

		System.out.println("copied: " + copied);

		copied.get(0).b.b = 3;

		System.out.println("\naList: " + aList);
		System.out.println("copied: " + copied);
	}
}
```

- 결과
```cmd
aList: [[a: -1, b: 1] , [a: -2, b: 2] ]
copied: [[a: -1, b: 1] , [a: -2, b: 2] ]

aList: [[a: -1, b: 1] , [a: -2, b: 2] ]
copied: [[a: -1, b: 3] , [a: -2, b: 2] ]
```
