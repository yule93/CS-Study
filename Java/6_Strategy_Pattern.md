# 전략 패턴(Strategy Pattern)
<img src="https://oopy.lazyrockets.com/api/v2/notion/image?src=https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Fec19f470-8cdd-4beb-929b-f0930dd05b1e%2F_2020-08-06__9.11.52.png&blockId=1ee4fe74-2c92-4e02-a9a9-f22b09b868d7" width = "50%">

여러 알고리즘을 하나의 추상적인 접근점(인터페이스)을 만들어 접근점에서 서로 교환 가능하도록 하는 패턴. 접근점에서 서로 변경(Deligate)이 가능하다.

사용자가 자신에게 맞는 전략을 취사선택해 수행할 수 있게 하는 패턴이다. 예시는 아래와 같다.

```Java
public interface Duck {
  public void quack();
}

public class WhiteDuck implements Duck {
  @Override
  public void quack() {
    System.out.println("하얀 오리 꽉꽉");
  }
}

public class MallardDuck implements Duck {
  @Override
  public void quack() {
    System.out.println("청둥 오리 꽉꽉");
  }
}

public class ChoicdDuck {
  private Duck duck;    // 서비스나 repo 쓰는 것처럼 인터페이스 선언

  public void setDuck(Duck duck) {
    this.duck = duck;
  }

  public void quack() {
    if(duck == null) 
      System.out.println("오리 없다");
    else {
      // 위임(Delegate)
      duck.quack();
    }
  }
}

```