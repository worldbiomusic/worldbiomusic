---
title: "Cloneable"
date: 2020-01-01 00:00:00 +09:00
categories: ['컴퓨터', 'Java', '기타']
tags: [Java]
---

# 설명
- 자바의 Object객체에는 기본적으로 clone()이 protected로 선언되어 있음
- 그리고 이상하게 Cloneable interface에는 아무런 메소드가 없음
- 이는 프로그램 작성 실수로 예측됨. 원래는 Object에서 clone()을 제거하고, 필요할때만 Cloneable interface의 clone()를 구현하게 해야 함


# 주의
- clone()을 사용하려할 때는 Cloneable을 implements하고(단순 체크 용도), clone()의 접근제어자를 public으로 바꿔서 사용해야 함 

# 참고
- https://stackoverflow.com/questions/1138769/why-is-the-clone-method-protected-in-java-lang-object
