# SOLID 원칙

## 3.LSP(Liskov Substitution Principle): 리스코프 치환 원칙

> 상위 타입 객체를 하위 타입의 객체로 치환해도 상위 타입을 사용하는 프로그램은 정상적으로 동작해야 한다.
> 상위클래스와 하위 클래스 사이의 행위가 일관성이 있어야 한다.  
> 상위 클래스의 구현 조건 사항 같은 계약사항을 하위 클래스가 따라야 한다.

## \* 표준적인 요구사항과 해당 예제

1.하위형에서 선행 조건(사전조건)은 강화될 수 없다.

```
public void Method(int data)
{
    // 값이 음수여선 안된다.
    if (data < 0) //data파라미터에 유효값이 들어오는지 확인하는 것이 선행조건
    {
    	throw new ArgumentOutOfRangeException("data", "데이터 값은 음수이면 안됩니다.");
    }
}
```

```
public void Method(int data)
{

    if (data <= 0) //0이면 안되는 조건을 추가시켰기 때문에 원칙 위배
    {
    	throw new ArgumentOutOfRangeException("data", "데이터 값은 0보다 커야합니다.");
    }

    // 코드
}
```

2. 하위형에서 후행 조건(사후 조건)은 약화될 수 없다.

```
public int Method_A(int data)
{
    int result;
    // 실행 코드
    if (result < 0){
    	result = 0;
    }
    return result;
}

public void Method_B(Money money, int data)
{
    // 실행 코드
    if (money.Amount < 0)
    {
         throw new ArgumentOutOfRangeException("money", "money.Amount 결과값이 음수 입니다.");
    }
}
```

```
public int Method_A(int data)
{
    int result;
    //기존 음수 조건 제거해서 후행조건 완화함
    return result;
}
```

위 코드는 음수 조건을 리턴해서 Method_A를 호출하는 코드가 오작동을 일으킬 수 있다. 후행조건 완화도 선행조건 추가처럼 프로그램에서 문제를 일으키게 만들 수 있으므로 하지 말아야 할 요구사항인 것이다.

3. 상위형의 불변 조건은 하위형에서 반드시 유지되어야 한다.

```
public class Parent{
    public int Data;
    {get{
         return _data;
        }
        set{
            if (value < 0){
                _data = 0;
                return;
            }
            _data = value;
        }
    }
    protected int _data;
}
```

위 코드는 \_data값이 항상0, 양수를 가지도록 한다.

```
public class Child : Parent{
    public void Method(int data){
        _data = data;
    }
}
```

자식 클래스에서 \_data를 아무런 조건없이 덮어쓰기하고 있다.  
부모 클래스에서 외부로부터 유지하던 불변성이 깨져 프로그램에 문제를 일으키게 된다.

4. 하위형에서는 새로운 예외를 던지면 안된다.  
   자식 클래스의 함수에서는 부모클래스의 함수에서 던지는 예외만 쓸 수 있다.

5. 공변성과 반공변성

- 공변성: B가 A를 상속하는 상속관계 B->A가 존재할 때 C\<T>가 C\<B>->C\<A>를 만족하면 이를 공변성을 띈다 한다.
- 반공변성:B가 A를 상속하는 상속관계 B->A가 존재할 때, C\<T>가 C\<A>->C\<B>를 만족하면 이를 반공변성을 띈다고 한다.

> 공변성 예시

```
public static void Main(){
    //다형성에 의해 Child[]를 Parent[]로 치환할 수 있는 것이 공변성이다.
    Parent[]array = new Child[];
}
public class Parent{}
public class Child:Parent{}
```

> 반공변성 예시

```
public static void Main(){
    //Action<Parent>를 Action<Chlid>로 치환할 수 있는 것이 반공변성이다.
    Action<Parent> parentAction = (parent)=>{};
    Action<Child> childAction = parentAction;

    childAction(new Child());
}
public class Parent{}
public class Child:Parent{}
```

참고자료  
[https://pizzasheepsdev.tistory.com/9]  
작성자: 다정  
작성일: 21.5.14
