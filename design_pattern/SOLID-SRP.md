# SOLID 원칙  

## 1. SRP(Single Responsibility Principle): 단일책임의 원칙  
> - 한 클래스는 단 한가지의 변경 이유만을 가져야 한다.  
> - 하나의 모듈은 오직 하나의 액터에 대해서만 책임져야 한다.  
> - SRP 원리를 적용하면 책임 영역이 확실해지기 때문에 다른 책임의 변경으로의 연쇄작용에서 자유로울 수 있다. 

SRP에 따른 설계를 하면 응집도는 높게, 결합도는 낮게 설계할 수 있게 된다.  
* 응집도: 한 프로그램의 요소가 얼마나 뭉쳐 있는지, 구성 요소들 사이의 응집력을 말한다.  
* 결합도: 프로그램 구성 요소들 사이가 얼마나 의존적인지를 말한다.  

### 장점  
1. 코드의 가독성 향상  
2. 유지보수 용이  
3. 다른 원리들을 적용하는 기초가 된다.  

### 적용방법  
* **여러 원인에 의한 변경(Divergent change)**  
Extract Class를 통해 혼재된 각 책임을 각각의 개별 클래스로 분할하여 클래스당 하나의 책임만을 맡도록 하는 것. 책임만 분리하는 것이 아니라 분리된 두 클래스간의 관계의 복잡도를 줄이도록 설계하는 것.  
 만약 Extract Class된 각각의 클래스들이 유사하고 비슷한 책임을 중복해서 갖고 있다면 Extract Superclass를 사용할 수 있다. 이것은 Extract 된 각각의 클래스들의 공유되는 요소를 부모 클래스로 정의하여 부모 클레스에 위임하는 기법이다. 따라서 각각 Extract Class들의 유사한 책임들은 부모에게 명백히 위임하고 다른 책임들은 각자에게 정의할 수 있다.  

* **산탄총 수술(Shotgun surgery)**  
Move Field와 Move Method를 통해 책임을 기존의 어떤 클래스로 모으거나, 새로운 클래스를 만들어 해결할 수 있다. 산발적으로 여러 곳에 분포된 책임들을 한 곳에 모으면서 설계를 깨끗하게 하여 응집성을 높인다. 

### 예제  
AOP(Aspect Oriented Programming): 여러개의 클래스가 로깅이나 보안, 트랜잭션 같은 부분은 공유하고 있을 수 있다. 이런 부분을 모듈화를 통해 각각 필요한 곳에 위빙해주는 방식을 위해 도입된 AOP 또한 로깅, 보안, 트랜잭션과 같은 부분을 하나의 모듈에 단일책임으로 부여하여 이를 사용하게 할 수 있도록 함으로써 SRP를 지키는 방법이다.  

### 적용사례  
- SRP 적용 전  
```
class Guitar (){
    public Guitar(String serialNumber, double price, Maker maker, Type type, String model, Wood backWood, Wood topWood, int stringNum){
        this.serialNumber = serialNumber;
        this.price = price;
        this.maker = maker;
        this.type = type;
        this.model = model;
        this.backWood = backWood;
        this.topWood = topWood;
        this.stringNum = stringNum;
    }
    private String serialNumber;
    private double price;
    private Maker maker;
    private Type type;
    private String model;
    private Wood backWood;
    private Wood topWood;
    private int stringNum;
}
```
price, Type, model, backWood, topWood, stringNum 등은 모두 특성 정보군으로 변경이 발생할 수 있는 부분이다.  
특성 정보군에 변화가 발생하면 항상 해당 클래스를 수정해야 하는 부담이 발생하게 된다. 

- SRP 적용 후  
```
class Guitar(){
    public Guitar(String serialNumber, GuitarSpec spec){
        this.serialNumber = serialNumber;
        this.spec = spec;
    }
    private String serialNumber;
    private GuitarSpec spec;
    ...
}
class GuitarSpec(){
    double price;
    Maker maker;
    Type type;
    String model;
    ...
}
```
변화가 예상되는 특성 정보군을 분리해서 해당 정보에 변경이 일어나면 GuitarSpec 클래스만 변경하면 된다. 

> 참고자료  
[https://victorydntmd.tistory.com/291]  
[https://velog.io/@kyle/%EA%B0%9D%EC%B2%B4%EC%A7%80%ED%96%A5-SOLID-%EC%9B%90%EC%B9%99-%EC%9D%B4%EB%9E%80]  
[https://www.nextree.co.kr/p6960/]  
작성자: 다정  
작성일: 21.3.30

