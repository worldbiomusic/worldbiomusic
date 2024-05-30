---
title: "apache-tomcat"
date: 2020-01-01 00:00:00 +09:00
categories: ['컴퓨터', '웹']
tags: [웹]
---

# 정리
먼저 web과 was의 차이를 아는것이 중요
- web: static data 처리
- was: dynamic data 처리

apache와 tomcat차이
- Apache Server라 함은 WEB 역할을 하는 서버의 이름입니다.
- Tomcat Server라 함은 WAS 역할을 하는 서버의 이름입니다.
- Apache Tomcat Server는 WEB + WAS 서버라 칭할 수 있습니다.

# 참고
- [t-story](https://ssd0908.tistory.com/entry/%EC%95%84%ED%8C%8C%EC%B9%98Apache%EC%99%80-%ED%86%B0%EC%BA%A3Tomcat%EC%9D%98-%EC%B0%A8%EC%9D%B4%EC%A0%90-%EB%B0%8F-%EC%9D%B4%ED%95%B41)
- [velog](https://velog.io/@kdhyo/Apache-Tomcat-%EB%91%98%EC%9D%B4-%EB%AC%B4%EC%8A%A8-%EC%B0%A8%EC%9D%B4%EC%A7%80)


# 참고 리소스 저장
이번 포스트에서는 아파치 톰캣에 대해 알아보도록 하겠습니다.
아파치 톰캣(Apache Tomcat)은 apache software 재단에서 개발한 서블릿 컨테이너만 있는 웹 애플리케이션 서버입니다. 톰캣의 정식 명칭은 Apache Tomcat으로 대다수의 개발자들이 톰캣이라고 통칭하여 부르며 사실상 웹 컨테이너의 표준으로써 순수 자바 플랫폼입니다. 또한 세계에서 가장 많이 사용하고 있는 WAS 중에 하나이기도 하며 지속적인 업데이트를 통해 계속 진화 중인 오픈소스입니다.
 

# WEB서버(Web Server), WAS(Was Server)의 이해 
1. WEB서버(Web Server)
 WEB서버는 정적인 자료를 처리하는 서버입니다. html, css, image등 내용이 변하지 않는 정적인 파일들을 만들어줍니다. Sever에 페이지를 요청하면 서버는 해당하는 화면을 Client PC에 html 파일로 뿌려줍니다. html 파일 이외에 화면의 레이아웃 구성이나 화면에 첨부된 image, css 파일은 내용이 변하지 않는 정적인 파일이기 때문에 WEB서버에서 처리하게 됩니다. 서버에 정적인 모든 파일을 저장하고 클라이언트에서 요청이 생길 때마다 서버에 저장된 파일을 내려주기 때문에 서버 자원의 한계가 생기고 리소스를 많이 차지하게 되는 단점이 있습니다. 이를 보안하기 위해 생긴 게 동적으로 파일을 처리하는 WAS 서버입니다.
 
2. WAS서버(Was Server)
 WAS 서버는 동적인 자료를 처리하는 서버입니다. 기존 WEB서버의 단점을 보완하여 Servlet Container 추가되었습니다. 클라이언트에서 웹 페이지를 요청하면 Servlet Container가 요청정보를 파악하여 실시간으로 페이지에 필요한 파일을 생성합니다. 요청이 올 때마다 페이지에 필요한 정보를 그때그때 생성하므로 서버의 리소스의 부하를 줄일 수 있습니다.
클라이언트에서 요청하는 페이지에서 크게 정적인으로 변하지 않는 정보(image, css, html 등)와 동적 인정보(DB 연동 및 비즈니스 로직)로 나뉠 수가 있는데 WEB서버와 WAS 서버가 요청정보에 맞게 역할을 분배하여 처리합니다.
 
 - Apache Server라 함은 WEB 역할을 하는 서버의 이름입니다.
 - Tomcat Server라 함은 WAS 역할을 하는 서버의 이름입니다.
 - Apache Tomcat Server는 WEB + WAS 서버라 칭할 수 있습니다.
 
3. 연동 목적
 Apache 서버와 Tomcat 서버를 반드시 연동할 필요는 없습니다. 프로젝트가 정적인 데이터만 필요로 하는지, DB 연동 및 비즈니스 로직 + 정직인 데이터를 필요로 하는지 프로젝트의 상황에 맞게 서버를 구축하면 됩니다. Apache 서버는 다양한 모듈과 설정을 통해 사용자에게 편리한 기능을 제공하는데 반해 Tomcat 서버는 Apache 서버에 비해 기능이 다양하지는 않습니다. 다만, Apache 서버의 다양한 모듈 및 설정을 활용하여 더 다양하고 복합적인 기능을 제공합니다.
Apache 서버와 Tomcat서버를 연동하는 모듈은 크게 두 가지로 분류할 수 있습니다.
 

mod_jk는 mod_jserv를 대체한 Apache 서버 모듈로서 AJP프로토콜을 이용해 Tomcat을 지원합니다. tomcat 서버 이외엔 사용할 수 없다는 단점이 있지만, jkMount의 옵션을 통해 여러 가상 호스트별로 설정이 가능하고 대규모 AJP 패킷 크기 지원 및 이상 감지 기능을 제공하는 장점이 있습니다.
mod_proxy는 Apahe 서버에서 제공하는 기본 모듈로서 모든 애플리케이션에서 사용이 가능합니다. Apache와의 연결 프로토콜 http, https, ajp 모두 지원하는 장점이 있습니다. 하지만 8K 이상의 패킷을 지원하지 못하고 부하 분산 기능만 제공하는 단점이 있습니다.



```
connector
port
http
8080
https
8443
ajp
8009
```


이것으로 Apache Tocmat에 대해서 알아보았습니다.
 