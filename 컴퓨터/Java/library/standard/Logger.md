---
title: "자바 라이브러리: Logger"
date: 2020-01-01 00:00:00 +09:00
categories: [컴퓨터, Java]
tags: [Java, library]
---

# Logger
- 로그(기록)을 다양한 옵션으로 조절하면서 기록하게 도와주는 라이브러리

---

# Fields



## `GLOBAL_LOGGER_NAME`
- 전체 프로그램에서 사용할 global 로거의 이름 (Logger#getGlobal()로 생성할 때의 이름)





---

# Methods


## `getLogger(String name)`
- static
- `name`으로 만들어진 로거를 리턴
- 다른 곳에서 같은 이름으로 가져오면 이미 생성되 있는 같은 객체를 리턴
```java
Logger logger = Logger.getLogger("a");

System.out.println("before: " + logger.getLevel());
logger.setLevel(Level.FINE);
System.out.println("after: " + logger.getLevel());

Logger l2 = Logger.getLogger("a");
System.out.println("new: " + l2.getLevel());
```
```yaml
before: null
after: FINE
new: FINE
```

## `log(Level level, String msg)`
- 주어진 level 단계의 msg 로그 작성



## `info(String msg)`
- info level 로그 작성



## `warning(String msg)`
- warning level 로그 작성



## `severe(String msg)`
- severe level 로그 작성



## `setLevel(Level newLevel)`
- 설정한 level 이상의 로그만 작성
```java
Logger logger = Logger.getLogger("a");

logger.log(Level.INFO, "INFO");
logger.log(Level.WARNING, "WARNING");
logger.log(Level.SEVERE, "SEVERE");

logger.setLevel(Level.WARNING);

System.out.println("==============");
logger.log(Level.INFO, "INFO");
logger.log(Level.WARNING, "WARNING");
logger.log(Level.SEVERE, "SEVERE");
```
```yaml
Mar 28, 2022 11:30:28 PM test.wbm.TestMain main
INFO: INFO
Mar 28, 2022 11:30:28 PM test.wbm.TestMain main
WARNING: WARNING
Mar 28, 2022 11:30:28 PM test.wbm.TestMain main
SEVERE: SEVERE
==============
Mar 28, 2022 11:30:28 PM test.wbm.TestMain main
WARNING: WARNING
Mar 28, 2022 11:30:28 PM test.wbm.TestMain main
SEVERE: SEVERE
```


## `addHandler(Handler handler)`
- 로그의 형식(format)을 변경
```java
Logger logger = Logger.getLogger("a");

System.out.println("===Default===");
logger.log(Level.INFO, "INFO");
logger.log(Level.WARNING, "WARNING");
logger.log(Level.SEVERE, "SEVERE");

// remove handler
logger.setUseParentHandlers(false);

System.out.println("===No handler===");
logger.log(Level.INFO, "INFO");
logger.log(Level.WARNING, "WARNING");
logger.log(Level.SEVERE, "SEVERE");

// set custom handler
Handler handler = new ConsoleHandler();
handler.setFormatter(new Formatter() {
  @Override
  public String format(LogRecord record) {
    String format = "";
    format += "[";
    format += record.getLevel();
    format += "] ";
    format += record.getMessage() + System.lineSeparator();

    return format;
  }
});
logger.addHandler(handler);

System.out.println("===Custom handler===");
logger.log(Level.INFO, "INFO");
logger.log(Level.WARNING, "WARNING");
logger.log(Level.SEVERE, "SEVERE");
```
```yaml
===Default===
Mar 28, 2022 11:56:25 PM test.wbm.TestMain main
INFO: INFO
Mar 28, 2022 11:56:25 PM test.wbm.TestMain main
WARNING: WARNING
Mar 28, 2022 11:56:25 PM test.wbm.TestMain main
SEVERE: SEVERE
===No handler===
===Custom handler===
[INFO] INFO
[WARNING] WARNING
[SEVERE] SEVERE
```

---

# Ref
- [codechacha](https://codechacha.com/ko/java-logging-api/)
- [sdesigner](https://sdesigner.tistory.com/100)
- [GIS DEVELOPER](http://www.gisdeveloper.co.kr/?p=5174)



















