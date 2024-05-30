---
title: "swap-memory"
date: 2020-01-01 00:00:00 +09:00
categories: ['컴퓨터', 'Linux']
tags: [Linux]
---

# Ubuntu
1. 스왑파일 생성
```
sudo fallocate -l 1G /swapfile
```

2. 스왑파일 권한 설정
```
sudo chmod 600 /swapfile
```

3. 스왑파일 포맷
```
sudo mkswap /swapfile
```

4. 스왑 활성화
```
sudo swapon /swapfile
```

5. 부팅시 자동 활성화 (`/etc/fstab` 파일에 추가)
```
echo '/swapfile none swap sw 0 0' | sudo tee -a /etc/fstab
```

6. 스왑 확인 (또는 `htop`로 스왑 메모리 확인 가능)
```
sudo swapon --show
```


# 스왑 메모리 크기 변경 방법
1. 스왑 비활성화
```
sudo swapoff /swapfile
```

2. 스왑 파일 크기 변경 (`bs`: 블럭크기, `count`: 블럭 개수)
```
sudo dd if=/dev/zero of=/swapfile bs=1M count=2048
```

3. 스왑 영역 설정
```
mkswap /swapfile
```

4. 스왑 활성화
```
swapon /swapfile
```

5. 크기 확인
```
swapon --show
```