---
title: "자바 라이브러리: Object"
date: 2020-01-01 00:00:00 +09:00
categories: [컴퓨터, Java]
tags: [Java, library]
---

# Object
- 자바의 모든 클래스가 상속하는 클래스
- 명시적으로 `extends`를 사용해서 다른 클래스를 상속하지 않으면 자동으로 Object 클래스를 상속 (또는 `extends Object`로 선언해놓아도 됨)

---

# Methods
## `clone()`
- 객체를 복사
- `Cloneable` interface 구현 필요
- 기본적으로 protected이므로 외부에서 사용하려면 public으로 변경
- 메모리 주소가 아예 다른, 즉 같은 값만을 가지는 또 다른 객체를 생성
- Object#clone() 자체는 깊은 복사(deep copy)이지만 내부의 변수가 참조형인 경우에는 메모리 주소만 복사해주는 얕은 복사(shallow copy)를 함 (내부 변수도 깊은 복사를 하려면 clone()을 같은 방식으로 구현해야 함)
- [참고](https://developer-youngjun.tistory.com/20)
- 이러한 방법대신 복사 생성자나 팩토리 패턴을 사용 가능

### clone() 예시
```java
public class Member implements Cloneable {
    private String name;
    private int age;
    private Address address;

    @Override
    public Member clone() {
        try {
            return (Member) super.clone();
        } catch (CloneNotSupportedException e) {
            // Cloneable을 구현했기 때문에 이 블록이 실행되는 일은 없다.
            return null;
        }
    }
}
```

### clone()의 내부 참조변수 deep copy 예시
```java
public class Member implements Cloneable {
    private String name;
    private int age;
    private Address address;

    @Override
    public Member clone() {
        try {
            Address clonedAddress = address.clone();
            Member clonedMember = (Member) super.clone();
            clonedMember.setAddress(clonedAddress);
            return clonedMember;
        } catch (CloneNotSupportedException e) {
            // Cloneable을 구현했기 때문에 이 블록이 실행되는 일은 없다.
            return null;
        }
    }
}

public class Address implements Cloneable {
    private long zipCode;
    private String city;

    @Override
    public Address clone() throws CloneNotSupportedException {
        return (Address) super.clone();
    }
}
```

## `equals()`
- primitive type: 두 객체의 값이 같은지 비교
- reference type: 두 객체의 메모리 주소가 같은지 비교
- `String#equals()`같은 경우는 equals()를 오버라이딩해서 문자열이 같은지 비교를 함


## `getClass()()`
- 클래스의 정보를 담고있는 `Class` 객체를 반환


## `hashCode()`
- hash 함수를 사용해서 객체를 구별하기 위한 메소드
- `equals()`에서 서로 객체를 비교할 때 기준이 되는 메소드 (구현하는 사람들간의 규약)
- [johngrib](https://johngrib.github.io/wiki/Object-hashCode/)


## `toString()`
- 객체의 정보를 문자로 정리해서 출력하는 메소드
- 기본값: `getClass().getName() + "@" + Integer.toHexString(hashCode())`
- [johngrib](https://johngrib.github.io/wiki/Object-toString/)


## `notify()`
- 잠들어있는 스레드중 랜덤으로 1개를 깨운다
- [happinessoncode](http://happinessoncode.com/2017/10/05/java-object-wait-and-notify/)
- [nowonbun](https://nowonbun.tistory.com/301)

## `notifyAll()`
- 잠들어있는 모든 스레드를 깨운다


## `wait()`
- 현재 실행중인 스레드를 잠들게 한다


## `wait(millis)`
- 현재 실행중인 스레드를 잠들게 한다


## `wait(mills, nano)`
- 현재 실행중인 스레드를 잠들게 한다



























