# SOLID 원칙  

## 4. ISP(Interface Segregation Principle): 인터페이스 분리의 원칙  
> 자신이 사용하지 않는 인터페이스는 구현하지 말아야 한다.  
> 클래스가 사용하는 기능만 제공하도록 인터페이스를 분리하는 것이다. 
> 인터페이스의 단일책임 강조  


## 적용방법  
1. 클래스 인터페이스를 통한 분리  
* 클래스의 상속을 이용해 인터페이스를 나눌 수 있다.  
이와 같은 구조는 클라이언트에게 변화를 주지 않을 뿐 아니라 인터페이스를 분리하는 효과를 갖는다.  
하지만 거의 모든 객체지향 언어에서는 상속을 이용한 확장은 상속받는 클래스의 성격을 디자인 시점에서 규정해 버린다.    
따라서 인터페이스를 상속받는 순간 인터페이스에 예속되어 제공하는 서비스의 성격이 제한된다.  

---

2. 객체 인터페이스를 통한 분리  
*위임(Delegation)을 이용해 인터페이스를 나눌 수 있다.  
*위임: 특정 일의 책임을 다른 클래스나 메소드에 맡기는 것. 만약 다른 클래스의 기능을 사용해야 하지만 그 기능을 변경하고 싶지 않다면, 상속 대신 위임을 사용한다.  



## 적용사례  
<img src="https://github.com/copazima/interview/blob/main/resource/interface_1.PNG?raw=true" width="400" height="300" align="center">

```
interface Animal{
    public void walk();
    public void eat();
    public void fly();
    public void tweet();
    public void talking();
    public void fireFighting();
}

class Person implements Aminal{
    public void walk(){...}
    public void eat(){...}
    public void fly(){...}//인간은 날 수 없음
    public void tweet(){...}//지저귈 수 없음
    public void talking(){...}
    public void fireFighting(){...}
}

class Bird implements Animal {
    public void walk(){...}
    public void eat(){...}
    public void fly(){...}
    public void talking(){...}//새는 대화를 나눌 수 없음
    public void tweet(){...}
    public void fireFighting(){...}//새는 불을 끌 수 없음
}
```
> Animal 인터페이스에 동물과 사람의 기능이 같이 모여있어 각 클래스별로 기능이 분리가 되지 않은 코드를 확인할 수 있다.  

---

<img src="https://github.com/copazima/interview/blob/main/resource/interface_2.PNG?raw=true" width="400" height="300" align="center">

```
interface Animal{ //종 상관없이 동물이면 모두 할 수 있는 기능
    public void walk();
    public void eat();
}

interface Person{//인간만 가능한 기능
    public void talking();
}

interface Bird{//새만 가능한 기능
    public void fly();
}

class fireFighter implements Animal, Person{
    public void walk(){...}
    public void eat(){...}
    public void talking(){...}

    public void fireFighting(){...}
}

class Sparrow implements Animal, Bird{
    public void walk(){...}
    public void eat(){...}
    public void fly(){...}

    public void tweet(){...}
}
```
> 하나의 일반적인 인터페이스보다는 여러 개의 구체적인 인터페이스가 낫다.

### 적용이슈  
1. 기존에 구현된 클라이언트에 변경을 주지 말아야 한다.  
2. 두 개 이상의 인터페이스가 공유하는 부분의 재사용을 극대화 한다.  
3. 서로 다른 성격의 인터페이스를 명백히 분리한다.  


> 참고자료  
[https://www.nextree.co.kr/p6960/]  
[https://gahee0416.tistory.com/8]

작성자: 다정  
작성일: 21.6.6
