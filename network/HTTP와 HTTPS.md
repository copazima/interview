# HTTP와 HTTPS의 차이

### HTTP(HyperText Transfer Protocol)
- 웹 서버와 웹 브라우저 사이에 문서를 전송하기 위한 통신규약(Protocol).

- HTTP 서버는 기본 포트인 80번 포트에서 서비스 대기 중이며, 클라이언트(웹 브라우저)가 TCP/UDP 80 포트를 사용해 
연결하면 서버는 요청에 응답하면서 자료(정보)를 전송한다. HTTP는 정보를 '텍스트'로 주로 HTML 문서로 주고 받는다. 
서버에서부터 브라우저로 전송되는 정보가 암호화 되지 않아 데이터가 쉽게 도난당할 수 있는 문제가 있다. 


### HTTPS(HTTP + S(Secure Socket)) 
- HTTP에 SSL(Secure Socket Layer)이나 TLS 프로토콜을 통해 세션 데이터를 암호화하고, TCP/IP 포트 443를 사용한다.

- SSL는 서버와 브라우저 사이에 안전하게 암호화된 연결을 만들수 있게 도와주고, 
서버 브라우저가 민감한 정보를 주고받을 때 이것이 도난당하는 것을 막아준다.

- TLS(Transport Layer Security)는 과거 SSL에서 이름이 변경 된 것이다. 하지만 아직도 SSL이란 명칭이 많이 사용되고 있다.

- HTTPS라하여 무조건 안전한 것은 아니고, 웹 브라우저에서의 구현 정확도와 서버 소프트웨어, 지원하는 암호화 알고리즘에 따라 보안수준이 다르다.
  
- SSL 인증서 구입비용 및 갱신비용이 발생하고 HTTP에 비해 서버 부하가 높아져서 속도가 느려진다. 그럼에도 보안을 위해 사용하는 곳이 많음  



**Reference**

[인터넷 프로토콜 http와 https의 차이는 뭘까?](https://post.naver.com/viewer/postView.nhn?volumeNo=16561296&memberNo=1834)

[Http와 Https차이](https://velog.io/@meekukin/Http%EC%99%80-Https%EC%B0%A8%EC%9D%B4)

[[네트워크]HTTP와 HTTPS의 차이점 그리고 동작 방식](https://devdy.tistory.com/14)

작성자 : 은솔

작성일 : 2020-12-06