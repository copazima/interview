# 클래스/ 인스턴스/ 필드/ 메서드 용어 개념 



* 클래스: 클래스에는 객체가 가져야 할 구성 멤버가 선언된다. 구성멤버에는 필드, 생성자, 메서드가 있다.  


* 인스턴스: 클래스로부터 객체를 선언하는 과정을 클래스의 인스턴스화라고 한다. 이렇게 선언된 해당 클래스 타입의 객체를 인스턴스라고 한다. 즉, 인스턴스란 메모리에 할당된 객체를 의미한다.
![인스턴스와 클래스의 비교](https://mblogthumb-phinf.pstatic.net/20140327_163/29java_1395846889536LrUiY_PNG/20140327_001318.png?type=w2)


* 필드: 객체의 고유 데이터, 상태 정보, 부품 객체를 저장하는 곳. 선언형태는 변수와 비슷하지만 필드를 변수라고 부르지 않는다.  
필드는 변수와 달리 생성자와 메서드 전체에서 사용되며 객체가 소멸되지 않는 한 객체와 함께 존재한다.


* 메서드: 객체의 동작에 해당하는 중괄호 {}블럭을 말한다.메서드를 호출하게 되면 중괄호 블럭에 있는 모든 코드들이 일괄적으로 실행된다.  
 메서드는 객체간의 데이터 전달의 수단으로 사용된다. 

```java
public class class Name{
    //필드
    int fieldnName;

    //생성자
    ClassName(){}  
    
    //메서드
    void methodName(){}

}
```
참고 자료: 이것이 자바다  
참고 링크:[http://www.tcpschool.com/java/java_class_intro]  
작성자: 다정
작성일:20201118