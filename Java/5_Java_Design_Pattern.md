# 자바 디자인 패턴

소프트웨어를 설계할 때, **특정 맥락**에서 자주 발생하는 고질적 문제들이 또 발생할 때를 대비해 재사용할 수 있는 패턴화 해결안.
`바퀴를 다시 발명하지 마라. (Don't reinvent the wheel.)` 이미 만들어져 있는 걸 다시 만들 필요가 없다는 뜻이다.

## 패턴이란?
- 각기 다른 소프트웨어 모듈이나 기능을 가진 다양한 응용 소프트웨어 시스템들을 개발할 때도 **서로 간에 공통되는 설계 문제가 존재하며 이를 처리하는 해결책 사이에도 공통점**이 있다. **이러한 유사점을 패턴**이라 한다.
- 패턴은 공통의 언어를 만들어주며 팀원 사이의 의사 소통을 원활하게 해주는 아주 중요한 역할을 한다.

## 자바 디자인 패턴의 종류

### GoF 디자인 패턴
- 에리히 감마(Erich Gamma), 리차드 헬름(Richard Helm), 랄프 존슨(Ralph Johnson), 존 블리시디스(John Vissides)로 소프트웨어 개발 영역에서 디자인 패턴을 구체화하고 체계화한 사람들이 만든 패턴.
- 23가지의 디자인 패턴을 정리하고 각각의 디자인 패턴을 생성(Creational), 구조(Structural), 행위(Behavioral) 3가지로 분류했다.

### GoF 디자인 패턴의 분류
<img src="https://gmlwjd9405.github.io/images/design-pattern/types-of-designpattern.png" width ="50%" style="background-color: white;">

### GoF 디자인 패턴의 종류
- 생성(Creational) 패턴
  - 추상 팩토리(Abstract Factory): 구제적인 클래스에 의존하지 않고 서로 연관되거나 의존적인 객체들의 조합을 만드는 인터페이스를 제공하는 패턴
  - 팩토리 메소드(Factory Method): 객체 생성 처리를 서브 클래스로 분리해 처리하도록 캡슐화하는 패턴
  - 싱글턴(Singleton): 전역 변수를 사용하지 않고 객체를 하나만 생성하도록 하며, 생성된 객체를 어디에서든지 참조할 수 있도록 하는 패턴(+데드락 문제)

- 구조(Structural) 패턴
  - 컴포짓(Composite): 여러 개의 객체들로 구성된 복합 객체와 단일 객체를 클라이언트에서 구별 없이 다루게 해주는 패턴
  - 데코레이터(Decorator): 객체의 결합을 통해 기능을 동적으로 유연하게 확장할 수 있게 해주는 패턴

- 행위(Behavioral) 패턴
  - 옵저버(Observer): 한 객체의 상태 변화에 따라 다른 객체의 상태도 연동되도록 일대다 객체 의존 관계를 구성하는 패턴
  - 스테이트(State): 객체의 상태에 따라 객체의 행위 내용을 변경해주는 패턴
  - 전략(Strategy): 행위를 클래스로 캡슐화해 동적으로 행위를 자유롭게 바꿀 수 있게 해주는 패턴
  - 템플릿 메소드(Template Method): 어떤 작업을 처리하는 일부분을 서브 클래스로 캡슐화해 전체 일을 수행하는 구조는 바꾸지 않으면서 특정 단계에서 수행하는 내역을 바꾸는 패턴
  - 커맨드(Command): 실행될 기능을 캡슐화함으로써 주어진 여러 기능을 실행할 수 있는 재사용성이 높은 클래스를 설계하는 패턴

- 기타 패턴
  - 추상 팩토리 패턴(Abstract Factory Pattern)
  - 어댑터 패턴(Adapter Pattern)
  - 프로토 타입 패턴(Prototype Pattern)
  - 빌더 패턴(Builder Pattern)
  - 브릿지 패턴(Bridge Pattern)
  - 퍼사드 패턴(Facade Pattern)
  - 이터레이터 패턴(Iterator Pattern)
  - 프록시 패턴(Proxy Pattern)
  - 컴파운드 패턴(Compound Pattern)
  - 메멘토 패턴(Memento Pattern): 객체를 이전의 상태로 복구시킬 때 쓰는 패턴

등 다양한 패턴이 있다.


## 참고 자료
https://catsbi.oopy.io/344dbe7b-9774-48fc-9c95-b554e9c1c4bc

https://gmlwjd9405.github.io/2018/07/06/design-pattern.html