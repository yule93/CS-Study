# TCP vs UDP

예전 통신 방법은 `회선 교환 방식`으로 다른 통신을 하고 싶을 때, 회선을 바꿔가며 연결을 했다. 즉, A가 중계국에 B랑 연결해달라 하면 중계국에서 A라벨의 구멍과 B라벨 구멍을 케이블로 연결해줬던 것이다.

하지만 이 방식은 물리적으로 회선을 잡아놓고 하나의 통신만 계속 이어갈 수 있어서 효율이 낮다. 빠르긴 하지만 케이블이 끊기면 연결이 사라져버리기 때문에 전쟁과 같은 긴급 상황에 어울리지 않는 데이터 교환 방식이었던 것이다.

이를 해결하기 위해 나온 방식이 `패킷 교환 방식`이다. 데이터를 잘게 쪼개 여러 개의 회선을 통해 조내는 방법으로, 전체 네트워크가 한 번에 타격되지 않는 이상 모든 데이터가 유실 될 확률이 적다. 또한, 패킷에 목적지를 적어두고 보내기만 하면 되니 회선 사용 효율이 높아진다. 그러나 이 방식에도 **데이터가 제대로 도착했는지 여부가 불분명할 때가 있어 이를 확인하고자 신호/플래그 개념을 사용한다.**

## TCP(Transmission Control Protocol)
  - ARQ: 특정 패킷만 다시 보내라는 신호
  - 시퀀스 번호: 패킷을 쪼갠 순서를 가리키는 정보
  - 슬라이딩 윈도우: 수신 측이 처리할 수 있는 속도를 알려주는 정보

### 헤더 정보
<img src = "https://evan-moon.github.io/static/08849868fcdd6a15a88abb391dccacf7/ee604/thumbnail.png" width = "50%">
<img src = "https://evan-moon.github.io/static/ac69210c44cd473bcb737665d590b124/d9199/tcp-header.png" width = "50%">

## UDP(User Datagram Protocol)



## 참고 자료
https://evan-moon.github.io/2019/11/10/header-of-tcp/