---
title: "PYTHONPATH"
date: 2020-01-01 00:00:00 +09:00
categories: ['컴퓨터', 'python']
tags: [python]
---

파이썬은 실행할 때 외부 모듈을 임포트하기 위한 기본 path를 현재 파일과 기본 라이러리를 참조한다.

만약 다른 폴더의 파일을 import해서 실행하려면 `PYTHONPATH`에 디렉토리를 등록해야 함
(PyCharm과 같은 IDE는 프로젝트폴더와 venv를 자동으로 등록해놓아서 사용가능한 것)

---

# 등록하는 법
**디렉터리 예시 구조**  
```
/a/p.py
/a/b/p2.py
```
위와 같이 있고 p.py에서 밑과 같이 p.py에서 p2.py를 import하려할 때 PYTHONPAHT를 `/a`로 등록해주어야 한다.
```py
from b import p2
```

리눅스에서는 하위쉘에서 파이썬을 실행하므로 export가 필요함
```sh
PYTHONPATH=$PYTHONPATH:/a
export PYTHONPATH
```