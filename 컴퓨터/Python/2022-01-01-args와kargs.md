---
title: "args와kargs"
date: 2020-01-01 00:00:00 +09:00
categories: ['컴퓨터', 'python']
tags: [python]
---

# `*` 쓰임
- `함수 인자`: 여러개 인자를 list로 묶어서 반환
- `일반 list 변수`: list변수를 여러개 인자로 풀어서 반환
- args = non-keyworded arguments

# `**` 쓰임
- `함수 인자`: 여러개 인자를 dict로 묶어서 반환
- `일반 dict 변수`: dict변수를 여러개 인자로 풀어서 반환
- kargs = keyworded arguments
- 인자를 전달할 것만 골라서 전달하려 할 때 사용하기 좋음

```py
def fun(a1, a2, a3=3):
  print(a1, a2, a3)

def one(*args): # 여러개 인자를 list로 묶음 (함수 인자에서 * 사용시)
  fun(*args) # list변수를 여러개 인자로 풀어서 함수로 전달 (일반 list 변수에 * 사용시)

def two(**kargs): # 여러개 인자를 dict로 묶음 (함수 인자에서 ** 사용시)
  fun(**kargs) # dict변수를 여러개 인자로 풀어서 함수로 전달 (일반 dict 변수에 ** 사용시)


p1 = [1, 2]
one(*p1)
one(1, 2) # one(*args)로 받으므로 풀어서 전달 가능

p2 = {"a1": 11, "a2": 22}
two(**p2)
two(a1=11, a2=22) # two(**kargs)로 받으므로 풀어서 변수:값 으로 전달 가능
```

결과
```
1 2 3
1 2 3
11 22 3
11 22 3
```

---

자동으로 다른 dict에 풀수도 있음
```py
def a(a, **kargs):
    print(a, kargs)
    d = {"a": a, **kargs} # {'a': 1, 'b': 2, 'c': 3}으로 알아서 풀어짐
    e = {"a": a, "kargs": kargs} # {'a': 1, 'kargs': {'b': 2, 'c': 3}}로 또 다른 dict 생성
    print(d, e)

a(1, b=2, c=3)
```

결과
```
{'a': 1, 'b': 2, 'c': 3}
{'a': 1, 'kargs': {'b': 2, 'c': 3}}
```