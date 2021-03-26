# 조인이란?  
> 두 개 이상의 테이블이나 데이터베이스를 연결하여 데이터를 검색하는 방법. 

# 조인의 종류  
```
1. INNER JOIN  
2. OUTER JOIN  
3. CROSS JOIN  
4. SELF JOIN  
```  

## 1. INNER JOIN  
![INNER](https://github.com/copazima/interview/blob/main/resource/INNER%20JOIN.png?raw=true)  
서로 연관된 내용만 검색하는 조인 방법으로 기존 테이블과 JOIN한 테이블의 중복된 값을 보여준다.  
결과값은 A의 테이블과 B 테이블이 모두 가지고 있는 데이터만 검색된다.  

* <b>명시적 조인 표현</b>  
테이블에 조인하라는 것을 지정하기 위해 'JOIN'키워드를 사용하고 ON의 키워드를 조인에 대한 구문을 지정하는데 사용된다.  
```
SELECT * FROM EMPLOYEE 
INNER JOIN DEPARTMENT ON EMPLOYEE.DEPARTMENTID = DEPARTMENT.DEPARTMENTID;
```  

* <b>암시적 조인 표현</b>  
SELECT 구문의 FROM 절에서 콤마를 사용하여 단순히 조인을 위한 여러 테이블을 나열하기만 하면 된다.  
```
SELECT * FROM EMPLYOEE, DEPARTMENT
WHERE EMPLOYEE.DEPARTMENTID = DEPARTMENT.DEPARTMENTID;
```  

## 2. OUTER JOIN  
조인하는 여러 테이블에서 한 쪽에는 데이터가 있고 한 쪽에는 데이터가 없는 경우, 데이터가 있는 쪽 테이블의 내용을 전부 출력하는 방법이다. 즉, 조인 조건에 만족하지 않아도 해당 행을 출력하고 시을 때 사용할 수 있다.  

* 2-1) LEFT OUTER JOIN  
![LEFT OUTER](https://github.com/copazima/interview/blob/main/resource/LEFT%20OUTER%20JOIN.png?raw=true)  
LEFT OUTER JOIN은 조인문의 왼쪽에 있는 테이블의 모든 결과를 가져온 후 오른쪽 테이블의 데이터를 매칭하고, 매칭 되는 데이터가 없는 경우 NULL을 표시한다.  
```
SELECT
테이블별칭.조회할칼럼,
테이블별칭.조회할칼럼
FROM 기준테이블 별칭
LEFT OUTER JOIN 조인테이블 별칭 ON 기준테이블별칭.기준키 = 조인테이블별칭.기준키


SELECT * FROM 
EMPLOYEE E LEFT OUTER JOIN DEPARTMENT D
ON E.DEPARTMENTID = D.DEPARTMENTID;
```

```
ORACLE
SELECT * FROM 
EMPLYEE E, DEPARTMENT D
WHERE E.DEPARTMENTID = D.DEPARTEMTNID(+);
```  

* 2-2) RIGHT OUTER JOIN  
![RIGHT OUTER](https://github.com/copazima/interview/blob/main/resource/RIGHT%20OUTER%20JOIN.png?raw=true)  
조인문의 오른쪽에 있는 테이블의 모든 결과를 가져온 후 왼쪽의 테이블의 데이털르 매칭하고, 매칭 되는 데이터가 없는 경우 NULL을 표시한다.  
```
SELECT * FROM EMPLYEE E 
RIGHT OUTER JOIN DEPARTMENT D
ON E.DEPARTMENTID = D.DEPARTMENTID;
```

```
ORACLE
SELECT * FROM EMPLOYEE E, DEPARTMENT D
WHERE E.DEPARTMENTID(+) = D.DEPARTMENTID;
```

* 2-3) FULL OUTER JOIN  
![FULL](https://github.com/copazima/interview/blob/main/resource/FULL.png?raw=true)  
합집합. 기준 테이블의 의미 없이 양쪽 테이블 모두 조건이 일치하지 않는 것들까지 모두 결합하여 출력  
```
SELECT
테이블별칭.조회할칼럼,
테이블별칭.조회할칼럼
FROM 기준테이블 별칭
FULL OUTER JOIN 조인테이블 별칭 ON 기준테이블별칭.기준키 = 조인테이블별칭.기준키 .....

SELECT *FROM EMPLOYEE E 
FULL OUTER JOIN DEPARTMENT D
ON E.DepartmentID = D.DepartmentID;

```

MYSQL에서 FULL OUTER JOIN 키워드가 안되므로 이런식으로 하는 것을 참조 
```
SELECT *FROM EMPLOYEE E 
LEFT OUTER JOIN department D
ON E.DepartmentID = D.DepartmentID

UNION SELECT * FROM EMPLOYEE E 
RIGHT OUTER JOIN DEPARTMENT D
ON E.DEPARTMENTID = D.DEPARTMENTID;
```





## 3. CROSS JOIN  
![CROSS](https://github.com/copazima/interview/blob/main/resource/CROSS.jpg?raw=true)  
CROSS JOIN은 카디션곱이라고도 하며 조인되는 두 테이블에서 곱집합을 반환한다.  
즉, 두 번째 테이블로부터 각 열과 첫 번째 테이블에서 각 열이 한 번씩 결합된 열을 만들 것이다. 예를 들어 M열을 가진 테이블과 N열을 가진 테이블이 교차 조인되면 M*N 개의 열을 생성한다. 그래서 테이블의 각 값을 연결해 테이블 행의 수를 모두 곱한 값만큼 만들어진다.  
```
SELECT * FROM EMPLOYEE  
CROSS JOIN DEPARTMENT;
```
EMPLOYEE 테이블의 튜플이 6개이고 DEPARTMENT 테이블의 튜플이 4개면 6*4= 24개의 결과가 나오는 것이다.  

## 4. SELF JOIN  
![SELF](https://github.com/copazima/interview/blob/main/resource/SELF.png?raw=true)  
SELF JOIN은 자기자신과 자기자신을 조인한다는 의미이다.  
하나의 테이블을 여러번 복사해서 조인하는 것. 자신이 가지고 있는 칼럼을 다양하게 변형시켜 활용할 경우에 자주 사용한다.  
```
SELECT 
테이블별칭.조회할칼럼,
테이블별칭.조회할 칼럼
FROM 테이블 별칭, 테이블별칭2
```  
> 참고자료:  
[https://coding-factory.tistory.com/87]  
[https://clairdelunes.tistory.com/22]  
[https://stanleykou.tistory.com/entry/SQL-INNER-%EC%A1%B0%EC%9D%B8%EA%B3%BC-OUTER%EC%A1%B0%EC%9D%B8%EC%9D%B4-%EB%AC%B4%EC%97%87%EC%9D%B8%EA%B0%80%EC%9A%94]  
작성자: 다정  
작성일: 21.3.26
