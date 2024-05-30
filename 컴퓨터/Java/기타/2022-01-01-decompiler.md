---
title: "decompiler"
date: 2020-01-01 00:00:00 +09:00
categories: ['컴퓨터', 'Java', '기타']
tags: [Java]
---

# 설명
- class 파일, jar 파일등을 원래 java 코드로 볼 수 있는 기능인 decompiler 설명

# [jd-gui](http://java-decompiler.github.io/#jd-gui-overview)
- 가벼운 독립 프로그램
## 사용방법
- class, jar 파일을 drag and drop 하면 java 코드로 디컴파일해서 보여준다


# [jd-eclipse](http://java-decompiler.github.io/#jd-eclipse-overview)
- eclipse 프로그램 안에서 사용할 수 있는 decompiler
## 적용방법
1. [jd-eclipse] 의 download에 나온 installation 순서대로 다운로드 한다
2. `Window > Preferences > General > Editor > File Associations`에서 `*.class`와 `*.class without source` 클릭해서 Associate editors 부분에 `JD Class File Viewer`를 
add하고, default로 지정한다
## 사용방법
- class 파일을 오픈한다
- java 소스코드 내에서 `ctrl`을 누른 상태로 클래스를 누르면 java코드의 클래스파일이 열린다
## 주의사항
- decompile 하려는 클래스가 build path에 등록이 되어있어야 한다
- 수정 불가능하다


[jd-eclipse]: http://java-decompiler.github.io/#jd-eclipse-overview
