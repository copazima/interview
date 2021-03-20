# 인덱스에 대해
## 인덱스의 개념  
> 어떤 데이터가 어느 위치에 있다는 정보를 가진 주소록 같은 개념  
>> 일반적인 select쿼리가 실행될 때 먼저 메모리의 데이터베이스 버퍼 캐시를 살펴본다.  
 버퍼 캐시에 자주 사용되는 테이블들이 캐싱되어 있는데 여기서 데이터가 있을 경우에는 바로 찾아 출력하고 없을 경우에도 하드 디스크에 있는 데이터 파일에서 데이터를 찾기 시작한다.  
*인덱스를 사용한다면 이런 과정을 거치지 않고 바로 주소를 통해 찾아간다.  

<br>  

## 인덱스의 생성 원리
> 해당 테이블을 모두 읽고 인덱스를 만드는 동안 데이터가 변경되면 문제가 되므로 해당 데이터들이 변경되지 못하도록 조치한후  *메모리에 정렬하게 된다.  
*메모리: PGA의 Sort Area  
-과정: 전체 테이블 스캔-> 정렬-> Block 기록  

## 인덱스를 생성하는 것이 좋은 컬럼  
* WHERE절이나 join조건 안에서 자주 사용 되는 컬럼  
* null 값이 많이 포함 되어 있는 컬럼  

## 인덱스 사용 단점  
* DML 작업에서의 성능 저하의 원인(Index Split작업이 발생)  
* 잘못된 인덱스 선정은 storage의 낭비를 유발  
* 잘못된 인덱스를 통해 조회 성능 저하 발생

## 인덱스의 종류  
오라클이 제공하는 인덱스 종류는 총 네가지이다. 
* B-TREE INDEX  
* BITMAP INDEX  
* REVERSE KEY INDEX  
* FUNCTION BASED INDEX  
<br>  
일반적으로 가장 많이 사용되는 것은 B-TREE인덱스와 BITMAP인덱스이다.  
<br>

## 데이터 처리 방법  
**OLTP(OnLine Transaction Processing): 실시간 트랜잭션 처리**  
* B-TREE INDEX 많이 사용  
실시간으로 데이터 입력과 수정이 일어나는 환경  
  
**OLAP(OnLine Analytical Processing): 온라인 분석 처리**  
* BITMAP INDEX 많이 사용  
대량의 데이터를 한꺼번에 입력한 후 주로 분석이나 통계 정보를 출력할 때 사용하는 환경  

  
### B-TREE INDEX  
```
B-TREE INDEX의 종류  
- UNIQUE INDEX
- Non UNIQUE INDEX
- Function Based INDEX
- DESCENDING INDEX
- ✨Composite INDEX(결합인덱스)- 참고사이트 하단 확인
```  

