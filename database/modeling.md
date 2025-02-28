# 기초모델링 / 논리모델링 / 물리모델링
+ ## 모델링
>  해당 문제에 영향을 미치는 여러 변수를 컴퓨터가 이해 가능한 형태로 변환한 것이 모델이고 Computer상에 모델을 설계하고 구현하는 과정을 모델링이라 한다.  

<br>

    ⚙ 데이터 모델링  
    
    물리적인 데이터베이스 모델 구현, 시스템 데이터베이스 반영 과정을 포함한다. 모델링은 시스템의 구체적인 Flow를 정의하는데도 매우 큰 영향을 미친다.  

    데이터 모델링 과정은 개념모델링, 논리모델링, 물리모델링 3가지로 분류하여 순차적으로 데이터 모델링작업을 수행한다.  
  
    개념모델링의 경우 일반적으로 논리모델링과 병행하여 진행하는 경우가 많아 논리모델링, 물리모델링 2개의 모델링 과정으로 이야기 하는 경우도 많다. 
  

+ ## 개념 모델링  

![개념모델링](https://github.com/ksy90101/TIL/blob/master/database/image/db_modelings_1.png?raw=true)  
- 데이터 모델링의 첫 단계. 고객의 요구사항을 수집, 분석해 전체적인 모양을 만듦  
- 핵심적인 엔티티와 그 엔티티 사이의 관계를 도출  
- 사용자가 요구하는 데이터의 범위 및 구조를 용이하게 확인이 가능하며 사용자와 함께 검토를 통해 신규 시스템에 해당 요구사항을 반영할 지 여부를 결정해 개발범위를 정하는데도 도움을 준다.  

[개념모델링 주요 Task]  
- 요구분석  
- 중요 엔티티 선별  
- 엔티티 정의  
- 식별자 정의  
- 엔티티 통합  
- 엔티티 간 관계 도출  

--- 

+ ## 논리 모델링 
![논리모델링](https://github.com/ksy90101/TIL/blob/master/database/image/db_modelings_2.png?raw=true)  
- 개념 모델을 상세화 하는 작업  
- 전체 속성 도출. 개념 모델링 단계에서 도출되지 않은 대부분의 엔티티가 도출되어야 함  
- 논리 모델링의 목적은 비즈니스 요건을 빠짐없이 반영하는 것  
- 논리 모델에는 실체, 행위, 목적, 엔티티 등 모든 엔티티가 도출돼야 하며 시스템 속성을 제외한 전체 속성이 도출돼야 한다. 
- 논레 모델은 모델 중 핵심이며 최종적으로 완료되어 물리적인 스키마 설계를 하기 전 단계의 데이터 모델 상태이다.  
  

[논리모델링 주요 단계]
- 엔티티 정의  
- 관계 도출  
- 속성 도출  
- 주 식별자 확정  
- 정규화  
- 이력 관리  
- 논리 모델 검증  

---
+ ## 물리 모델링  
![물리모델링](https://github.com/ksy90101/TIL/blob/master/database/image/db_modelings_3.png?raw=true)  
- 물리 모델링의 목표는 성능의 최적화
- 논리적 모델을 특정 데이터베이스로 설계함으로써 데이터를 저장할 수 있는 물리적인 스키마를 말한다.  
- 논리모델을 각 DBMS의 특성에 맞게 데이터 베이스 저장 구조(물리 데이터 모델)로 변환하는 것  

[물리 모델링의 주요 Task]  
- 서브타입 모델의 변환  
- 엔티티 합체와 분해  
- 비정규화  
- PK의 확정  
- 테이블 파티션 확정  
- 데이터 저장 방법 확정  
- 인덱스 설계  
- 뷰 설계  
- 시스템 속성 추가
  
<br>
<br>  
  
> 참고자료  
[https://mangastorytelling.tistory.com/entry/03-%EA%B0%9C%EB%85%90-%EB%AA%A8%EB%8D%B8-%EB%85%BC%EB%A6%AC-%EB%AA%A8%EB%8D%B8-%EB%AC%BC%EB%A6%AC-%EB%AA%A8%EB%8D%B8]   
[https://rutgo-letsgo.tistory.com/138]  
[http://www.incodom.kr/%EB%8D%B0%EC%9D%B4%ED%84%B0%EB%AA%A8%EB%8D%B8%EB%A7%81]  
작성자: 다정  
작성일: 20210209






    