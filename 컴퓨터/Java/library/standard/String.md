---
title: "자바 라이브러리: String"
date: 2020-01-01 00:00:00 +09:00
categories: [컴퓨터, Java]
tags: [Java, library]
---

# String
- 문자열 관련 클래스
- 주의할 것: 대부분의 문자열의 메서드는 반환값을 이용해서 적용해야 함 (String 클래스의 예외적인 특징) (효율을 위해서 객체이지만 기본 타입처럼 동작)

---

# Fields
- 없음

---

# Methods


## `chatAt(int index)`
- index 번째의 문자 값 리턴


## `compareTo(String anotherString)`
- anotherString과 문자열을 사전식으로 비교한 값 리턴
```yaml
- 동등: 0
- 이전: -(차이)
- 이후: +(차이)
```


## `compareToIgnoreCase(String str)`
- `compareTo(String anotherString)`메서드에서 영어 대소문자를 구분하지 않음


## `concat(String str)`
- 현재 문자열의 뒤에 str을 붙임
- String은 연산자 오버로딩으로 `+`로 간단하게 사용 가능


## `contains(CharSequence s)`
- 문자열에 `s` 가 포함되어 있는지 여부


## `endsWith(String suffix)`
- 문자열의 끝이 `suffix`로 끝나는지 여부


## `equals(Object obj)`
- obj와 문자열의 값이 같은지 비교


## `equalsIgnoreCase(String anotherString)`
- `equals(Object obj)`에서 영어 대소문자를 구분하지 않고 비교


## `format(String format, Object... args)`
- static
- C언어 스타일의 format


## `indent(int n)`
- 각 라인의 앞에 n만큼 공백(` `) 들여쓰기
- [javastring](https://www.javastring.net/java/string/java-string-indent-method-examples)

## `indexOf(int ch)`
- 문자열에서 `ch`(문자)가 나오는 가장 첫번째 위치


## `indexOf(String str)`
- 문자열에서 `str`(문자열)가 나오는 가장 첫번째 위치



## `isBlank()`
- 아무것도 없거나 공백(` `)으로만 이루어지면 true



## `isEmpty()`
- length가 0일 때만 true



## `lastIndexOf(int ch)`
- 문자열에서 `ch`(문자)가 나오는 가장 마지막 위치



## `lastIndexOf(String str)`
- 문자열에서 `str`(문자열)가 나오는 가장 마지막 위치



## `length()`
- 문자열 길이



## `lines()`
- 각 라인이 담긴 Stream 리턴



## `matches(String regex)`
- 주어진 regex와 정규표현식이 맞는지 비교



## `repeat(int count)`
- 문자열 * `count` 만큼 이어붙임



## `replace(CharSequence target, CharSequence replacement)`
- 문자열의 `target`을 모두 `replacement`로 변경



## `split(String regex)`
- `regex` 기준으로 문자열 나누기



## `startsWith(String prefix)`
- 문자열이 prefix로 시작하는지 검사



## `strip()`
- 앞, 뒤의 공백 제거 (trim()보다 더 많은 공백 제거)



## `substring(int beginIndex, int endIndex)`
- `beginIndex`부터 `endIndex`까지 문자열 자르기



## `toUpperCase()`
- 모든 문자열을 대문자로 변경


## `toLowerCase()`
- 모든 문자열을 소문자로 변경


## `trim()`
- 앞, 뒤의 공백 제거


## `valueOf(Object obj)`
- obj의 값을 가지고 문자열로 변환
- 보통은 `"" + obj`로 사용





---

# Ref
- [api](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/lang/String.html)
