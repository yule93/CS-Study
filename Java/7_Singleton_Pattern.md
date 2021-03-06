# 싱글톤 패턴


## 

## 문제점(중요함)

### 멀티스레드의 Deadlock 발생
- 멀티스레드에서 내부에서 호출하는 메서드 중에서 인스턴스의 멤버 변수에 접근할 때는 synchronized 해주어야한다.
- 멀티스레드 환경에서는 singleton 패턴으로 인스턴스를 하나만 생성해서는 병목현상이 일어나므로 되도록 singleton 패턴을 안 쓰는 것이 좋다.
- 서블릿 프로그램에서 서블릿 클래스에 멤버 변수를 정의하지 말라. 서블릿 인스턴스는 컨테이너에서 싱글톤 처럼 동작(한 번 생성한 인스턴스를 재활용)하므로 스레드 경합시 데이터 값을 보장할 수 없기 때문이다.
- 오픈 호출: lock을 확보하지 않은 상태로 메서드 호출 하는 기법
- lock의 시간제한: 암묵적인 락 synchronized 말고 락 시간을 제한할 있는 Lock 클래스의 tryLock 메소드를 사용한다. 
- 순환대기 (circular wait) 예방 : 프로그래밍에서 적용할 수 있는 현실적인 방법이다. 여러가지 아이디어가 있을 수 있지만 핵심은 lock을 걸어주는 타이밍을 잘 조정해 주어서 순환 대기가 발생하지 않게 하는 것이다.
synchronized 동기화 블록 최소화