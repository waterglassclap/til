### How to Catch up

#### 1. RSS
https://feedly.com/i/my

##### Back to the Mac
- http://macnews.tistory.com/rss
- 

- http://feeds.feedburner.com/Bloter

- http://arxiv.org/rss/cs
- http://feeds.dzone.com/home
- https://code.facebook.com/posts/rss
- http://feeds.feedburner.com/GoogleOpenSourceBlog
- https://www.infoq.com/feed
- http://www.itworld.co.kr/rss/feed
- http://feeds.wired.com/wired/index


#### 2. facebook pages



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
// 싱글톤은 객체를 하나만 만들 수 있는 클래스다
* 코드가 깔끔해질 수 있음


#### Rule 2. 생성자 인자가 많을 때는 Builder pattern 적용을 고려하라

#### Rule 3. private 생성자나 enum 타입을 사용해서 싱글톤의 특성을 유지하자

#### Rule 4. private 생성자를 사용해서 인스턴스 생성을 못하게 하자

#### Rule 5. 불필요한 객체의 생성을 피하자

#### Rule 6. 쓸모 없는 객체 참조를 제거하자

- 만기 참조를 제거하는 가장 좋은 방법은 해당 참조가 보관된 변수가 scope를 벗어나게 두는 것이다. 변수를 정의할 때 그 유효범위를 최대한 좁게 만들면 자연스럽게 해결된다.
- 객체 참조를 null 처리하는 것은 규범이라기 보단 예외적인 조치가 되어야 한다.
- 메모리 누수가 흔히 발견되는 또 한 곳은 리스너(listener)등의 callback이다. callback 등록 기능을 제공하는 api를 사용하는 클라이언트가 콜백을 명시적으로 제거하지 않을 경우, 적절한 조치를 취하기 전까지 메모리는 점유된 상태로 남아있게 된다.
- ** garbage collector가 콜백을 즉시 처리하도록 할 가장 좋은 방법은, 콜백에 대한 약한 참조(weak reference)만 저장하는 것이다. WeakHashMap의 키로 저장하는 것이 그 예다 // TODO : Detail

#### Rule 7. 종료자 사용을 피하라.

<br/>


### 모든 객체의 공통 메서드

