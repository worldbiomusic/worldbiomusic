---
title: "git credential"
date: 2020-01-01 00:00:00 +09:00
categories: [컴퓨터, Git]
tags: [git, 깃]
---

# 설명
- git command line(git bash)를 이용해서 github과 작업할 때 자동 로그인 기능 해주는 작업
- `Git Credential / Keychain`이 안전함 (`git config --global credential.helper wincred`)
- github이 token을 사용한 이후부터는 `password`에 token을 넣어야 함
- `window > Credential Manager > WIndows Credentials > Generic Credential`에서 git:https:github.com 목록을 Edit 누르고, 
`password`에 token값을 넣으면 됨

# 순서
0. [Token 발행](https://github.com/worldbiomusic/Blog/blob/main/Git/github-token.md)
1. `git config --global credential.helper wincred`
2. git에서 push or pull로 연관 작업 실행
3. Access token 입력
4. 유효한 keychain이면 Credential Manager에 git keychain이 자동으로 등록됨


# 참고
- [블로그](https://pinedance.github.io/blog/2019/05/29/Git-Credential)



