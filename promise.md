# 비동기와 Promise의 필요성  
JS에서는 대부분의 작업들이 비동기로 이루어진다. 어떤 작업을 요청하면서 콜백 함수를 등록하면, 작업이 수행되고 나서 결과를 나중에 콜백 함수를 통해 알려주는 식이다. 비동기 작업이 아니더라도 JS에서는 결과를 콜백으로 알려주는 패턴이 흔하게 사용된다. 최근에 프론트엔드의 규모가 커지며 초기처럼 이벤트 발생 후 특정 작업을 콜백 함수로 호출하는 수준보다 코드의 복잡도가 높아졌다. 이런 케이스에서 콜백이 중첩 되는 경우의 문제를 극복하기 위해 Promise 패턴이 제안되어져 왔다.  

 Promise 패턴을 사용하면 비동기 작업들을 순차적으로 진행하거나, 병렬로 진행하는 등의 컨트롤이 보다 수월해지고 코드의 가독성이 좋아진다. 또 내부적으로 예외처리에 대한 구조가 탄탄하기 때문에 오류가 발생했을 때 오류 처리 등에 대해 보다 가시적으로 관리해줄 수 있는 장점이 있다. 

# Promise  
Promise 객체는 비동기 작업이 맞이할 미래의 완료 또는 실패와 그 결과값을 나타낸다.  
Promise는 프로미스가 생성될 때 꼭 알 수 있지는 않은 값을 위한 대리자로, 비동기 연산이 종료된 이후의 결과값이나 실패 이유를 처리하기 위한 처리기를 연결할 수 있도록 한다. 프로미스를 사용하면 비동기 메서드에서 마치 동기 메서드처럼 값을 반환할 수 있다. 다만 최종 결과를 반환하지는 않고, 대신 프로미스를 반환해서 미래의 어떤 시점에 결과를 제공한다.  



대기 중인 프로미스는 값과 함께 이행할 수도, 어떤 오류로 인해 거부될 수도 있다.  
<img src="https://mdn.mozillademos.org/files/8633/promises.png">  

## Promise 기초 예제  
```
//Promise 선언
var_promise = function(param){
    return new Promise(function (resolve, reject){
        //비동기를 표현하기 위해 setTimeout 함수를 사용
        window.setTimeout(function (){
            //파라미터가 참이면
            if(param){
                //해결됨
                resolove("해결 완료");
            }
            //파라미터가 거짓이면
            else{
                //실패
                reject(Error("실패"));
            }
        },3000);
    });
};

//Promise 실행
_promise(true)
.then(function(text){
    //성공시
    console.log(text);
},function(error){
    //실패시
    console.error(error);
})
```
실행 결과는 콘솔 로그로 '해결 완료'가 나온다.  

### Promise 선언부  
> Promise는 다음 중 하나의 상태를 가진다.  
* 대기(pending): 아직 약속을 수행 중인 상태(fulfilled 혹은 rejected가 되기 전)
* 이행(fulfilled): 연산이 성공적으로 완료됨(promise가 지켜진 상태)
* 거부(rejected): 연산이 실패함  
* settled: 약속의 이행여부와 상관 없이 결론이 난 상태  

위의 예제에서 Promise 선언부를 보면, 나중에 Promise 객체를 생성하기 위해 Promise 객체를 리턴하도록 함수로 감싸고 있다.  
Promise 객체만 보면 파라미터로 익명함수를 담고 있고, 익명함수는 resolve와 reject를 파라미터로 받고 있다.  

new Promise로 Promise가 생성되는 직후부터 resolve나 reject가 호출되기 전까지의 순간을 pending 상태라고 볼 수 있다. 이후 비동기 작업이 마친 뒤 결과물을 약속대로 잘 줄 수 있다면 첫번째 파라미터로 주입되는 resolve함수를 호출하고, 실패했다면 두 번째 파라미터로 주입되는 reject 함수를 호출한다는 것이 promise의 주요 개념이다.  

---

### Promise 실행부  
```
_promise(true)
.then(function(text){
    //성공시
    console.log(text);
},function(error){
    //실패시
    console.error(error);
});
```
_promise()를 호출하면 Promise 객체가 리턴된다. Promise 객체에는 정상적으로 비동기작업이 완료되었을 때 호출하는 then이라는 API가 존재한다. 위의 예제는 하나의 then API를 호출해서 비동기 작업이 완료되면 결과에 따라 성공 혹은 실패 메시지를 콘솔로그로 찍어주게 된다.  

then API는 첫번째 파라미터에 성공시 호출할 함수를, 두 번째 파라미터에 실패시 호출할 함수를 선언하면 Promise의 상태에 따라 수행하게 된다.  
앞서 선언부에서 Promise객체를 생성할 때 resolve와 reject 파라미터를 받았는데 그 파라미터가 실행부의 함수와 동일하다. 

>참고자료  
[https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Promise]  
[https://joshua1988.github.io/web-development/javascript/promise-for-beginners/]  
[https://programmingsummaries.tistory.com/325]  
작성자: 다정  
작성일: 21.6.18
