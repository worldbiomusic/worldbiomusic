- MCU = CPU + I/O + Memory 등

- 아두이노 = MCU(마이크로컨트롤러(uC 라고도 부름)) + 부가적인 부품 (전원, 리셋버튼, 핀 등)

- SRAM = cache
- DRAM = memory

- 아두이노는 UART로 통신을 받는데 USB에서 통신이 오면 UART로 방식으로 바꿔주기 위해 USB 커넥터 앞에서 아두이노로
정보를 넘겨주기 전에 USB serial 변환 uC 를 하나 사용

##### processor가 8비트면
> - register = 8bit
> - ram 한개 공간 = 8bit

- 부트로더 = UART로 들어오는 프로그램들을 아두이노의 memory로 올려주는 역할

- 맨 처음 아두이노 부품이 제작된 경우에는 부트로더에 프로그램을 심어주기 위해서 ISP같은 방법으로 업로드한다(?)


- 핀은 uC안에 포트(register)가 많다는 뜻
- 아두이노 메가는 포트가 11개 있음 (1개 포트당 8bit이므로 8개 핀 단자와 소통 가능?) (1bit = 한 개 단자 포트 레지스터로서 사용)

- 왜 철로 되어있는 회로 같은걸 손으로 만져도 정상작동 하나 (사람도 전기 흐르는데)
> 실제로 만져보니까 전구 불 들어왔다 안왔다 함 > 영향을 받음  

- AVR 코드 예시
```yaml
DDRB |= 0x80; (Data direction register B에 첫 비트(10000000)를 or(|)로 변경 (PORTB를 출력으로서 사용한다는 의미))
PORTB |= 0x80; (PORTB에 데이터를 0x80으로 설정)
```

- UART: parallel(병렬) <-> serial(직렬) 변환해주는 장치
- 만약 baud rate가 100이면 clock을 100번씩 작동하게 해서 비트를 1개씩 가져옴/보냄

- 시리얼 버퍼 레지스터: 실제로 데이터 전송받는 곳 (병렬 <-> 직렬) (shift 레지스터와 같은 말(?))
- 시리얼 control 레지스터: baud rate 설정한 값 저장되는 곳(?)


```

    CPU
    

ㅡㅡㅡㅡㅡㅡㅡㅡ
0 0 0 1 0 1 0 1

```
![](shift-register.png)

- 1clock 당 1개의 비트 값을 cpu로 전송해 줌

---

- I2C, XPI: clock단자 선, 데이터 단자 선 두개 사용 (clock 을 이용해서 동기식으로 작동) (MISO (master input/slave output))
- UART: 데이터 단자선만 사용 (clock은 서로 각 컴퓨터에서 맞춰줘야 제대로 데이터를 서로 주고받을 수 있음) (비동기) (rx, tx)

- RS-232: 디프렌셔(?) (선을 두개 써서 서로 전압 차이로 데이터 전송(중간에 전압이 튀어도(?) 서로의 차는 같아서 상관 x))

---

- UART는 1대1 통신이므로 2개 이상을 같이 통신하려면 단자 핀을 이용해야 함 (아두이노에서는 softwareSerial class 사용)


---

# 전기
- 전압: 전하향
- 전류: 전하 흐르는 속도
- 저항: 전하 흐르는 속도 방해하는 것 (예. 저항이 적으면 전류(흐르는 속도)가 강해져서 열이 더 발생)



- 전압 = 전하량 = 세기(강한 정도) 
- 전류 = 움직이는 전하의 양 = 도체의 전자가 잘 움직이는 정도 (구리는 금보다 전자가 잘 안움직여서 전류가 잘 안 통함 = 저항이 구리가 더 크디고 볼 수 있음)
- 모든물체는 분자 > 원자 > 양성자, 중성자, 전자 순으로 나눠서 볼 수 있음
- 전자가 잘 튕겨나가면(움직이면) 도체 아니면 부도체 (예. 리튬은 전자가 3개가 돌고있는데 안에 있는 2개는 안정적이지만 밖에 돌아다니는 1개는 잘 튕겨져서 전기가 잘 흐름)
- 전압은 높은곳에서 낮은곳으로 흐름


