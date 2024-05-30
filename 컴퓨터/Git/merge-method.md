---
title: "git merge 전략"
date: 2020-01-01 00:00:00 +09:00
categories: [컴퓨터, Git]
tags: [git, 깃]
---

# 설명
- Merge에는 간단하게 3가지 방법을 볼 수 있다
1. `일반 merge`: 가장 기본적인 방법으로 branch가 분기되었던 기록이 남고, 다시 병합되는 것까지 기록 됨
2. `squash and merge`: branch가 분기되었던 기록이 없고, 분기되서 작업했던 커밋들을 모두 1개의 커밋으로 압축시켜서 main으로 병합됨
3. `rebase and merge`: `squash and merge`방법과 비슷하지만, 분기되서 작업했던 커밋들이 압축되지 않고, 그대로 main으로 병합됨

# 요약
![image](https://user-images.githubusercontent.com/61288262/188128635-6f2ac377-25b0-47d1-b930-b1c2213b9f28.png)

---

# 이미지
![image](https://user-images.githubusercontent.com/61288262/158950532-81130b0d-e581-45b7-b03c-5161aad7a7ca.png)
![image](https://user-images.githubusercontent.com/61288262/158950577-73e4166d-f5af-42c8-b1e1-196c81452c27.png)

## 일반 merge
![image](https://user-images.githubusercontent.com/61288262/158950586-90425e4e-8652-434d-9b31-2e3f1ebee1ba.png)

## squash and merge
![image](https://user-images.githubusercontent.com/61288262/158950599-8ffc414a-d467-45b4-9205-e0c9cf5447b5.png)

## rebase and merge
![image](https://user-images.githubusercontent.com/61288262/158950607-84a2602c-f149-4ca6-ad1a-ce6438dfb29f.png)




# 참고
- [tistory](https://im-developer.tistory.com/182)

