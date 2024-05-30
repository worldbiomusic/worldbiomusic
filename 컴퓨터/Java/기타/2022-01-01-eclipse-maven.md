---
title: "eclipse-maven"
date: 2020-01-01 00:00:00 +09:00
categories: ['컴퓨터', 'Java', '기타']
tags: [Java]
---

# 설명
- 이클립스에서 Maven 사용 설명
- 이클립스에는 기본적으로 maven이 같이 설치되어 있음 (`Window > Preferences > Maven > Installations` 에서 maven 버전 확인 가능)
- 기본적으로 다운로드된 maven은 환경변수 설정이 안되있어서 cmd 창에서 사용 못함 (프로그램위치를 모르겠음)

# 새로운 Maven 다운로드
- 새로운 maven을 다운로드 받고 환경변수 설정을 하고 이클립에도 적용을 하면, 이클립스와 cmd 2군데서 같은 maven으로 사용할 수 있다
- [설치 방법](https://copycoding.tistory.com/176)

# plugin
- maven에서 제공하는 여러가지 기능의 플러그인
## 종류
- [`shade`](https://maven.apache.org/plugins/maven-shade-plugin/): 의존중인 library(.jar) 들과 함께 1개의 jar파일로 빌드해주는 도구 (Fat-jar 와 비슷한 기능)

# 오류
## 플러그인 파일에 plugin.yml 미포함
- `pom.xml`파일에 밑의 코드가 필요하다
```xml
<sourceDirectory>src</sourceDirectory>
```
