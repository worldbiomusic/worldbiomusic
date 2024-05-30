---
title: "iterator-iterable"
date: 2020-01-01 00:00:00 +09:00
categories: ['컴퓨터', 'python']
tags: [python]
---

# iterator
- 요소들을 실제 순차접근 가능한 클래스
- `__next()__`를 가짐, for에서 순차접근할 때 쓰임


# iterable
- `__iter()__`를 가짐, iterator()를 리턴 (`iter(객체)`로도 쓰임)
- `list, map, set`들이 iterable 객체 (반복작업 될 때 내부 `__iter()__`가 사용됨)


# 참고
- [tistory](https://tibetsandfox.tistory.com/27)