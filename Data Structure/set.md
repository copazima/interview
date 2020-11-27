# set 자료구조 특징

![set](https://postfiles.pstatic.net/MjAyMDAxMDNfMjMg/MDAxNTc4MDM1ODU4NTky.Kn4t0F-ZpseWfi0YoCA8lDyK5vY_z0rsyGsq9hYVy3wg.DcOcCLBXcXnjs1ZbOWECLOr3fBC9ERnBrv6Aa3Ip950g.PNG.kkkths/image.png?type=w773)  

> set 특징  
* 데이터를 비순차적으로 저장할 수 있는 순열 자료구조  
* 순서 없이 저장됨  
* 수정 가능
* 중복값 저장 불가
* Fast Lookup(특정값을 포함하고 있는지 확인)이 필요할 때 주로 사용  
<br>
<br>

> set 저장 순서  
1. 저장할 요소의 값의 hash 값 구하기  
2. 해시값에 해당하는 공간(bucket)에 값 저장  
<br>
<br>  

> hash set 코드: Set중에 가장 성능이 좋음
```java
class TestSet{
	public static void main(String[] args) {
		HashSet<Integer> test = new HashSet<Integer>();
		test.add(1);
		test.add(2);
		test.add(3);
		test.add(2);
		test.add(9);		
		System.out.println(test);
	}
}
결과값:1,2,3,9 (중복 제거됨)
```
<br>
<br>

> Tree set코드 :저장된 데이터의 값에 따라 정렬됨. HashSet보다 성능이 느림
```java
class TestSet{
	public static void main(String[] args) {
		TreeSet<String> test = new TreeSet<String>();
		test.add("A");
		test.add("D");
		test.add("C");
		test.add("G");
		test.add("Z");
		test.add("F");
		System.out.println(test);
	}
}
결과:A,C,D,F,G,Z (값에 따라 순서를 결정하고 속도가 HashSet보다 느리다.)
```
<br>
<br>

> LinkedHashSet 코드 :연결된 목록 타입으로 구현된 hash table에 데이터 저장. 저장된 순서에 따라 값이 정렬. 셋 중 가장 느림

```java
class TestSet{
	public static void main(String[] args) {
		LinkedHashSet<String> test = new LinkedHashSet<String>();
		test.add("안녕");
		test.add("하세");
		test.add("요");
		test.add("ㅎㅎ");
		test.add("감사");
		test.add("합니다");
		System.out.println(test);
	}
}
결과: 안녕,하세,요,ㅎㅎ,감사,합니다 (순서대로 삽입된다.)
```

> 참고 자료:[https://blog.naver.com/kkkths/221758649384]  
작성자: 다정  
작성일: 20201127