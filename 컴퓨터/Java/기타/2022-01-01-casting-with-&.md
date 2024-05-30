---
title: "casting-with-&"
date: 2020-01-01 00:00:00 +09:00
categories: ['컴퓨터', 'Java', '기타']
tags: [Java]
---

# 설명
만약 한번만 어떤 클래스에 실시간으로 메서드가 없는 특정 인터페이스를 구현하도록 해놓으려면 원래는 `클래스 implements`를 사용해서 컴파일 되기전에 해야 되지만, 밑의 방법으로 임시로 구현하게 만들 수도 있다

new B()가 A클래스로 형변환 하면서 임시로 메서드가 없는 `Serializable`인터페이스를 구현하게 동시에 해준다 (그래서 m()의 반환값이 Serializable이 가능하다)

```java
interface A {
}

class B implements A {
}

class Main {
    Serializable m() {
        return (A & Serializable) new B();
    }
}
```


# 참고
[링크](https://stackoverflow.com/questions/28509596/java-lambda-expressions-casting-and-comparators)

