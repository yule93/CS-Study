# Garbage Collector
줄여서 GC라고도 불리는 가비지 컬렉터는 *유효하지 않은 메모리(가비지)*를 자동으로 정리해주는 서비스를 말한다. 사용하지 않는 변수, 클래스, 함수를 계속해서 할당한다면 *메모리 누수*에 해당하기 때문에 효율적인 서비스를 위해 주기적으로 검사해 청소하는 것이다.

## Minor GC와 Major GC
JVM의 힙 영역은 처음 설계될 때, 다음의 2가지를 전제(Weak Generational Hypothesis)로 설계되었다.
- 대부분의 객체는 금방 접근 불가 상태(Unreachable)가 된다.
- 오래된 객체에서 새 객체로의 참조는 아주 적게 존재한다.
**즉, 객체는 대부분 일회성이며 메모리에 오래 남아있는 경우는 드물다.** 따라서 객체의 생존 기간에 따라 물리적인 Heap 영역을 나누게 됐고 Young, Old 총 2가지 영역으로 설계됐다. *초기엔 Perm 영역이 있었지만 Java 1.8 버전에서 삭제됐다.*

<img src = "https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fva8qQ%2FbtqUSpSocbS%2FkxTvtnmrdhf4bnVPXth0UK%2Fimg.png">

### Young 영역(Young Generation)
- **새롭게 생성된 객체가 할당(Allocation)되는 영역**
- 대부분의 객체가 금방 Unreachable 상태가 되기 때문에, 많은 객체가 Young 영역에 생성되었다가 사라진다.
- Young 영역에 대한 가비지 컬렉션(Garbage Collection)을 *Minor GC*라고 부른다.

### Young 영역의 구성과 동작 방식
- Eden 영역: 새로 생성된 객체가 할당(Allocation)되는 영역
- Survivor 영역 2개: 최소 1번의 GC 이상 살아남은 객체가 존재하는 영역

새로 생성한 대부분의 객체는 Eden에 위치하며, GC가 발생 후 살아남은 객체는 Survivor 중 하나로 이동된다. **이 때, 하나의 서바이버 영역이 가득 차면 살아남은 객체를 다른 서바이버 영역으로 이동시키고, 가득 찼던 다른 서바이버 영역은 빈 상태가 된다.** 이 과정을 반복해 계속 살아 남은 객체는 Old 영역으로 이동하는 것이다. *중요한 건 서바이버 영역 중 한 개는 반드시 비어 있는 상태로 남아 있어야 한다.*

<img src = "https://d2.naver.com/content/images/2015/06/helloworld-1329-3.png" >

### Old 영역(Old Generation)
- **Young영역에서 Reachable 상태를 유지하여 살아남은 객체가 복사되는 영역**
- Young 영역보다 크게 할당되며, *영역의 크기가 큰* 만큼 가비지는 적게 발생한다. 
- Old 영역에 대한 가비지 컬렉션(Garbage Collection)을 *Major GC 또는 Full GC*라고 부른다.

---

## GC의 동작 방식
Minor와 Magor는 각기 다른 메모리 구조로 돼있어 세부적인 동작 방식이 다르지만, 공통적인 2단계를 거친다.
- **Stop The World**
- Mark and Sweep

### Stop The World
Stop The World는 **가비지 컬렉션을 실행하기 위해 JVM이 애플리케이션의 실행을 멈추는 작업**이다. GC를 실행하는 쓰레드를 제외한 모든 쓰레드들의 작업이 중단되고, GC가 완료되면 작업이 재개된다. 당연히 모든 쓰레드들의 작업이 중단되면 애플리케이션이 멈추기 때문에, GC의 성능 개선을 위해 튜닝을 한다고 하면 보통 stop-the-world의 시간을 줄이는 작업을 하는 것이다. 또한 JVM에서도 이러한 문제를 해결하기 위해 다양한 실행 옵션을 제공하고 있다.

### Mark and Sweep
- Mark: 사용되는 메모리와 사용되지 않는 메모리를 식별하는 작업
- Sweep: Mark 단계에서 사용되지 않음으로 식별된 메모리를 해제하는 작업

## GC의 내용 요약
<img src = "https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FdM4wqf%2FbtqUWs2lW8H%2FGvRECmsUIfZ2jhDoKhSCD0%2Fimg.png">

---

## 참고 자료
https://d2.naver.com/helloworld/1329

https://mangkyu.tistory.com/118