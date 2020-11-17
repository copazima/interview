# 함수형 언어(Lisp,Haskell,Scala...) 에서 자주 사용되는 용어

### 순수함수 / 일급 객체 / 불변성  

1. 불변성 (side effect가 없음)  
함수형 언어는 대입문이 없어 변수에 값이 할당되면 그 이후 절대 변하지 않는다.  
  (javaScript는 가능하지만 불가능한 언어들이 있다) 그래서 순수 함수를 지향하는 프로그래밍 언어라고 설명하기도 한다.  
함수 호출은 함수의 결과 계산 외에 다른 효과는 없기 때문에, 함수의 실행 순서는 중요하지 않게 되며 프로그램의 검증이 쉬워 동작을 예측하기 수월하다.  
  ** side effect: 함수 내부에서 인자값을 변경하거나 프로그램 상태를 변경하는 것
```java
// 불변이 아닌 변하는(Mutatable) 데이터
function rateColor(color, rating) {
  color.rating = rating;
  return color;
}

console.log(rateColor(color_lawn, 5), rating) // 5
console.log(color_lawn.rating) // 5

// 불변성 데이터
function rateColor(color, ratring) {
  return Object.assign({}, color, {ratring:ratring});
}

console.log(rateColor(color_lawn, 5), rating) // 5
console.log(color_lawn.rating) // 0  *변하지 않음*
```

2. 순수 함수  
순수 함수는 동일한 입력에는 항상 같은 값을 반환해야 하고  
함수의 실행은 Side effect가 없어야 한다.
```java
// 순수하지 않은 함수, DOM을 변경하는 부수효과를 발생시킴
function Header(text) {
  let h1 = document.createElement('h1');
  h1.innerText = text;
  document.body.appendChild(h1);
}

// 순수한 함수, 부수효과를 발생시키지 않음
// DOM을 변경하는 책임은 애플리케이션의 다른 부분이 담당하도록 한다.
const Header = (props) => <h1>{props.title}</h1>
```

3. 1급 객체  
1급 객체를 충족시키는 요건으로는 세 가지 정도를 들 수 있다.  
첫째, 변수나 데이터에 할당할 수 있어야 한다.  
둘째, 파라미터로 전달할 수 있다.  
셋째,반환값(return value)로 사용할 수 있음을 들 수 있다.  
  함수를 하나의 값처럼 다룰 수 있기 때문에 객체지향 패러다임에서 클래스를 재사용하는 것처럼 함수를 재사용할 수 있다.   
자바스크립트에서 함수(Function)은 객체(Object)이므로 1급 함수로 불린다.  


작성자: 다정  
작성일:20201117  
참고 블로그: 1급객체란?:[https://medium.com/@lazysoul/functional-programming-%EC%97%90%EC%84%9C-1%EA%B8%89-%EA%B0%9D%EC%B2%B4%EB%9E%80-ba1aeb048059]  
함수형 프로그래밍에 필요한 개념:[https://velog.io/@kyusung/%ED%95%A8%EC%88%98%ED%98%95-%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%98%EB%B0%8D-%EC%9A%94%EC%95%BD]