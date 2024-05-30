---
title: "PATH-vs-CLASSPATH"
date: 2020-01-01 00:00:00 +09:00
categories: ['컴퓨터', 'Java', '기타']
tags: [Java]
---

# 설명
- PATH는 운영체제에서 사용하는 전역변수 (예. `java`와 `javac`같은 프로그램을 어디서든지 실행할 수 있게 해줌)
- CLASSPATH는 java언어가 실행될 때 (`java` 명령어), import부분에 있는 클래스들을 참조하기 위한 기준 디렉터리 주소
(근데 내 환경에서 CLASSPATH = `.` 이던데, 왜 기본 자바 라이브러리가 불러와지면서 실행이 잘되지?)

- java로 실행할 클래스가 패키지 내에 있으면, 외부에서 `java packages.../class`로 실행해야 함

# 참고
- [what-is-the-difference-between-path-and-classpath-in-java](https://stackoverflow.com/questions/33062443/what-is-the-difference-between-path-and-classpath-in-java)
- [how-to-run-a-class-file-that-is-part-of-a-package-from-cmd](https://stackoverflow.com/questions/18139756/how-to-run-a-class-file-that-is-part-of-a-package-from-cmd)
