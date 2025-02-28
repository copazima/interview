# Call By Value : 값에 의한 호출  

* 함수를 호출 할 때 단순히 값을 함수의 인자로 전달    
함수의 인자값은 매개변수에 복사되는 것이라 인자값과 매개변수는 값을 주고 받은 사이일 뿐 아무런 관계가 없다.  
+ __장점__ : 복사해서 처리하기 때문에 안전하고 원래의 값이 보존이 된다.  
+ __단점__ : 복사를 하기 때문에 메모리가 사용량이 늘어난다.  

```java
class Data {int x;}  

class PrimitiveParamEx{  
  public static void main(String[] args){
    Data d = new Data();
    d.x = 10;
    System.out.println("main(): x="+d.x);
    
    change(d.x);
    System.out.println("After change(d.x)");
    System.out.println("main():x ="+d.x);
  }
  static void change(int x){//기본형 매개변수
  x = 1000;
  System.out.println("change():x="+x);
  }
}
```

* 실행결과 
main(): x = 10  
change() : x = 1000  
After change(d.x)  
main(): x = 10  

# Call By Reference : 참조에 의한 호출    

* 인자로 받은 값의 주소를 참조해서 직접 값에 영향을 준다.  
함수를 호출 할 때 주소값이나 레퍼런스를 함수의 인자로 전달하며 따라서 함수 내에서 함수 외부에 선언된 변수에 직접 접근할 수 있다.  
+ __장점__ : 복사하지 않고 직접 참조를 하기에 빠르다.  
+ __단점__ : 직접 참조를 하기에 원래 값이 영향을 받는다.  

```java
class Data {int x;}
class ReferenceParamEx{
    public public static void main(String[] args) {
        Data d = new Data();
        d.x = 10;
        System.out.println("main():x="+d.x);

        change(d);
        System.out.println("After change(d)");
        System.out.println("main():x="+d.x);

    }
    static void change(Data d){//참조형 매개변수
        d.x = 1000;
        System.out.println("change(): x = "+d.x);

    }
}
```
* 실행결과
main(): x = 10  
change():x = 1000  
After change(d)  
main(): x = 1000  

* 참고 할 자료  
자바의 정석 p265-265 플래시 동영상 PrimitiveParam.exe / ReferenceParam.exe 
[https://github.com/castello/javajungsuk3]  
참고할만한 코드 : https://re-build.tistory.com/3


작성자:다정  
작성일:20201111