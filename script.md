# \<script>와 \<script async>,  \<script defer>의 차이  
동적인 웹 어플리케이션을 만들기 위해서는 JavaScript 파일을 불러오는 것이 필수적이다. 하지만 복잡한 비즈니스 로직이 포함된 JavaScript 파일이라면 그 용량이 매우 클 것이다. 따라서 스크립트 파일을 비동기 방식으로 불러오는 방식을 통해 로드 시간을 줄일 수 있다.  

이를 가능하게 만들어주는 \<script> 태그의 속성이 async, defer 이다.

* DOM을 따라 반드시 순서대로 실행되어야 한다면 \<script>  
* DOM이나 다른 스크립트에 의존성이 없고 실행 순서가 중요하지 않은 경우라면 \<script async>
* DOM이나 다른 스크립트에 의존성이 있고 실행 순서가 중요한 경우라면 \<script defer>

---

# \<script>

## 스크립트를 비동기 방식으로 불러와야 하는 경우  
<img src="https://github.com/copazima/interview/blob/main/resource/%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8%20%EB%A1%9C%EB%93%9C%EC%88%9C%EC%84%9C.png?raw=true" width="400" height="200">  

일반적으로 브라우저는 HTML 파일을 읽어온 후 , 위에서부터 아래로 한 줄씩 해석을 시작한다. 중간에 스크립트 파일을 마주하는 경우에는, 해당 파일을 모두 해석하기 전까지 나머지 HTML 렌더를 일시적으로 멈추는데 이로 인해 몇 가지 문제가 발생한다.  


1. 같은 코드임에도 불구하고 위치에 따라 스크립트 동작 여부가 달라질 수 있다. 
```
<script>
  // `null` 의 `innerHTML` 에 접근할 수 없어 에러발생.
  console.log(document.getElementById("hello").innerHTML);
</script>

<div id="hello">안녕하세요</div>

<script>
  // `안녕하세요` 가 출력됨.
  console.log(document.getElementById("hello").innerHTML);
</script>

```

2. 스크립트 파일을 읽는 도중에 DOM 파싱이 멈추기 때문에 용량이 큰 스크립트 파일을 불러올 때 스크립트 아래의 HTML 문서가 제대로 보이지 않게 된다.  
```
<script src="jquery.js">
  // 다운로드 받는 데 10초가 걸리는 JavaScript 파일
</script>

<!-- 아래의 엘리먼트는 JavaScript 파일을 모두 로드한 후에 렌더된다.  -->
<div id="hello">안녕하세요</div>
```

> 브라우저가 스크립트 파일을 병렬로 불러오는 방식으로 DOM 렌더 과정을 막지 않게 선언할 수 있다.  
이를 가능하게 하는 키워드가 async와 defer이다.  

# \<script async>    
<img src="https://github.com/copazima/interview/blob/main/resource/async.png?raw=true" width="400" height="200">  

async 스크립트는 DOM 렌더 과정을 방해하지 않도록 병렬로 로드한다.  
```
<script src="analytics.js" async></script>
```
async 속성 적용하면 스크립트를 불러오는 과정에서 DOM 렌더를 차단하지 않도록 보장한다.  
async 스크립트는 오직 파일을 불러오는 것만 병렬로 실행한다. 파일의 로딩을 마치게 된다면 그 즉시 DOM을 멈추고 async 방식으로 불러온 스크립트 파일의 해석을 시작한다. 때문에 async 속성으로 파일을 불러온다고 해도, 스크립트의 해석이 얼마나 오래 걸릴지는 스크립트 파일의 오버헤드에 달려 있다. 따라서 DOM에 접근하는 스크립트를 async 방식으로 불러오는 것은 권장되지 않는다.  

이러한 특성 때문에 async 스크립트는 실행 순서가 보장되지 않는다. 실행 순서를 조정할 수 없기 때문에 여러 스크립트가 서로 의존성이 있다면 제대로 동작하지 않을 수 있다.  

또한 async 스크립트는 완전히 비동기로 불러오기 때문에, DOM이 모두 로드된 경우 발생하는 DOMContentLoaded 이벤트 콜백으로 로드를 보장할 수 없다. DOM 구성이 끝나기 전에 로그다 완료되었다면 DOMContentLoaded에서 확인할 수 있지만 그렇지 않다면 확인할 수 없다. 

> async 스크립트는 DOM에 직접 접근하지 않거나 다른 스크립트에 의존적이지 않은 스크립트들을 독립적으로 실행해야 할 때 효과적이다. 

# \<script defer>  
<img src="https://github.com/copazima/interview/blob/main/resource/defer.png?raw=true" width="400" height="200">  

defer 스크립트는 DOM 렌더를 방해하지 않고 병렬로 로드한다. defer 스크립트는 모든 DOM이 로드 된 후에야 실행되며 스크립트를 선언한대로 실행 순서가 보장된다.  
또한 defer 스크립트는 단순히 먼저 로드한 스크립트라 하더라도 실행하는 시점을 지연시키는 것이기 때문에 DOMContentLoaded 이벤트가 발생되기 전에 이미 실행된 상태이다.  
이 때문에 기본적으로 DOM의 모든 엘리먼트에 접근할 수 있고, 실행 순서도 보장하기 때문에 가장 범용적으로 사용할 수 있는 속성이다. 또한 스크립트 파일끼리의 의존성이 있는 경우에도 정답이 될 수 있다. 

---

* async와 defer의 공통점  
스크립트를 다운로드하는 동안 문서(HTML)이 중단되지 않는다.  

* async와 defer의 차이점  
async는 스크립트를 다운로드 됐을 때 곧바로 평가 실행하고 defer은 문서(HTML)을 완전히 다 읽은 후에 실행한다.  
async는 먼저 다운로드 된 순서대로 실행하고 defer는 정의된 순서대로 실행된다.  

> 참고자료  
[https://webroadcast.tistory.com/15]  
[https://wormwlrm.github.io/2021/03/01/Async-Defer-Attributes-of-Script-Tag.html]  
작성자: 다정  
작성일: 21.6.12

