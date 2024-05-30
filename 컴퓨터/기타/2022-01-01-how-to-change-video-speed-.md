---
title: "how-to-change-video-speed-"
date: 2020-01-01 00:00:00 +09:00
categories: ['컴퓨터', '기타']
tags: [ ]
---

# 웹 브라우저에서 동영상 속도 변경 방법
## 1. 웹 브라우저 개발자 모드 실행 (F12)

## 2. `Console`창에 밑의 코드 입력
```javascript
document.querySelector('video').playbackRate = 16.0;
```

# 예외
- 위의 방법이 안될 때는 보통 동영상 브라우저가 따로 띄워지지 않고 html속에 포함되어 있는 경우이다. 이 때는 개발자모드(F12) 탭에서 `element select 버튼`을 누르고 동영상부분을 눌러 포커스를 
설정한 다음에 다시 Console창에 코드를 입력하면 됨
