# PK(Primary Key)와 FK(Foreign Key)

## PK (주키, 주식별자)
Primary key란 행을 고유하게 구분해 주는 최소의 정보입니다. 
모든 테이블에는 primary key가 있어야 하며, 오직 하나의 primary key만 존재할 수 있습니다.
primary key를 기준으로 데이터를 selecct 한다거나 primary key를 기준으로 다른 컬럼(들)의 값을 
update 또는 delete하는 작업이 흔히 수행되기 때문에 테이블에 primary key를 정의해 주면 where 조건절에 primary key가 
SARGs(Search Arguments)로 사용된 쿼리들의 성능은 현저하게 향상됩니다.



- 주 식별자키로 테이블의 모든 데이터를 식별하는 컬럼

- 테이블 생성시 단 한 개의 PK 설정 (고유 인덱스 자동 생성)

- 중복이나 NULL 불가, 단일 값(unique)을 가진다.

- 기본키를 추가할 때에는 기본키가 되는 컬럼 또는 컬럼의 그룹에 대하여 자동으로 단일의 B-트리 인덱스가 생성된다.



## FK (외부키, 외부식별자)

- 테이블간 관계(Relationship)를 의미. 

- 상위 테이블, 참조할 컬럼(참조시 삭제나 변경 불가) 필요.

- 두 테이블 간의 종속이 필요한 관계일 때 접점이 되는 컬럼을 FK로 지정해 서로 참조할 수 있도록 관계를 맺어줌.

- 테이블 간 잘못된 매핑을 방지하는 역할
 


## UNIQUE KEY 
- 중복 값을 허용하지 않는 고유키. 고유 인덱스 생성됨. ex) 주민등록 번호

## NOT NULL  
- null 값을 허용하지 않음

## CHECK  
- 컬럼에 값이 입력되기 전에 조건을 확인한다 (if 조건이 일치한다면, 값을 입력하겠다)


**Reference**

[[DATABASE] 기본키(PK), 외래키(FK)](https://velog.io/@jch9537/DATABASE-PK-FK)

[데이터베이스 테이블 제약조건](https://lovefor-you.tistory.com/261)

[PRIMARY KEY (기본 키) 선택 -1탄](https://blog.naver.com/newcomsa/30082713932)

작성자 : 은솔

작성일 : 2020-12-11