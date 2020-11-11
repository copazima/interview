
# 🎯 주로 사용하는 Java버전과 특징을 설명  <br>
---
국비 교육과정에서 사용했던 버전은 1.8이었고 이후 VSC에서 8버전을 지원하지 않아 현재는 11버전사용중이므로 설명 답변은 1.8과 11버전으로 하겠습니다.<br>  
__참고: 1.8은 32비트 지원 마지막 공식버전/ 썬이 오라클로 인수 된 이후 출시된 첫 버전11은 OracleJDK독점 기능이 OpenJDK에 이식되어 둘이 동일해졌음__  <br>

---
## 버전 1.8의 특징  
<br>
 __람다식의 출현:__ 람다는 함수형 인터페이스를 간편히 구현하는 역할로 함수를 따로 만들지 않고 코드 한줄에함수를 써서 호출하는 방식입니다. <br>
 __stream api:__  컬렉션,  배열등의 저장 요소를 하나씩 참조해서 람다식을 적용해서 반복적으로 처리할 수있도록 해주는 기능입니다.  <br>
 __interface default method:__  자바 1.8에서는 기본 메서드란 개념이 추가되어 하위호환성 문제없이인터페이스에 새로운 메서드를 추가할 수 있게 되었습니다.  <br>
 __날짜와 시간 API의 다양화:__  불변객체로 사용하지 못하고 일관성 없는 요일 상수의 특성을 가지고 있던기존의 Date API가 다양화 되어 LocalDate, Localtime등 여러 개로 분화됐습니다. <br>
 __GC(가비지 컬렉터)의 성능 개선:__   Java7  까지는  new / survive / old/ perm/ native로 메모리영역을구분했습니다. <br>
java 8에서는 new / survive / old / metaspace 로 아키텍쳐가 변경되었고 기존의perm에 저장되어 문제를 유발하던 static obect는 heap으로 옮겨서 GC 대상이 최대한 될 수 있도록 변경되었습니다. <br>  <br>
추후에도 수정이 될 가능성이 적어 보이는 정보는 Native(Metaspace) 로 넣고 사이즈는자동적으로 조정되도록 1.8부터 개선되었습니다.  <br>

---
## 버전 11의 특징<br>
__자바 11버전의 가장 큰 변화는 라이센스 부분이고 이외에는 HTTP클라이언트 표준화 기능추가,  앱실론가비지 컬렉터 등의 추가가 있습니다.__  <br>
 __라이선스 부분:__ .Java 11부터 Oracle JDK의 독점기능이 오픈소스 버전인 OpenJDK에 이식되어OracleJDK와 OpenJDK가 완전히 동일해졌습니다.<br>
 __HTTP클라이언트 표준화 기능추가:__  Java 9, 10에서 HTTP  통신을 위해 사용되었던  jdk.incubator.http패키지가 표준화되어 java.net.http 패키지로 성능이 개선되었습니다. <br>
 __앱실론 가비지:__ 앱실론은 메모리 할당만 처리하고 회수하지는 않는 가비지 컬랙터로 힙이 종료되면 JVM이 종료됩니다. 간단히 작동하고 마치는 테스트처리에 주로 사용됩니다.<br>

---
**참고 링크**  <br>
람다식을 적용한 stream api 관련 코드:https://jeong-pro.tistory.com/165  <br>
1.8버전 이전 날짜 api클래스 문제점:https://jeong-pro.tistory.com/163  <br>
자바 1.8 개선 사항 관련:https://blog.fupfin.com/?p=27  <br>
자바 1.8\-11버전 특징: https://thatisgood.tistory.com/entry/Java-10-버전-특징  <br>
자바 13버전까지 특징 간단 요약:https://i3utterfly.tistory.com/entry/JAVA-%EB%B2%84%EC%A0%84%EB%B3%84-%EC%A0%95%EB%A6%AC?category=831532?category=831532  <br>

---
작성자 : 다정  <br>
작성일 : 20201110
