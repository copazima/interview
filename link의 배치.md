# CSS <link>의 배치:\</body>\</head>\<script>

## \<link>를 \<head>\</head> 사이에 쓰기  
> 사이트 UX 최적화에 도움이 되므로 좋은 방법  
* 정보와 정보 표현 방식은 웹사이트에서 가장 필수적인 부분이므로, 두 가지가 우선적으로 로딩됨으로써 유의미한 화면을 빠르게 유저에게 보여줄 수 있다.    (웹사이트 로딩시 HTML과 CSS가 동시에 파싱됨. 각각 DOM,CSSOM을 생성)  

* 스타일이 없는 내용이 잠깐 보이는 현상(flashes of unstyled content:FOUC)을 방지할 수 있다.  

## \<link>를 \<body>\</body> 사이에 쓰기  
> \<head>사이에 css \<link> 태그를 사용할 경우 1. 필요보다 더 많은 css를 다운로드 할 수 있어 전체 내용이 도착하기 전까지 렌더링이 블로킹 됨의 문제 2. 캐시 전략의 비효율 문제가 발생할 수 있다. 

* body에 필요한 css만 다운로드 할 수 있도록 \<link>를 사용하면 페이지에 필요한 css만 다운로드 가능하며 주요 렌더링 과정에서 차단 CSS의 크기가 줄어들고 캐시 전략을 보다 신중하게 선택할 수 있다. 

## \<link>를 \<script>에 사용하기  
브라우저는 현재 실행중인 CSS가 있을 경우 \</script>를 실행하지 않는다.  
스크립트 태그 내에서 CSS가 도착해 파싱되기 전까지 이에 대한 정보를 찾는 경우 JS가 응답하는 내뇽이 잘못될 수도 있다. 이를 방지하기 위해 브라우저는 CSSOM이 구성될 때까지 \</script>를 실행하지 않는다.  
따라서 \</script>내에 css에 의존하는 코드가 없다면 이를 상단에 배치하는 것이 좋다.  
```
<script>
  var script = document.createElement('script')
  script.src = 'analytics.js'
  document.getElementsByTagName('head')[0].appendChild(script)
</script>

<link rel="stylesheet" href="app.css" />
``` 
>CSSOM에 의존하지 않는 자바스크립트는 CSS 이전에 둔다. 

>CSSOM에 의존하는 자바스크립트는 이후에 둔다.  

자바스크립트 중 일부는 CSS에 의존하고 일부는 그렇지 않은 경우에는 두 개로 분할 하면 다운로드와 실행이 모두 최적의 순서로 발생된다.  
```
<!-- This JavaScript executes as soon as it has arrived. -->
<script src="i-need-to-block-dom-but-DONT-need-to-query-cssom.js"></script>

<link rel="stylesheet" href="app.css" />

<!-- This JavaScript executes as soon as the CSSOM is built. -->
<script src="i-need-to-block-dom-but-DO-need-to-query-cssom.js"></script>
```

> 참고자료  
[https://velog.io/@bangina/FE%EB%A9%B4%EC%A0%91%EB%8C%80%EB%B9%84-link-script%ED%83%9C%EA%B7%B8%EC%9D%98-%EB%B0%B0%EC%B9%98]  
[https://yceffort.kr/2021/02/css-and-webpage-performance]  
작성자:다정  
작성일:21.6.13