# synchronized 키워드


둘 이상의 쓰레드가 공동의 자원(파일이나 메모리 블록)을 공유하는 경우, 순서를 잘 맞추어 다른 쓰레드가 자원을 사용하고 있는 동안 한 쓰레드가 절대 자원을 변경할 수 없도록 해야 한다.  
 한 쓰레드가 파일에서 레코드를 수정하는데, 다른 쓰레드가 동시에 같은 레코드를 수정하면 심각한 문제가 발생할 수 있다. 이런 상황을 처리할 수 있는 한 방법은 관련된 쓰레드에 대한 동기화(synchronization)를 이용하는 것이다.

* synchronization 목적 : 여러 개의 쓰레드가 하나의 자원에 접근하려 할 때 오직 하나의 쓰레드만이 접근 가능하도록 하는 것
<br> 
<br> 
> <b>동기화의 방법  </b>  
synchronization 메서드: 코드를 메서드 수준에서 관리 가능 [메서드 자체에 해당 키워드를 적용]  
synchronization 블럭: 코드를 블럭 수준에서 관리 가능 [메서드 내부에 동기화가 필요한 로직에만 synchronized블럭으로 감싸는 형태]

```java
// 메서드에 사용하는 경우
public synchronized void method() {
	// 코드
}
```

```java
//인스턴스 메서드 안의 동기화 블록
public void add(int value) {
	synchronized(this) {
		this.count += value;
    }
}
```

```java
//스태틱 메서드 안의 동기화 블럭
public class MyClass {

    public static synchronized void log1(String msg1, String msg2){
       log.writeln(msg1);
       log.writeln(msg2);

    public static void log2(String msg1, String msg2){
       synchronized(MyClass.class){
          log.writeln(msg1);
          log.writeln(msg2);  
       }
    }
  }
```


참고할만한 블로그:[https://perfectacle.github.io/2019/03/10/java-synchronized-note/]  
[https://ooeunz.tistory.com/110]  
작성자: 다정  
작성일: 20201202