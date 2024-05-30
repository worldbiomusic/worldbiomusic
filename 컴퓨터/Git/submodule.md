---
title: "git submodule"
date: 2020-01-01 00:00:00 +09:00
categories: [컴퓨터, Git]
tags: [git, 깃]
---

# 설명
- Git에서 다른 프로젝트의 Github을 참조해서 사용하는 기능이 `submodule`이다


# submodule 제거 순서
1. 프로젝트 폴더로 들어간다
2. `.gitmodules` 파일에서 삭제할 서브모듈 부분을 제거한다
3. `git add .gitmodules`로 .gitmodules가 바뀐것을 stage시킨다
4. `.git/config`에서 삭제할 서브모듈 부분을 제거한다
5. `git rm --cached <제거할 서브모듈 경로>`입력
6. `.git/modules`에 들어가서 삭제할 서브모듈 폴더를 제거한다
7. <제거할 서브모듈 경로>의 폴더를 삭제한다 (서브모듈을 쓰진 않지만, 폴더를 쓰려면 이 폴더 삭제만 안하면 됨)







# 참고
- https://stackoverflow.com/a/1260982/14850276
