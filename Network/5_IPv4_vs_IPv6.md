# IPv4 vs IPv6

## IP
- Internet Protocol의 약자로 지정한 IP 주소에 패킷 통신 단위로 데이터를 전달하는 프로토콜.
- 특징으로는 비연결성, 비신뢰성이 있어 보완을 위해 TCP 프로토콜을 같이 사용한다.

### 비연결성
- 패킷을 받을 대상이 없거나 비연결, 서비스 불능 상태여도 패킷을 전송한다.
- 보내고자 하는 대상 서버의 상태를 알 수 없기 때문에 서버에 계속해서 패킷을 보낸다.

### 비신뢰성
- 중간에 패킷의 일부분이 사라지더라도 송신자 입장에서 데이터가 정확하게 갔는지 알 수 없다. **패킷 전달 여부에 대해서 보증하지 않는다.**
- 패킷을 보낸 순서와 받는 순서가 다를 수도 있어 송신자 측에선 `Hello World`를 보냈으나, 수신자 측에선 `World Hello`를 받을 수 있다.

### 프로그램 구분
- 같은 IP를 사용하는 서버에서 통신하는 앱이 여러개일 경우 구분이 어렵다.

## IPv4

### 헤더
<img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbSGzOp%2FbtqKSWLT9iH%2FdypOd7iFYkMQEZnhF7PeY0%2Fimg.png" width="40%" style="background-color: white;">

- VER: 인터넷 프로토콜의 버전을 의미한다. IPv4, IPv5, IPv6 등의 버전이 들어갈 수 있다.
- HLEN: 헤더의 길이이다. 헤더의 길이는 최소 20바이트부터 최대 60바이트의 크기를 가지기에 0부터 15까지의 수를 표현할 수 있는 4비트를 가지고 60바이트까지 표현하기 위해서 4를 곱한다. 0~15 표현 범위에 4를 곱하면 0~60까지를 표현할 수 있다. IPv6에서는 헤더의 크기가 항상 320바이트이기에 이 필드가 없다.
- Service type: IP 데이터그램의 서비스 형태를 알린다.이 필드를 통해 이 패킷이 얼마나 중요하고 긴급한 것인지를 알 수 있기에 QoS(Quality of Service)를 구현할 수 있다. IPv6에서는 Traffic Class로 이름이 바뀌었다. 이 필드는 6비트의 DSCP(Differenctiated Service Code Point)와 2비트의 ECN(Explicit Congestion Notification)라는 필드로 구분된다.
  - DSCP: 서비스 유형을 의미하는 필드이다. 인터넷(Internet)과 지역(Local), 실험 또는 임시적으로 쓰는 패킷인지를 구분 하는 것이 정의되어 있다.
  - ECN: 원래는 경로의 혼잡 정보를 담는 필드로 쓰려고 정의했다고 하는데 지금은 쓰지 않는 필드이다. 어떤 경로의 혼잡 정보를 담는 건지 모르겠다. 인접 라우터의 혼잡 정보인지 종단간 혼잡 정보인지 도통 모르겠다. 추후에 알게 되면 갱신하겠다.
- Total length: 헤더의 크기까지 포함한 IP데이터그램의 크기를 의미한다.
- Identification: IP 데이터그램을 구분하기 위해서 쓴다. 예를 들어 IP 데이터그램이 단편화(fragmentation)되었을 때 단편화된 데이터그램이 원래 어떤 데이터그램에 속해 있는 지를 알 수 있다. IPv6에서는 라우터가 패킷을 단편화하지 않기 때문에 이 필드는 삭제되었다.
- Flags: IP 데이터그램이 단편화됬는지를 나타내는 필드이다. 마찬가지로 IPv6에서는 삭제되었다.
- Fragmentation offset: 단편화된 데이터그램의 순서를 나타낸다. 역시나 IPv6에서는 삭제되었다.
- TTL(Time To Live): 패킷이 라우터를 최대 몇 번 거쳐서까지 살아 남을 것인지를 나타내는 필드이다. 패킷이 라우터를 거칠 때마다 이 필드의 값이 1씩 감소되며 0이 되면 버려진다. 흔히 TTL로 줄여 부른다.
- Protocol: IP 데이터그램의 데이터(페이로드)에 담겨져 있는 상위 계층의 프로토콜을 알려준다. IPv6에서는 Next Header로 이름이 변경되었다.
  - ICMP가 1번, IGMP가 2번, TCP가 6번, UDP가 17번으로 정의되어 있다.
- Header checksum: Header 필드의 오류를 검출할 수 있는 정보가 담긴 필드이다. 하위 계층에서 원홉오류검출을 하고 상위계층에서 종단간오류검출을 하는 데도 불구하고 네트워크 계층의 프로토콜에 이 필드가 있는 이유는 다음과 같다. 과거에는 이웃 노드간 통신 중에 패킷이 깨지는 경우가 너무 빈번하였기에 라우터에서 한번 더 오류검출하기 위해 정의한 필드라고 한다. 현재는 기술이 많이 발전하여 유선에서는 사실 거의 패킷유실(Packet loss)가 발생하지 않는다. 그래서 IPv6에서는 지워진 필드다.
- Source IP address: 패킷을 보낸 노드의 IP 주소가 담긴다.
- Destination IP address: 패킷이 도착해야하는 목적지의 IP 주소가 담긴다.


## IPv6

## 참고 자료
https://xn--3e0bx5euxnjje69i70af08bea817g.xn--3e0b707e/jsp/resources/ipv6Info.jsp

https://engineeringcode.tistory.com/49