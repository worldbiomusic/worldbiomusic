---
title: "data-URI-scheme"
date: 2020-01-01 00:00:00 +09:00
categories: ['컴퓨터', '웹']
tags: [웹]
---

# Data URI scheme
- 웹 페이지나 다른 문서에서 리소스(이미지, CSS, JavaScript 등)를 인라인으로 포함시키기 위한 방법
- 웹 html을 서버로 부터 받아올 때 이미 html내부에 저장되어 있는 코드
- 작은 리소스를 빨리 불러오기 위해 사용 (큰 데이터는 서버로 부터 받는것이 좋음)

## format
`data:[<mediatype>][;base64],<data>`
- `<mediatype>`: 데이터의 형식을 나타내는 MIME 타입 (예: image/png, image/jpeg, text/plain 등). MIME 타입은 해당 데이터가 어떤 형식인지를 나타내는 식별자
- `;base64`: 이 부분은 옵션이며, 데이터가 Base64로 인코딩되어 있음을 나타냅니다. (이 부분이 없는 경우 데이터가 텍스트 형식으로 인코딩되어 있다는 의미)
- `<data>`: 데이터 자체가 인코딩된 문자열 (만약 `image/png` 라면 png형식의 binary data로 저장됨)
