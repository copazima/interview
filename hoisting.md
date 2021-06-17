# JS의 Hoisting  

## 호이스팅 개념  
* 실행 컨텍스트가 활성화 되었을 때 해당 영역에서 변수의 이름을 메모리에 먼저 수집하는 현상  
*JS Parser가 함수 실행 전 해당 함수를 한 번 훑는다.  
*함수 안에 존재하는 변수/함수 선언에 대한 정보를 기억하고 있다가 실행 시킨다.  
*유효 범위: 함수 블록{}안에서 유효  

* 함수 내에서 아래쪽에 존재하는 내용 중 필요한 값들을 끌어올리는 것이다.  
*실제로 코드가 끌어올려지는 것은 아니며, JS Parser 내부적으로 끌어올려서 처리하는 것이다. JS엔진은 스크립트를 가져오면 가장 먼저 코드에서 데이터를 위한 메모리를 설정한다.  
*실제 메모리에는 변화가 없다.  
*함수는 전체 함수에 대한 참조와 함께 저장된다.  
*변수의 경우 ES6 문법인 let과 const는 초기화 되지 않은 채로 저장이 되고, var는 undefined로 저장이 된다. 

* 변수의 범위가 전역 범위인지 함수 범위인지에 따라서 다르게 동작될 수 있다.  
1. 전역범위: 전역 범위에서는 스크립트 단위에서 최상단으로 끌어 올려진다.  
2. 함수범위: 함수 범위에서는 해당 함수의 최상단으로 끌어 올려진다.
> 최상단으로 끌어올려지는 건 변수의 선언과 할당 내용 모두를 끌어올리는 것이 아닌 선언만 끌어 올려지게 된다. 

## 호이스팅 대상  
* var 변수 선언과 함수 선언문에서만 호이스팅이 일어난다.  
*var변수/함수의 선언만 위로 끌어 올려지며, 할당은 끌어 올려지지 않는다.  
*let/const 변수 선언과 함수 표현식에서는 호이스팅이 발생하지 않는다.  

* 호이스팅은 함수 선언문과 함수 표현식에서 서로 다르게 동작하기 때문에 주의해야 한다.  
*변수에 할당된 함수표현식은 끌어 올려지지 않기 때문에 이때는 변수의 스코프 규칙을 그대로 따른다.  

## 호이스팅 예시
* 변수의 호이스팅  
```
 var myname; // [Hoisting] "선언"
  console.log("hello");
  myname = "HEEE"; // "할당"
  let myname2 = "HEEE2"; // [Hoisting] 발생 X
```

* 함수 선언문에서의 호이스팅  
```
/* 정상 출력 */
function printName(firstname) { // 함수선언문 
    var result = inner(); // "선언 및 할당"
    console.log(typeof inner); // > "function"
    console.log("name is " + result); // > "name is inner value"

    function inner() { // 함수선언문 
        return "inner value";
    }
}

printName(); // 함수 호출 
```
```
/** --- JS Parser 내부의 호이스팅(Hoisting)의 결과 - 위와 동일 --- */
/* 정상 출력 */
function printName(firstname) { 
    var result; // [Hoisting] var 변수 "선언"

    function inner() { // [Hoisting] 함수선언문
        return "inner value";
    }

    result = inner(); // "할당"
    console.log(typeof inner); // > "function"
    console.log("name is " + result); // > "name is inner value"
}

printName(); 
```
* 함수 표현식에서의 호이스팅  
함수 표현식은 함수 선언문과 달리 선언과 호출 순서에 따라서 정상적으로 함수가 실행되지 않을 수 있다.  

---
1. 함수 표현식의 선언이 호출보다 위에 있는 경우 - 정상 출력  
```
/* 정상 */
 function printName(firstname) { // 함수선언문
     var inner = function() { // 함수표현식 
         return "inner value";
     }
        
     var result = inner(); // 함수 "호출"
     console.log("name is " + result);
 }

 printName(); // > "name is inner value"
```

```
 /* 정상 */
 /** --- JS Parser 내부의 호이스팅(Hoisting)의 결과 - 위와 동일 --- */
 function printName(firstname) { 
     var inner; // [Hoisting] 함수표현식의 변수값 "선언"
     var result; // [Hoisting] var 변수값 "선언"

     inner = function() { // 함수표현식 "할당"
         return "inner value";
     }
        
     result = inner(); // 함수 "호출"
     console.log("name is " + result);
 }

 printName(); // > "name is inner value"
```

---
2. 함수표현식의 선언이 호출보다 아래에 있는 경우(var변수에 할당)-TypeError  
```
/* 오류 */
 function printName(firstname) { // 함수선언문
     console.log(inner); // > "undefined": 선언은 되어 있지만 값이 할당되어있지 않은 경우
     var result = inner(); // ERROR!!
     console.log("name is " + result);

     var inner = function() { // 함수표현식 
         return "inner value";
     }
 }
 printName(); // > TypeError: inner is not a function
```

```
/** --- JS Parser 내부의 호이스팅(Hoisting)의 결과 --- */
 /* 오류 */
 function printName(firstname) { 
     var inner; // [Hoisting] 함수표현식의 변수값 "선언"

     console.log(inner); // > "undefined"
     var result = inner(); // ERROR!!->pringName이 실행되는 순간 호이스팅에 의해 inner는 undefined로 지정된다. undefined라는 것은 아직은 함수로 인식되지 않고 있다는 것을 의미
     console.log("name is " + result);

     inner = function() { 
         return "inner value";
     }
 }
 printName(); // > TypeError: inner is not a function
``` 
---
3. 함수 표현식의 선언이 호출보다 아래에 있는 경우(const/let 변수에 할당)-ReferenceError  
```
 /* 오류 */
 function printName(firstname) { // 함수선언문
     console.log(inner); // ERROR!! ->inner에 대한 선언이 되어 있지 않기 때문에 inner is not defined 오류 발생
     let result = inner();  
     console.log("name is " + result);

     let inner = function() { // 함수표현식 
         return "inner value";
     }
 }
 printName(); // > ReferenceError: inner is not defined
```

## 호이스팅 우선순위  
- 변수 선언> 함수 선언 
- 함수 선언문>값이 할당되어 있지 않은 변수  
- 값이 할당 되어 있는 변수> 함수 선언문  

## 호이스팅 사용시 주의  
* 코드의 가독성과 유지보수를 위해 호이스팅이 일어나지 않도록 한다.  
-호이스팅을 제대로 모르더라도 함수와 변수를 가급적 코드 상단부에 선언하면, 호이스팅으로 인한 scope 꼬임 현상을 방지할 수 있다.  
-let/const를 사용한다.  

>참고자료  
[https://gmlwjd9405.github.io/2019/04/22/javascript-hoisting.html]  
[https://developer.mozilla.org/ko/docs/Glossary/Hoisting]  
[https://velog.io/@stampid/Hoisting%ED%98%B8%EC%9D%B4%EC%8A%A4%ED%8C%85%EC%9D%B4%EB%9E%80]  
[https://velog.io/@hoo00nn/%ED%98%B8%EC%9D%B4%EC%8A%A4%ED%8C%85Hoisting-%EC%9D%B4%EB%9E%80]  
작성자: 다정  
작성일: 21.6.17

