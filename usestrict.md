# JS에서 strict mode 사용하기  

## use strict  
* Strict mode의 선언 방식: 스크립트의 시작 or 함수의 시작 부분에 'use strict'를 선언하면 strict모드로 코드를 작성할 수 있다.  
* 이 문구는 ES5부터 적용되는 키워드로 안전한 코딩을 위한 하나의 가이드라인이다.  
strict mode는 JS 시멘틱스에 몇 가지 변경을 일으킨다.  
* strict mode는 코드에 더 나은 오류 검사를 적용하는 방법이다.  
* strict mode는 전체 스크립트 또는 부분함수에 적용 가능하지만 {}괄호로 묶여진 블록문에는 적용되지 않는다. eval코드, Function코드, 이벤트 핸들러 속성,WindowTimers.setTimeout()과 연관된 함수들에 전달된 문자열이 전체 스크립트이며 여기에서 strict mode가 예상대로 동작한다.  
* strict mode는 구문과 런타임 동작을 모두 변경한다.  

## strict mode의 적용시  
1. 기존에는 무시되던 에러들을 throwing 한다.  
2. JS 엔진의 최적화 작업을 어렵게 만드는 실수들을 바로잡는다. strict mode의 코드는 sloppy mode의 동일한 코드보다 더 빨리 작동하도록 만들어진다.  
3. strict mode는 ECMAScript의 차기 버전들에서 정의 될 문법을 금지한다.  

## strict mode 사용시 오류로 변경되는 이전 허용 내용들  
1. 실수로 글로벌 변수를 생성하는 것을 불가능하게 한다. 일반적인 JS에서 변수를 잘못 입력하면 전역 객체에 대한 새 속성이 만들어지고 그대로 "동작"했지만 strict mode에서는 오류를 발생시킨다. 
```
"use strict";
 // 전역 변수 mistypedVariable 이 존재한다고 가정
mistypedVaraible = 17; // 변수의 오타때문에 이 라인에서 ReferenceError 를 발생시킴
```

2. 예외를 발생 시키는 실패를 작업한다. 예를 들어 NaN은 쓸 수 없는 전역변수라 NaN에 할당하는 일반적인 코드는 아무것도 하지 않고 개발자도 실패 피드백을 받지 않는다. strict mode에서 NaN에 할당하는 것은 예외를 발생시킨다. 일반 코드에서 실패 피드백이 발생하지 않는 실패에 대해(쓸 수 없는 전역 또는 프로퍼티에 할당, getter- only 프로퍼티에 할당, 확장 불가 객체에 새 프로퍼티 할당) strict mode에서는 예외를 발생시킨다.  
```
"use strict";

// 쓸 수 없는 프로퍼티에 할당
var undefined = 5; // TypeError 발생
var Infinity = 5; // TypeError 발생

// 쓸 수 없는 프로퍼티에 할당
var obj1 = {};
Object.defineProperty(obj1, "x", { value: 42, writable: false });
obj1.x = 9; // TypeError 발생

// getter-only 프로퍼티에 할당
var obj2 = { get x() { return 17; } };
obj2.x = 5; // TypeError 발생

// 확장 불가 객체에 새 프로퍼티 할당
var fixed = {};
Object.preventExtensions(fixed);
fixed.newProp = "ohai"; // TypeError 발생

```

3. 삭제할 수 없는 프로퍼티를 삭제하려할 때 예외를 발생시킨다.(시도가 어떤 효과도 없을 때)  
```
"use strict";
delete Object.prototype; // TypeError 발생
```

4. Gecko34 이전의 strict mode는 객체 리터럴의 모든 프로퍼티의 이름이 유니크하도록 요구한다. 일반 코드는 프로퍼티의 값이 나중에 정해진 프로퍼티 이름으로 중복할 것이다. 하지만 마지막 인스턴스만 변경했기 때문에 코드를 수정해 마지막 인스턴스를 변경하는 것 이외의 속성 값을 변경하면 복제는 버그의 벡터가 된다. strict mode 프로퍼티 이름을 중복하는 것은 구문 에러이다.  
```
"use strict";
var o = { p: 1, p: 2 }; // !!! 구문 에러
```

5. strict mode는 유니크한 함수 파라미터 이름을 요구한다. 일반 코드에서는 마지막으로 중복된 인수가 이전에 지정된 인수를 숨긴다. 따라서 strict mode에서는 중복 인수명은 구문 에러이다.  
```
function sum(a, a, c){ // !!! 구문 에러
  "use strict";
  return a + b + c; // 코드가 실행되면 잘못된 것임
}
```

6. ECMAScript5 에서의 strict mode는 8진 구문을 금지한다. ECMAScript2015 에서는 접두사 0o를 붙여 8진수를 지원한다.  
```
var a = 0o10; // ES6: 8진수
```

```
"use strict";
var sum = 015 + // !!! 구문 에러
          197 +
          142;
```

7. ECMAScript6의 strict mode는 primitive 값에 프로퍼티를 설정하는 것을 금지한다. strict mode가 아닐 때에는 프로퍼티 설정이 간단히 무시되지만 strict mode에서는 TypeError를 발생 시킨다. 
```
(function() {
"use strict";

false.true = "";         // TypeError
(14).sailing = "home";   // TypeError
"with".you = "far away"; // TypeError

})();
```

## strict mode의 장점  
* 흔히 발생하는 코딩 실수를 잡아 내 예외를 발생 시킨다.  
* 상대적으로 안전하지 않은 액션이 발생하는 것을 방지한다.  
* 정확하게 고려되지 않은 기능들을 비활성화 시킨다.  


> 참고자료  
[https://ithub.tistory.com/162]  
[https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Strict_mode]  
작성자: 다정  
작성일: 21.6.16