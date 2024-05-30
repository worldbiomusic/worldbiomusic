---
title: "git lfs"
date: 2020-01-01 00:00:00 +09:00
categories: [컴퓨터, Git]
tags: [git, 깃]
---

[git lfs](https://git-lfs.com/)

- 깃에서 대용량 파일을 관리할 때 사용하는 시스템
- 외부 저장소에 파일을 저장하고 포인터로 관리하는 원리


# 사용법
1. `git lfs install`
2. `git lfs track "원하는 파일"`
> 예. `git lfs track "abc"`
> 예. `git lfs track "*.mp4"`
3. git add .gitattributes
> git lfs 세팅을 저장하는 파일

# 주의사항
이전 다른 브런지 또는 이전 커밋 히스토리에 있는 대용량 파일들은 자동으로 관리되지 않음. 그러므로 관리하려면 `git lfs migrate <mode>` 명령어 사용해야 함

**[<mode> 종류](https://github.com/git-lfs/git-lfs/blob/main/docs/man/git-lfs-migrate.adoc?utm_source=gitlfs_site&utm_medium=doc_man_migrate_link&utm_campaign=gitlfs)**  
- import
- export
- info