> 쓰레드: 프로세스 내에서 실행되는 여러 흐름의 단위  
  
> 멀티 쓰레드: 프로세스는 1개 이상의 스레드를 가질 수 있는데 이게 멀티 스레드이다.  
하나의 프로그램에서 동시에 여러 개의 일을 수행할 수 있도록 해준다.

![쓰레드](https://magi82.github.io/images/2017-2-6-process-thread/03.png)  
![멀티쓰레드](https://t1.daumcdn.net/cfile/tistory/995444505AD60F8314)  

쓰레드는 프로세스 내에서 각각 Stack만 따로 할당을 받고 Code, Date, Heap영역을 공유한다.  


# 멀티 쓰레드의 장점  
 1. 경제성: 데이터, 메모리 공유로 인한 시스템 자원 소모가 줄어듦(쓰레드간 통신이 필요한 경우에도 쉽게 데이터를 주고받을 수 있음)
 2. 응답성: 프로그램의 일부분(쓰레드)이 중단 되거나 긴 작업을 수행 하더라도 프로그램의 수행이 계속 되어 사용자에 대한 응답성이 증가한다.
 예) 채팅 프로그램을 멀티쓰레드화 하면 채팅의 일부분이 전송이 되지 않거나 큰 파일을 전송하고 있어도 사용자는 다른 스레드를 통해서 다른 사용자와 대화가 가능하다. 
 3. 자원 공유: 쓰레드 간의 통신이 필요한 경우에도 별도의 자원을 이용하는 것이 아니라 전역 변수의 공간 또는 동적으로 할당된 공간인 힙(Heap)영역을 이용해 데이터를 주고받을 수 있다.  
  멀티쓰레드에서는 쓰레드간의 스택영역(메모리의 값이 아닌 주소만 보관)과 힙 영역을 공유한다.

# 멀티 쓰레드의 단점  
 1. 디버깅의 난이도 증가: 멀티쓰레드를 기반으로 할 경우, 동일 자원에 접근할 수 있기 때문에 프로그래밍시 신경을 써줘야 한다.
 2. 동기화 작업 필요: 서로 다른 쓰레드가 데이터와 힙 영역을 공유하기 때문에 어떤 쓰레드가 다른 쓰레드에서 사용중인 변수나 자료구조에 접근해 엉뚱한 값을 읽어오거나 수정할 수 있다. 그래서 동기화 작업이 필요하다  
 +동기화 작업을 제대로 하지 않으면 락 문제가 일어날 수 있고 데이터 병목 현상이 일어날 수 있다. 

 
 읽어볼 만한 자료: [http://tcpschool.com/java/java_thread_multi]  
 작성자: 다정  
 작성일:20201207