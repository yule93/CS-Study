# OSI
OSI는 Open System Interconnection의 약자로 **개방형 시스템간 상호 접속**을 뜻한다.
ISO 국제표준화기구에서 컴퓨터의 통신, 네트워크간 상호 접속 용이를 위해 규정한 네트워크 프로토콜로 표준화, 상호 통신이 가능하게 한다.


## OSI 7계층
<img src="https://miro.medium.com/max/1400/1*tnEkvHfXNnhv7xAthT2sJQ.png" width = "35%">
<img src="https://user-images.githubusercontent.com/33534771/74589801-e603cf00-504b-11ea-862c-765c57d3169b.png" width = "35%">

OSI 7계층은 다음과 같이 이루어져 있다. 이중 1 ~ 3은 Lower Layer, 4 ~ 7은 Upper Layer에 해당되며 각 계층마다 사용하는 프로토콜(통신규약), 기기가 다르다.

```t
Lower Layer
├─ 1계층 - 물리 계층
├─ 2계층 - 데이터 링크 계층
└─ 3계층 - 네트워크 계층(IP)

Upper Layer
├─ 4계층 - 전송 계층(TCP/UDP/SMTP 등)
├─ 5계층 - 세션 계층
├─ 6계층 - 표현 계층(jpg, png같이 파일 형식)
└─ 7계층 - 응용 계층(HTTP, HTTPS 등)
```

### 계층 별 데이터
<img src="https://miro.medium.com/max/1400/1*cGvBcdEgSDfHUHNiSTuaNw.png" width = "70%">

데이터 전송 단위: 비트(1계층)-프레임(2)-패킷(3)-세그먼트&데이터그램(4)-메시지(5, 6, 7)


### 1계층(물리 계층)
하나의 네트워크에서 **기본 네트워크 하드웨어 전송 기술들로 구성된다.** 네트워크의 높은 수준 기능의 논리 데이터 구조를 기초로 하는 필수 계층!
  - 물리적 매체를 통해 비트(Bit)의 흐름을 전송하기 위해 필요한 기능들을 조율하는 계층
  - 사용 장비: **허브(리피터 역할+여러 기기 연결 동시 수행), 리피터(신호 증폭기), 케이블(말 그대로 LAN)**
  - 데이터 전송 단위: 비트
  - 프로토콜: Ethernet, RS-232C, MAC

### 2계층(데이터 링크 계층)
포인트 투 포인트(Point to Point)간 신뢰성 있는 전송을 보장하기 위한 계층으로 **CRC 기반 오류 제어와 흐름 제어가 중요하다.** 네트워크 위의 개체들 간 데이터를 전달하고, 물리 계층에서 발생할 수 있는 오류를 찾아내고 수정하는 데 필요한 기능적/절차적 수단을 제공한다.
  - 오류 없이 한 장치에서 다른 장치로 프레임(비트의 모음)을 전달하는 역할
  - 사용되는 장비: **브릿지, 스위치(L2~L4, L7: 숫자가 커질 수록 비싸고 성능 좋음)**
  - 데이터 전송 단위: 프레임
  - 프로토콜: MAC, PPP, HDLC, Frame_relay, FDDI, ATM 등

### 3계층(네트워크 계층)
**여러개의 노드를 거칠 때마다 경로를 찾아주는 역할을 한다.** 다양한 길이의 데이터를 네트워크를 통해 전달하고, 그 과정에서 전송 계층이 요구하는 서비스 품질(Quality of Service: QOS)을 제공하기 위해 기능적/절차적 수단을 제공한다. 라우팅, 흐름제어, 세그멘테이션(seg~/deseg~), 오류 제어, 인터네트워킹 등을 수행한다.
  - 다중 네트워크 링크에서 패킷을 발신지로부터 목적지로 전달할 책임을 갖는다.
  - 사용되는 장비: **라우터**
  - 데이터 전송 단위: 패킷
  - 프로토콜: IP(Internet Protocol), ICMP(Internet Control Message Protocol: IP에서 신뢰형으로 발전한 프로토콜), IGMP(Internet Group Management Protocol: 호스트가 멀티캐스트 그룹 수성원을 인접한 라우터로 알리는 프로토콜), ARP(Address Resolution Protocol: 논리 주소를 물리 주소로 변환하는 프로토콜)

