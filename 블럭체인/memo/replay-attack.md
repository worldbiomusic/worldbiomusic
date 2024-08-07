### 리플레이 공격 (Replay Attack)

리플레이 공격은 공격자가 유효한 데이터를 가로채서 반복하거나 지연시켜 원래의 유효한 데이터로 인해 예상치 못한 결과를 초래하는 공격 방법

### 블록체인에서의 리플레이 공격

- **발생 상황**: 포크(Fork)된 체인에서 동일한 거래가 유효할 때 발생
- **중복 거래**: 한 체인에서 생성된 거래를 다른 체인에서 재전송

#### 예시
1. 사용자가 포크된 체인 1에서 거래를 생성
2. 공격자가 거래를 가로채서 체인 2에서 재전송
3. 사용자 자산의 의도치 않은 손실 발생

### 영향

- 자산의 이중 사용(double spending) 문제 발생
- 사용자에게 경제적 손실 초래

### 방지 방법

1. **체인 구별(Replay Protection)**
   - 포크 시 거래에 고유한 시퀀스 번호 추가
2. **타임스탬프(Time Lock) 및 시퀀스 넘버**
   - 거래에 타임스탬프나 시퀀스 넘버를 추가하여 이전 거래가 유효하지 않도록 설정
3. **고유한 주소 사용**
   - 포크 이후 각 체인에 대해 고유한 주소 체계 사용
4. **서명 체계 변경**
   - 새로운 체인은 거래 서명 체계를 변경하여 기존 체인에서 유효하지 않도록 설정

### 요약

리플레이 공격은 포크된 블록체인 네트워크에서 발생할 수 있으며, 공격자가 유효한 거래를 다른 체인에서 재전송하여 자산 손실을 초래할 수 있는 공격 방법. 방어 기법으로 체인 구별, 타임스탬프 및 시퀀스 넘버 사용, 고유한 주소 사용, 서명 체계 변경 등이 있음