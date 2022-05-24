# Hash 자료구조

## Set과 Map의 차이

## HashSet

## HashMap

## ConcurrentHashMap

## 멀티스레드에서 사용할 때,
위의 세 가지는 조금씩 다른데 **이 차이점은 동기화를 할 때 가장 잘 드러난다.**

HashMap의 경우 `Collections.synchronizedMap(new HashMap<>())` 으로 초기화하지 않을 경우 엔트리 사이즈가 비정상적으로 출력된다.

즉, 동기화 이슈가 있다면 일반적인 HashMap을 사용하기 보다는 HashTable, concurrentHashMap을 사용하는 게 바람직하다.