### 4계층(전송 계층)
양 끝단(End to End)의 **사용자들이 신뢰성 있는 데이터를 주고받을 수 있게 해서 상위 계층들이 데이터 전달의 유효성이나 효율성을 생각하지 않도록 하는 계층.** **시퀀스 넘버 기반의 오류 제어 방식을 사용하며 특정 연결의 유효성을 제어**한다. 일부 프로토콜(TCP같은)은 상태 개념이 있고(stateful), 연결 기반이다.(connection oriented)
  - 전체 메시지를 발신지 대 목적지(End to End)간 제어와 에러를 관리한다.
  - 사용되는 장비: **게이트웨이**
  - 데이터 전송 단위: TCP는 Segment, UDP는 Datagram
  - 프로토콜: TCP, UDP

### 5계층(세션 계층)
**양 끝단의 응용 프로세스가 통신을 관리하기 위한 방법을 제공하는 계층.** 동시송수신 방식(duplex), 반이중 방식(half-duplex), 전이중 방식(full duplex) 통신과 함께, 체크 포인팅과 유휴, 종료, 다시 시작 과정 등을 수행한다.
  - 통신 세션을 구성하는 계층으로, **포트 연결이라고 할 수 있다.**
  - 응용간의 질서 제어
  - 데이터 전송 단위: 메시지
  - 프로토콜: SSH, TLS(보통 HTTPS와 같이 인증이 필요한 응용 계층 프로토콜에 사용되는 )
    - **세션(Session)**

      **네트워크 환경에서 사용자 간 또는 컴퓨터 간 대화를 위한 논리적 연결. 프로세스 사이에 통신을 수행하기 위해 메시지 교환으로 서로를 인식한 후부터 통신을 마칠 때까지의 시간을 일컫는다.**

### 6계층(표현 계층)
**코드 간 번역을 담당해 사용자 시스템에서 데이터의 형식상 차이를 다루는 부담을 응용 계층으로부터 분리한 계층. MIME 인코딩이나 암호화 등 동작이 여기서 이뤄진다.** 예를 들면 ECDIC로 인코딩된 문서 파일을 아스키로 디코딩하는 게 이 계층이 해야할 일이다.
  - 운영체계의 한 부분으로 입출력 데이터를 하나의 표현 형태로 변환한다. 사용자가 이해할 수 있는 포멧 변환을 한다.
  - 데이터 전송 단위: 메시지
  - 프로토콜: JPEG, MPEG, SMB, AFP

### 7계층(응용 계층)
**응용 프로세스와 직접 관계해 일반적 응용 서비스(웹이라던지 게임같이)를 수행한다.** 일반적인 응용 서비스는 관련된 응용 프로세스들 사이의 전환을 제공한다. 예로는 Telnet, SSH, HTTP, SMTP, FTP가 있다.
  - 사용자가 네트워크에 접근할 수 있게 해주는 계층. 직접적 서비스 제공.
  - 데이터 전송 단위: 메시지
  - 프로토콜: DHCP(Dynamic Hosting Configuration Protocol: 호스트의 IP 주소와 각종 TCP/IP 프로토콜의 기본 설정을 클라이언트에게 자동 제공), DNS(Domain Name Service), FTP(File Transfer Protocol), HTTP(HyperText Transfer Protocol)

<img src="https://t1.daumcdn.net/cfile/tistory/26213535565D1D3D3A" width = "50%">

## 참고 자료
http://www.incodom.kr/OSI#h_e0b94db87bcbb287fcabaf91095249db

https://m.blog.naver.com/soojin_2604/221961003092

https://medium.com/harrythegreat/osi%EA%B3%84%EC%B8%B5-tcp-ip-%EB%AA%A8%EB%8D%B8-%EC%89%BD%EA%B2%8C-%EC%95%8C%EC%95%84%EB%B3%B4%EA%B8%B0-f308b1115359
<<<<<<< HEAD

https://hahahoho5915.tistory.com/12
=======
>>>>>>> b78c4287c298d1bae0fd7c6ae24506fc7dc41705
