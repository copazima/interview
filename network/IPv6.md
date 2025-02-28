# IPv4에서 IPv6로 가려는 이유?  

* IPv6의 특징  

| 특징  |      설명    |  
|:----------:|:-------------:|
| **확장된 주소 공간** |  128비트 주소 체계를 사용하는 IPv6는 IPv4의 주소 부족 문제를 해결 |
| **새로운 헤더 포맷** |    헤더를 고정 길이로 변경   |  
| **향상된 서비스의 지원**| IPv6는 트래픽을 효과적으로 분류할 수 있는 기능을 제공|   
| **보안기능** |    확장헤더를 통해서 네트워크 계층에서의 종간단 암호화를 제공   |   
| **주소 자동설정** | 로컬IPv6주소를 LAN상의 MAC주소와 라우터가 제공하는 네트워크 프리픽스에 결합하여 IP주소를 자동 생성 |    

---
<br>

* IPv4와 IPv6의 특징 비교  


| 특징  |      IPv4    |     IPv6    |
|:----------:|:-------------:|:-------------:|
| **주소 길이** | 32비트 |   128비트 |  
| **표시 방법** | 8비트씩 3부분 10진수 표시 |   16비트 8부분 16진수로 표시 | 
| **주소 개수** | 약 43억개 |   2^128개(약 43억x43억x43억x43억) | 
| **주소할당 방식** | A,B,C,D등의 클래스 단위 비순차 할당 |   네트워크 규모, 단말기 수에 따라 순차할당 | 
| **브로드캐스트 주소** | 있음 |   없음(대신, 로컬범위 내에서 모든 노드에 대한 멀티캐스트 주소 사용) | 
| **헤더 크기** | 가변 |   고정 | 
| **QoS제공** | 미흡 |   제공 | 
| **보안** | IPSec프로토콜 별도 설치 |   IPsec자체 지원 | 
| **서비스 품질** | 제한적 품질 보장(Type Of Service에 의한 서비스 품질 일부 지원) |   확장된 품질 보장(트래픽 클래스, 플로우 레이블에 의한 서비스 품질 지원) | 
| **Plug&Play** | 불가(DHCP 이용 시 가능) |   가능 | 

<br>  

> <b>QoS(Quality of Service)</b>는 라우터 또는 스위치가 트래픽 유형을 구별한 후에 적절한 동작을 트래픽에 적용할 수 있도록 해주는 프로세스  

  
  참고자료: [https://blog.naver.com/PostView.nhn?blogId=hai0416&logNo=221566797342&parentCategoryNo=&categoryNo=7&viewDate=&isShowPopularPosts=true&from=search]  
  작성자: 다정  
  작성일: 20210119