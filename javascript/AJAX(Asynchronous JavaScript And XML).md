

![ajax_logo](https://upload.wikimedia.org/wikipedia/commons/thumb/a/a1/AJAX_logo_by_gengns.svg/220px-AJAX_logo_by_gengns.svg.png)

# AJAX(Asynchronous JavaScript And XML)

Ajax에서 가장 중요한 키워드를 꼽으라면 **비동기**일 것 같습니다. 비동기는 간단하게 말하자면 병렬적으로 태스크(task)를 수행하는 것입니다. 기존 웹에서는 클라이언트가 요청하면 서버는 클라이언트가 원하는 정보가 담긴 HTML 전체를 응답해줬습니다.  이런 방식은  일부분 빼고는 다 같은 HTML이라고 하더라도 다시 전체를 리로딩해야 한다는 문제점이 있었습니다.

 이런 문제를 해결하고자 Ajax 비동기 통신을 이용하기 시작했습니다. Ajax는 리로드 없이 클라이언트에게 필요한 정보만을 쏙 바꿔서 화면에 나타낼 수 있습니다. 이 방식이 가능한 이유는 Ajax 비동기 통신이 HTML이 아닌 XML 또는 JSON 데이터를 응답하기 때문입니다.

 Ajax의 한 예가 댓글 기능입니다. 어떤 게시물에 댓글을 달면 페이지 리로딩 없이도 내가 쓴 글을 바로 확인할 수 있습니다. 댓글을 입력하고 확인 버튼을 누르면 Ajax를 이용해서 서버로 댓글 데이터를 보냅니다.  서버는 Http 상태메세지로 성공 여부를 알려주고, 클라이언트는 다시 Ajax 비동기 통신을 이용해서 댓글 목록만 갱신해서 화면에 새 댓글을 보여줍니다. 갱신이 필요한 부분만 갱신할 수 있으니 기존의 방식보다 효율적입니다.

 그리고 또 하나 장점은 하이브리드(hybrid)입니다. 웹 애플리케이션을 안드로이드 앱으로도 만들어야 하는데, 기존 HTML을 응답하는 방식이라면 서버를 새로 만들어야 할 수도 있습니다. 하지만 Ajax를 이용하는 방식으로 만들어졌다면 서버는 HTML이 아닌 데이터를 리턴할 테니, 기존 서버를 그대로 사용할 수 있습니다. 화면 구성은 앱에 맞게 하고, 필요한 데이터만 받아서 사용할 수 있기 때문입니다.

 보통 Ajax는 제이쿼리와 함께 사용합니다. 일단 코드의 양이 줄어들고 브라우저에 국한되지 않고 개발할 수 있기 때문입니다.

장점을 정리하자면 이 정도가 될 것 같습니다.

1. 비동길로 필요한 부분만 갱신하니 빠르다.
2. 새로운 HTML을 작성할 필요가 없다.
3. 편리한 UX를 제공할 수 있다.

단점도 몇 가지 있습니다.

1. 연속으로 요청할 경우, 서버에 부하가 올 수 있습니다.
2. 보안이 취약합니다.
3. 히스토리 관리가 안 된다.(뒤로 가기의 부재)
4. 페이지 로딩이 끝난 것인지, 진행 정보를 파악하기 어렵다.



----

참고



https://coding-factory.tistory.com/143



작성자 - 지훈



작성일 - 20201127
