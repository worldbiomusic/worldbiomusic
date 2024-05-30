---
title: "boot-loader"
date: 2020-01-01 00:00:00 +09:00
categories: ['컴퓨터', 'Linux']
tags: [Linux]
---

주로 사용되는 GRUB(GRand Unified Bootloader) 관한 문서
- 대부분의 OS 부트로드 가능
- 부트로더가 커널 이미지를 로드해서 OS가 실제로 동작하는 것
- 부팅경로와 OS이미지를 알려줘야 부팅이 가능
- `c`를 누르면 grub를 컨트롤할 수 있는 간단한 bash를 구현한 쉘이 시작되서 할 수 있다.
(ls, clear, exit, set, help 등의 간단한 명령어만 지원)

# 순서
1. 어떤 디스크들이 있는지 확인 (이름이 나와서 확인 가능)
```bash
ls
```
2. 부팅경로 설정
```bash
set root=(hd0,msdos1)
```
3. root경로를 디스크 경로로 바꾸기
```bash
linux /boot/vmlinuz root=/dev/sda1 (예시)
```
4. 커널 이미지 경로 설정
```bash
initrd /boot/initrd
```
5. 부트 시작
```bash
boot
```

**디스크이름**  
나의 경우에는 Ubuntu를 rufus에 다운받고 시도했다.

다른 컴으로 폴더 구조를 보면 `/casper/vmlinuz`, `/casper/initrd` 이런식으로 경로가 구성되어 있었다. 그리고 적용할 컴퓨터에서 grub에서 ls를 실행해보면 
```
(hd0) (hd0,msdos2) (hd0,msdos1) (hd1) (hd1,msdos4) (hd1,msdos3) (hd1,msdos2) (hd1,msdos1)
```
이렇게 윈도우 디스크가 나왔다.

![hd](https://github.com/worldbiomusic/Blog/assets/61288262/5cf734a8-4f75-462d-b96c-7b110d8d8b8e)

위의 하드디스크 이름을 보고 위에 3번에서 `root=`를 잘 설정해줘야 한다.

근데 이 모든건 사실 `grub.cfg`파일에 스크립트로 만들어져 있고, grub이 실행되면 선택만 하면 실행이 자동으로 된다. 


# 참고
- [1](https://blog.neonkid.xyz/225)
- [2](https://m.blog.naver.com/dudwo567890/130158001734)
