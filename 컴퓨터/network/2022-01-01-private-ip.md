---
title: "private-ip"
date: 2020-01-01 00:00:00 +09:00
categories: ['컴퓨터', 'network']
tags: [network]
---

# 설명
- IP 주소는 모든것이 public ip가 아니라, 일정 범위는 모두 다 약속으로(RFC 1918) private ip 대역으로 쓰기로 약속했다
```yaml
Class A: 10.0.0.0 to 10.255.255.255
Class B: 172.16.0.0 to 172.31.255.255
Class C: 192.168.0.0 to 192.168.255.255
```
- 위의 범위들은 무조건 private ip로  보는것이다 (컴퓨터들 세팅이 모두 이렇게 하기로 약속함)
- 그러므로 이 범위의 아이피들은 밑의 특징을 가진다

1. non-routable (어차피 내부에서만 쓰이므로 라우팅 필요없음)
2. not unique (private ip는 다른 공인 아이피들이 각자 또 따로 private ip범위를 할당해서 사용할 수 있으므로) (하지만 내부에서는 유니크)
3. private ip는 등록되어서 사용될 필요가 없다

# 참고
- [private address ranges](https://www.ibm.com/docs/en/networkmanager/4.2.0?topic=translation-private-address-ranges)
