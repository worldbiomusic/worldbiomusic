---
title: "remove-with-all-configs"
date: 2020-01-01 00:00:00 +09:00
categories: ['컴퓨터', 'Linux']
tags: [Linux]
---

# 설명
- 특정 소프트웨어를 삭제하려면 `apt-get remove <sw>`로 되지만, 설정파일들은 같이 삭제가 안된다
- 모든 설정파일까지 같이 삭제하려면 `apt-get purge --auto-remove <sw>`를 입력해야 한다
