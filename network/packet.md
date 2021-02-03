# 패킷 스니핑

![패킷 스니핑](https://1.bp.blogspot.com/-b5oVrxO8pZA/XW8kOpNJfOI/AAAAAAAAB1Y/bjJQG82oNNY4dxC4ZPiiVG05X7Xw2bM6ACLcBGAs/s640/%25EC%25BA%25A1%25EC%25B2%2598.JPG)  

> 스니핑의 의미  
  
  * 해킹 기법: 네트워크 상에서 다른 상대방의 네트워크 트래픽을 도청하는 과정  

> 스니퍼 

  * 스니핑을 할 수 있도록 하는 도구  

---
![스니핑](https://mblogthumb-phinf.pstatic.net/MjAxNzEwMTJfMjI3/MDAxNTA3ODE0Mjg4MDQ3.T3sgRfTpVMCffJTBEJlttUSAMyUwzgmdKgyjTuvZKa0g.SOX-QssDCw01F-qqk67N4U03yHP_rIX2QT8CxV89o0Ug.PNG.wnrjsxo/image.png?type=w800)
> 스니핑의 원리  

 이더넷 로컬 네트워크 내의 모든 호스트는 동일한 선(wire)을 공유하도록 설계 되었고, 호스트를 식별하기 위해 물리적인 MAC(Media Access Control)주소를 가지게 된다.   
   

전송하는 주체는 자신의 MAC 주소와 수신 주체의 MAC주소, 데이터를 포함하여 전송하게 된다. 같은 네트워크 내의 모든 컴퓨터는 다른 컴퓨터가 통신하는 모든 트래픽을 볼 수 있으나 이럴 경우 관계 없는 트래픽까지 처리해야 하기 때문에 네트워크 성능 저하, 비효율의 문제가 발생한다.  
  
그렇기 때문에 로컬 네트워크 내의 모든 호스트는 수신 MAC 주소를 확인해 본인이 아닐 경우 해당 패킷을 폐기하는 방식인 필터링 기능을 가지고 있다.  
  

로컬 네트워크를 동작하게 만드는 하드웨어 장치인 랜카드의 모드를 Promiscuous로 변경할 경우 모든 패킷을 버리지 않기 때문에 스니핑을 수행하는 공격자는 자신이 가지지 말아야 할 정보까지 모두 받아들이게 된다.
   
  
  
* 참고자료: [https://m.blog.naver.com/PostView.nhn?blogId=wnrjsxo&logNo=221115871221&proxyReferer=https:%2F%2Fwww.google.com%2F]  
[https://korea07.tistory.com/26]  
* 작성자: 다정  
* 작성일: 20210204
  