- 전구가 타는 이유? (전압이랑 전류랑 저항 때문) 
```yaml
- 전압이 처음에 결정됨
- 그다음에 전선을 타고 들어가서 저항(전선 종류 굵기, 또 다른 저항 부품 등등)에 의해서 전류의 양이 결정됨
- I = V / R
- 만약 전류가 너무 많이 흐르면 전선이 열이 받음 > 녹거나 다른 부품(플라스틱) 등을 녹여서 부품이 고장남
```
- GND를 연결하는 이유 (?)

- 전하량은 전압와 비례

- URAT에서 GND를 서로 연결하는 이유은 rx, tx가 서로 통신할 떄 전압을 맞춰주기 위해서 (전압은 두 곳의 전압 차이를 말하기 때문에 rx, tx의 전압 차이 기준점을 맞춰야 함)

- UART에는 전기신호로 보낼 때, 받을 떄 트랜시버(transceiver)을 사용해서 전기적인 레벨로 변환해서 주고 받음 (트랜시버 규약은 여러개: (e.g. RS-232))

- 디프렌샤? = 두 개 선 같이 보냈을 때 전압이 튀어도? 서로에게 영향을 줘서 받을 때 두개의 선의 전압차로 정보를 판별
```
- RS-232C: 전이중, single ended
- RS-422: 반이중, 디프렌샤
- RS-485: 전이중, 디프렌샤
```

# UART얼 포트
- SBUF: shift register
- SCON: 설정된 baud rate에 맞춰서 SBUF에서 가져오게 도와주는 것 (CPU의 interrupt와 timer 사용해서)

---

- Mega의 이미 존재하는 시리얼 포트들은 이미 UART 장치가 하나씩 모두 달려있음
- Uno의 SoftwareSerial은 마치 디지털로 송수신 하는 과정을 UART의 shift register처럼 동작하게 해서 통신을 함


---

# SPI 통신
- 멀티 통신 (master : slaves(1:n))
- master쪽은 lib이 있는데 slave쪽은 register 접근해야 함








---

ppt 모든 파일 요청 하기


---

- 아두이노의 0번(rx), 1번(tx)핀은 이미 컴퓨터와 통신중이기 때문에, 연결된 상태에서 0, 1번핀을 사용하면 충돌이 일어나기 때문에, SOftwareSerial 사용해야 함

- LCD는 액정을 전기신호로 빛 투과양을 조절함
- 디코더: MCU에서 각 장치로 데이터 보내줄때 분리해주는(?) 약할
- 번지(memory): 위치, 포트 = 글자

---

- 배터리 +, - 극이 있을 때, 실질적인 전자의 흐름은 -극 쪽에서 도선을 타고 +극으로 흐름
- 하지만 양성자에 비해서 전자가 너무 작아서 옛날에 사람들이 전류가 +에서 -로 흐르는것으로 알고 전류(기)는 +극에서 도선을 타고 -극으로 흐르는것으로 착각
> 물리적 이유: 전자의 이동으로 전기가 발생하는것은 맞지만(전자가 많은곳이 전위가 높고, 전기는 기본적으로 전위가 높은곳에서 낮은곳으로 흐름), 다르게 보면 전자 때문에 끌려오는 다른 원자(양성자, 전자)로 사람들이 양성자의 존재만 알던 때에 양성자가끌려오는것을 보고 전기가 +에서 -로 흐른다고 정의해버림  
> 하지만!, 실제로 전기는 흐르는것으로 보면 안될 것같음(방향성이 없음). 왜냐하면 단순히 전자의 적은 앞 또는 뒤 움직임으로 인해서 전기가 발생하는거지, 실질적으로 이동하는 전자입자가 전기가 되는것이 아니기 때문. (단순한 전자의 움직임이 전기 에너지를 발생시키는 것) (전자는 흐름이 있지만, 전기는 흐름이 없고 발생만 한다)

---

- 특정 프로그램 위에서 동작하는 event기반 보다는 하드웨어의 interrupt기반이 훨씬 빠르다(바로 지연없이 되므로)

---

- 전자파 = 전기 + 자기 같이 포함하는 것
