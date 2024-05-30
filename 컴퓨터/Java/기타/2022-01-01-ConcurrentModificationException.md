---
title: "ConcurrentModificationException"
date: 2020-01-01 00:00:00 +09:00
categories: ['컴퓨터', 'Java', '기타']
tags: [Java]
---

# 설명
- `ConcurrentModificationException`이란 자바 collection들을 반복문에서 remove를 접근하려 할 때 여러 thread의 접근으로 데이터 무결성이 깨질 수 있어서 예외를 던짐

# 해결법
### 실행 환경이 single threadd 일 때
single thread 접근을 가정하는 `CopyOnWriteArrayList<>()` 객체 사용
### 실행 환경이 multi threadd 일 때
Iterator<> 사용