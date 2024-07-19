# 설명
- 해당 값이 특정 집합에 포함되는지 여부를 해시 함수를 사용한 구조로 빠른 시간과 적은 공간으로 판별하는 알고리즘

# 원리
![1](https://github.com/worldbiomusic/Blog/blob/main/resources/bloom_filter1.png)
![2](https://github.com/worldbiomusic/Blog/blob/main/resources/bloom_filter2.jpg)
- 집합들은 각 해시함수로 bitmap의 비트가 1로 만들어진것이고, 검사할 값도 해시함수로 bitmap에 인덱싱을 해서 1이면 참, 
0이면 거짓을 나타내는 것

# 순서
1. 먼저 여러개의 해쉬함수를 준비하고, 큰 크기의 bitmap(bit array같은것)을 준비한다
2. 집합원소들에 대해 하나씩 모든 해시함수에서 나온값을 bitmap에 1값(참)으로 인덱싱해서 검사 준비를 끝낸다
3. 검사할 원소를 모든 해시함수에 넣어서 나온값을 bitmap에 인덱싱해서 모두 참으로 나온지 검사한다(이 부분은 다르게 튜닝 가능할 듯)

# 장점
- 확률이 100%는 아니지만, 속도와 공간 절약이 많이 됨
- 거짓 부정(false negative) 존재 불가능

# 단점
- 어디까지나 확률을 사용한 알고리즘이므로 100%가 아니다(개수 조절로 확률 조절 가능)
- 해시함수에서 같은것이든 다른것이든 collision이 일어나면 bitmap에 같은 곳으로 인덱싱이 되고 참이 도출되는 거짓 긍정(false positive) 오류가 발생할 수 있다

# 정리
- 해시함수의 collision이 거의 없는것을 아주 제대로 이용한 알고리즘
- 개수를 엄청 늘리면 확률이 더 올라감
- bitmap이 bloom filter라고 불림
- membership test라도고 불림
- 사이즈를 크게 하면 분류를 할 때 높은 확률로 많은 도움이 되므로, 스팸 메일 검사, 스팸 url검사에 사용된다고 함

# 블럭체인에서 사용하는 이유
- SPV노드가 트랜잭션을 검사할 때 merkle branch(merkle path, merkle proof)를 얻기 위해 bloom filter를 만들어서 풀 노드들에게서 빠르게 merkle branch를 얻어내기 위함
- [참고1](https://developer.bitcoin.org/devguide/operating_modes.html#bloom-filters)
- [참고2](https://bitcoinops.org/en/topics/transaction-bloom-filtering/)
- [참고3](https://reference.cash/protocol/spv/bloom-filter)


# 참고
- https://meetup.toast.com/posts/192
- http://www.secmem.org/blog/2019/05/17/bloom-filter/
- https://dashnewskorea.com/%EB%B8%94%EB%A3%B8-%ED%95%84%ED%84%B0bloom-filter%EB%8A%94-%EB%AC%B4%EC%97%87%EC%9D%B4%EB%A9%B0-%EC%96%B4%EB%96%BB%EA%B2%8C-%EC%82%AC%EC%9A%A9%EB%90%98%EB%8A%94%EA%B0%80/









