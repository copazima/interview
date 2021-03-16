# JVM, JRE, JDK의 차이
  
![WORA](https://github.com/copazima/interview/blob/main/resource/WORA.jpg?raw=true) 
> 자바의 원칙  
WORA: Write once, Run Anywhere  
(한 번 쓰고 모든 곳에서 실행한다)  


![JVM,JRE,JDK](https://github.com/copazima/interview/blob/main/resource/jrejvmjdk.png?raw=true)
## JVM(Java Virtual Machine)
* 운영체제 독립적으로 동작하기 위해 필요(WORA)  
* JVM은 홀로 배포되지 않고 JRE형식으로 배포된다.  
  
  
## JRE(Java SE Runtime Environment)  
* java class libraries, JVM, java class loader를 포함
* JVM이 원활하게 작동할 수 있도록 환경을 맞춰주는 역할을 함  

## JDK(Java Development Kit)  
* 자바 개발 키트, JRE+컴파일러, 디버거등의 개발도구  
* JRE에는 없는 컴파일러를 포함하고 있다.  
* JDK는 폐쇄적 상업코드 기반의 오라클JDK와 오픈소스인 OPEN JDK가 있다. 
* java 11버전부터 JDK만 지원  

> 참고자료:  
[https://medium.com/@pjuyeon25/java-jdk-jre-jvm-%EC%B0%A8%EC%9D%B4-b5a60fe4653]  
[https://m.blog.naver.com/duqrlwjddns1/221770110714]  
[https://arer.tistory.com/156]  
작성자: 다정  
작성일:21.3.16
