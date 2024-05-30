---
title: "Decorator 패턴"
date: 2020-01-01 00:00:00 +09:00
categories: [컴퓨터, 디자인패턴, 정리]
tags: [디자인패턴]
---

데코레이터 패턴은 적용할 기준이 있다. 바로 객체들끼리 서로 감싸야 하는 필요성이 있을 때 사용하면 좋은 패턴이다.

예를 들면, 

1. Notifier를 구현하는 EmailNotifier과 MessageNotifier가 있을 때 이것을 decorator로 해도 상관은 없다. 하지만 서로를 연결시켜서 얻는 장점은 단지 편리성 밖에 얻지 못한다. (심지어 저것들은 List로도 관리해도 런타임때 변경도 되고 무방하다)
2. Java library의 [InputStream](https://docs.oracle.com/javase/7/docs/api/java/io/InputStream.html)을 보면 FileInputStream과 BufferedInputStream를 결합해서 같이 사용할수 있다. 이 떄 장점은 BufferedInputStream이 input작업의 속도를 buffer를 사용해서 빠르게 FileInputStream으로 전송해주어서 편리성 외에 속도를 높혀주는 장점을 사용한 것이다. 감싼 객체의 결과값이 감싸진 객체에 영향을 주어서 서로간의 결합도 중요하고 순서도 중요해서 데코레이터 패턴을 사용해서 구현해야 좋은 케이스.

이 처럼 단지 편리성을 위해서 데코레이터를 쓰는것보다는 서로 겹쳐있어야 하는 경우나 다른 효용성이 더 있는 경우같은 객체들끼리 있을 때 주로 써야 좋은 패턴이다.

# 참고
- [refactoring.guru](https://refactoring.guru/design-patterns/decorator): 밑에 DataSource 구현해보기 (예제가 좋음), java lib의 I/O stream도 구현해보기