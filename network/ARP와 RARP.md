참조 링크들을 한번씩 읽어보길 권장합니다.

# ARP와 RARP

### ARP(Address Resolution Protocol)
논리적인 IP 주소를 (망계층), 물리적인 MAC 주소로 (데이터링크 계층) 바꾸어주는 역할을 하는  주소 해석 프로토콜
     
### RARP(Reverse Address Resolution Protocol)
네트워크 계층 프로토콜이기도한데, RARP는 모든 호스트가 서버에서 IP 주소를 가져올 수있게 해주는 TCP / IP 프로토콜이다. 
RARP는 ARP 프로토콜에서 채택되었으며 ARP와 반대임.

### ARP와 RARP의 차이점

- ARP의 완전한 형태는 주소 해석 프로토콜 인 반면, 완전한 형태의 RARP는 역방향 주소 결정 프로토콜이다.

- ARP 프로토콜은 수신자의 물리적 주소를 검색한다. 반면, RARP 프로토콜은 프로토콜의 논리 (IP) 주소를 검색합니다.

- ARP는 32 비트 논리 (IPv4) 주소를 수신기의 48 비트 물리적 주소에 매핑합니다. 반면에 RARP는 48 비트 물리적 주소를 수신기의 32 비트 논리 주소에 매핑합니다.

|비교 근거|ARP|RARP|
|--------|---|---|
|전체 양식|주소 확인프로토콜|역방향 주소 확인 프로토콜|
|기본|리시버의 물리 주소를 얻어 온다|서버에서 컴퓨터의 논리 주소를 검색한다|
|매핑|ARP는 32 비트 논리 (IP) 주소를 48 비트 실제 주소로 매핑한다|RARP는 48 비트 물리적 주소를 32 비트 논리적 (IP) 주소로 매핑한다|

**Reference**

[ARP와 RARP의 차이점](https://ko.gadget-info.com/difference-between-arp)

[ARP 쉽게 이해하기](https://aws-hyoh.tistory.com/entry/ARP-%EC%89%BD%EA%B2%8C-%EC%9D%B4%ED%95%B4%ED%95%98%EA%B8%B0)

[GeeksforGeeks](https://www.geeksforgeeks.org/what-is-rarp/?ref=rp)

[정보통신기술용어해설](http://www.ktword.co.kr/abbr_view.php?nav=1&m_temp1=10&id=421)

작성자 : 은솔

작성일 : 2020-12-04