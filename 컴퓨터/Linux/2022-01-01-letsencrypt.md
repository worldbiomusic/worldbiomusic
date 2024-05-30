---
title: "letsencrypt"
date: 2020-01-01 00:00:00 +09:00
categories: ['컴퓨터', 'Linux']
tags: [Linux]
---

```bash
sudo apt install letsencrypt
sudo certbot certonly --standalone -d veneer-kisia.r-e.kr
/etc/letsencrypt/live/veneer-kisia.r-e.kr
```


# 설정법
1. letsencrypt 다운로드
```bash
sudo apt install letsencrypt
```

2. 도메인 등록
```bash
sudo certbot certonly --standalone -d {domain}
# 예. sudo certbot certonly --standalone -d veneer.r-e.kr
```

3. 권한 설정: `/etc/letsencrypt/live/{domain}`안의 파일들을 user or group에 `x` 권한 부여


4. 사용


# 파일 위치
- `/etc/letsencrypt`
- `/etc/letsencrypt/archive`: 실제 키 파일
- `/etc/letsencrypt/live`: archive를 향한 link 파일


# 주의사항
- letsencrypt의 파일들은 기본적으로 `/etc/letsencrypt`에 root 권한으로 설정됨
- 기본 계정으로 flask에서 ssl을 적용하면 파일을 읽지 못하기 때문에 root계정으로서 실행 또는 위에 `live` 파일의 user권한을 자신것 혹은 그룹권한을 설정해줘야 함 (최소 `2`(--x)이여야 함: 단지 실행하는 것이므로)


# 참고
- [ssl(letsencrypt) 설정방법](https://minsigi.tistory.com/9)