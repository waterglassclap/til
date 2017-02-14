#### 객체의 생성과 삭제

###### Rule 1. 생성자 대신 정적 팩토리 메서드를 사용할 수 없는지 생각해보라

**일반적인 생성자 함수 방식**
```java
public class Test{
public Test(){
...
}
```

**정적 팩토리 메서드 방식**
```java
public class Test{
	private static final Test INSTANCE = new Test();
	
	private test(){}
	
	public static Test getInstance(){
		return INSTANCE;
	}
```
장점 : 
 
* 일반 생성자처럼 클래스 이름을 부여하는게 아니라 함수 기능에 맞는 이름을 부여할 수 있다. (new Test vs Test.getInstance)
* 생성할 때마다 객체를 새로 만들지 않기 때문에, 싱글톤 디자인에 적합
* 코드가 깔끔해질 수 있음

