# 생성자 함수의 개념  

> 생성자: new 연산자와 같이 사용 되어 클래스로부터 객체를 생성할 때 호출 되어 객체의 초기화를 담당한다. 생성자를 실행시키지 않고는 클래스로부터 객체를 만들 수 없다. 


* 생성자의 조건
1. 생성자 이름 = 클래스 이름
2. 리턴값 없음. void 사용하지 않는다.
3. 모든 클래스에 한 개 이상의 생성자가 필요하다.
---

> 기본 생성자 : 생성자 0개 입력일 때
```java
class Data{
    int value;
    Data(){} // Data클래스의 기본생성자. 컴파일러가 자동 생성해준다.
} 
```

> 생성자 선언 
```java
public class Car{
    //생성자
    Car(String color, int cc){} 
    //아래의 CarEx 클래스에서 생성자를 호출해서   color값은 검정으로
    //cc값은 3000으로 됨
}
```
> 생성자를 호출해서 객체 생성
```java
public class CarEx{
    public static void main(String [] args){
        Car myCar = new Car("검정",3000);
        //Car myCar = new Car(); 기본 생성자 호출 불가능
    }
}
```
---
클래스로부터 객체 생성될 때 기본 초기값 외에 다른 값으로 초기화 하는 방법
1. 필드 선언시 초기값을 주기  
2. 생성자에서 초기값을 주기

> 생성자에서 필드 초기화
```java
public class Korean{
    //필드
    String nation="한국";
    String name;
    String ssn;

    //생성자
    public Korean(String n, String s){
        name = n;
        ssn = s;
    }
}
```
> 객체 생성 후 필드값 출력
```java
public class KoreanEx{
    public static void main(String [] args){
        Korean k1 = new Korean("김코코","951111-1234567");
        System.out.println("k1.name: "+k1.name+"k1.ssn: "+k1.ssn);

        Korean k2 = new Korean("한모모","991119-1234567");
        System.out.println("k2.name: "+k2.name+"k2.ssn: "+k2.ssn);
    }
}
```

> 생성자 오버로딩
```java
public class Car{//오버로딩
    Car(){}
    Car(String model){
        this.model = model;
    }
    Car(String model, String color){
        this.model = model;
        this.color = color;
    }
}

public class CarEx{//객체 생성지 생성자 선택
    public static void main(String[] args){
        Car car = new Car();
        Car car1 = new Car("택시");
        System.out.println("car모델"+car1);

        Car car2 = new Car("택시","주황");
        System.out.println("car모델,색상"+car2);
    }
    
}
```

> 다른 생성자 호출(this)  

생성자 오버로딩이 많아질 경우 생성자 간의 중복된 코드가 발생할 수 있다. 필드 초기화 내용은 한 생성자에만 집중적으로 작성하고 나머지 생성자는 초기화 내용을 가지고 있는 생성자를 호출하는 방법으로 개선할 수 있다. 다른 생성자를 호출할 때는 this() 코드를 사용한다.

```java
public class Car{//다른 생성자 호출하기
    //필드
    String model
    String color;
    int maxSpeed;

    //생성자
    Car(){}

    Car(String model){//가장 아래 생성자 호출
        this(model,"은색",250);
    }
    Car(String model, String color){//가장 아래 생성자 호출
        this(model,color,250);
    }
    Car(String model, String color, int maxSpeed){
        //공통실행 코드
        this.model = model;
        this.color = color;
        this.maxSpeed = maxSpeed;
    }
}

public class carEx{//객체 생성시 생성자 선택
    public static void main(String [] args){
        Car car1 = new Car();
        System.out.println(car1);

        Car car2 = new Car("자가용");
        System.out.println("car2"+car2.model);

        Car car3 = new Car("자가용","빨강");
        System.out.println("car3.model"+car3.model);
        System.out.println("car3.color"+car3.model);

        Car car4 = new Car("택시","검정",200);
        System.out.println("car3.model"+car4.model);
        System.out.println("car3.color"+car4.color);
        System.out.println("car3.color"+car4.maxSpeed);
    }
}

```  
작성자:다정  
작성일:20201119  
참고 자료: 이것이 자바다 