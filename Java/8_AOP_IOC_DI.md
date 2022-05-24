# AOP, IOC, DI

- 프레임워크의 등장으로 결합도(낮춰야 되는거)를 낮추고 응집도(높여야 되는거)를 높이기 위해 사용되는 개념이다.
- 서로간의 의존성을 줄이고 재사용성을 높이기 위해 사용된다.
- 특히, **기존에는 개발자가 직접 객체의 생성과 소멸을 제어했는데 DI를 사용해 객체의 생성/소멸/제어를 스프링 컨테이너가 대신 해준다.** 아래 예시와 같이 사용된다.

```Java
@RestController
public class CommunityController {
	private final CommunityService communityService;

  // autowired로 DI 주입
	@Autowired
	public CommunityController(CommunityService communityService) {
		super();
		this.communityService = communityService;
	}
```

## IoC
- Inversion of Control로 제어의 역전을 뜻한다.
- 원래는 객체 생성 및 의존관계 연결의 제어권을 애플리케이션이 갖고 있으나, **IoC 컨테이너와 프레임워크가 모든 권한을 갖게 되면서 객체의 생명주기를 관리**한다.

## DI
- Dependendy Injection으로 의존성 주입을 뜻한다. **객체 자체가 아니라 프레임워크에 의해 객체의 의존성이 주입되는 설계 패턴으로 IoC로써 완성**된다.
- **@Setter, @Inject, @Autowired**와 같이 DI를 주입시키는 어노테이션으로 IoC 컨테이너에 의존성 주입을 하는 것을 말한다.

## AOP
- Aspect Oriented Programming으로 관점 지향 프로그래밍을 뜻한다.
- 반복되는 작업들을 모아서 필요한 적절한 시기에 재사용이 가능하도록 코드 밖에서 개발을 해두고 프록시 개념으로 메서드가 실행되기 전, 후, 실행시점(리액트에는 componentDidMount 등이 여기에 속하겠네요)에 따라 따로 기능을 적용시킨다.

## 참고 자료
https://velog.io/@wlsdud2194/what-is-di