![B-TREE](https://github.com/copazima/interview/blob/main/resource/B-TREE%20INDEX.png?raw=true)  
데이터의 값이 종류가 많고 동일 데이터가 적을 경우 사용 하는 인덱스 
 어느 데이터를 엑세스 하더라도 성능이 동일하기 때문에 조회,삭제,추가 등의 작업에 효율적이다.    
실제 테이블의 주소는 Leaf Block들에 전부 들어 있다. 해당 데이터들에 대한 데이터들이 Branch Block과 Root Block에 들어 있다.  
특정 데이터를 찾아야 할 경우 Root Block에서 Branch Block정보를 찾고 그 다음 Leaf Block정보를 찾아가서 해당 데이터의 ROWID를 찾아 데이터가 들어 있는 블록을 메모리로 복사해 온다.   

<br>

### BITMAP INDEX

![BITMAP](https://github.com/copazima/interview/blob/main/resource/BITMAP%20INDEX.png?raw=true)  
데이터의 값이 종류가 적고 동일 데이터가 많을 경우 사용 한다.  
데이터가 있을 경우 있다는 해당 지도 정보를 Bit로 표시한다. 데이터가 있으면 1, 없으면 0으로 표시된다.  
맵은 인덱스 컬럼의 개수만큼 만들어진다. 데이터가 추가 되면 BITMAP INDEX를 전부 수정해야 하고 추가 데이터만큼의 MAP을 추가 해야 한다. 

<br>


### REVERSEKEY INDEX  

연속된 데이터를 관리할 때 이전의 데이터들을 지워버리면 한쪽의 데이터가 삭제되어 인덱스의 밸런스가 깨져 효율이 안좋아진다.  
그 대안으로 해당 컬럼의 값을 뒤집어 그 값을 ROWID와 매칭 시켜 인덱스를 만들면 후에 연속 데이터가 균등하기 지워져서 인덱스의 밸런스가 유지된다. REVERSEKEY INDEX는 오라클 DB 8버전부터 지원한다. 해당 인덱스의 단점은 범위 scan시 인덱스를 이용한 접근이 불가하다. 실제 인접한 것들이 REVERSEKEY INDEX상에서는 서로 인접 되어 저장되지 않기 때문이다. (101,102은 101,201로 저장되기 때문)  

![REVERSE](https://github.com/copazima/interview/blob/main/resource/reverse1.gif?raw=true)  
여기서 사업번호 컬럼의 값이 순차적으로 증가할 경우 가장 우측의 리프블록에 있는 인덱스 엔트리는 계속 순차적으로 insert가 발생하게 되며 최근 데이터가 저장돼 있는 리프블록에 대한 경합이 증가된다.  
![REVERSE](https://github.com/copazima/interview/blob/main/resource/reverse2.gif?raw=true)  
먼저 기존 테이블에 대한 인덱스 키 컬럼의 값을 반대로 변경해 B-TREE 인덱스를 생성한다. 테이블의 데이터 <03550,이가혜>는 인덱스 키 컬럼인 사원번호 컬럼은 반대로 만들어지므로 데이터 값이 <05330,이가혜>로 변경된다.  
해당 데이터는 리버스 키 인덱스에서 인덱스 키 컬럼의 값이 05330으로 변경 돼 사원번호 인덱스에 저장된다.  
이처럼 리버스 키 인덱스는 B-TREE 인덱스와 구조가 같다. 단지 인덱스 키 값만을 반대로 변경해 B-TREE 인덱스를 생성한 것에 불과하다.

<br>

### FUNCTION BASED INDEX
기존의 인덱스가 걸려 있는 컬럼에는 쿼리 조건에 가공이 불가했다. 함수 기반 인덱스는 가공된 상태(함수or계산식)를 인덱스로 만들기 때문에 인덱스를 탈 수 있게끔 해준다. 오라클 8버전부터 이용 가능하다.
```
> 함수 기반 인덱스를 생성하기 위해 필요한 조건
1. Compatible= 8.1.0이상  
2. 매개변수 설정[QUERY_REWRITE_ENABLED=TRUE]  
3. 시스템 권한[QUERY_REWRITE_INTEGRITY=TRUSTED]  
4. 통계 정보 필요: 함수 기반 인덱스 생성하고자 하는 테이블에 통계 정보가 생성돼 있어야 한다.  
```



권순용의 DB 이야기 : 인덱스 종류 이해[http://www.gurubee.net/expert/kwontra]  
권순용의 DB 이야기: 함수형 인덱스: [https://www.kdata.or.kr/info/info_04_view.html?field=title&keyword=%B1%C7%BC%F8%BF%EB%C0%C7%20DB%20%C0%CC%BE%DF%B1%E2&type=techreport&page=1&dbnum=188802&mode=detail&type=techreport]  
결합인덱스: [https://lee-mandu.tistory.com/483]  
인덱스 주의 사항: [https://choko11.tistory.com/entry/%EC%9D%B8%EB%8D%B1%EC%8A%A4-1-%EA%B0%9C%EB%85%90%EC%A2%85%EB%A5%98%EC%A3%BC%EC%9D%98%EC%82%AC%ED%95%AD]  
인덱스 상세 쿼리문: [https://rongscodinghistory.tistory.com/113]  
