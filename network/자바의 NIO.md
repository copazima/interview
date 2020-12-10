I/O 멀티플렉싱(multiplexing)에 대한 개념에 대해 아직 잘 이해하지 못하고 있다면 먼저 [멀티플렉싱 기반의 다중 접속 서버로 가기까지](https://jongmin92.github.io/2019/02/28/Java/java-with-non-blocking-io/) 포스팅을 읽어주세요.

[Java NIO와 멀티플렉싱 기반의 다중 접속 서버](https://jongmin92.github.io/2019/03/03/Java/java-nio/) 글의 원문을 꼭 읽어보길 추천합니다.

# Java의 NIO

자바 NIO (New IO)는 기존의 자바 IO API가 (IO프로세스를 거치는 동안 작업을 요청한 쓰레드는 블록킹되는 문제점을 Non-blocking IO(NIO)를 사용해서 블록킹되는 문제를 개선) 대체하기 위해 자바 1.4부터 도입됐다.

자바 NIO는 다음과 같은 핵심 컴포넌트로 구성되어있다.

- Channels
- Buffers
- Selectors

### Channels

- NIO의 모든 IO는 채널로 시작한다. 채널 데이터를 버퍼로 읽을 수 있고, 버퍼에서 채널로 데이터를 쓸 수 있다.

- 채널을 통해서는 읽고 쓸 수 있지만, 스트림은 일반적으로 단방향(읽기 혹은 쓰기)으로만 가능하다.

- 네이티브 IO , Scatter/Gather 구현으로 효율적인 IO처리 (시스템 콜 수 줄이기, 모아서 처리하기)

- 비동기적(asynchronously)으로 읽고 쓸 수 있다.


### BUffers

- NIO의 버퍼는 채널과 상호작용할 때 사용됨. 데이터는 채널에서 버퍼로 읽혀지거나, 버퍼에서 읽혀 채널로 쓰여진다.

- 커널에 의해 관리되는 시스템 메모리를 직접 사용할 수 있는 Buffer 클래스
  

### Selectors

- 셀렉터를 사용하면 하나의 스레드가 여러 채널을 처리(handle)할 수 있다.

- 네트워크 프로그래밍의 효율을 높이기 위한 것
  
- 클라이언트 하나당 쓰레드 하나를 생성해서 처리하기 때문에 쓰레드가 많이 생성될 수록 급격한 성능 저하를 가졌던 단점을 개선하는 Reactor패턴의 구현체
  
  
  

**Reference**

★[Java NIO와 멀티플렉싱 기반의 다중 접속 서버](http://jongmin92.github.io/2019/03/03/Java/java-nio/)

[자바 NIO 정리 #1 개요](https://jeong-pro.tistory.com/145)

[[Java] NIO 기반 입출력 및 네트워킹 - NIO,파일 & 디렉토리](https://palpit.tistory.com/640)


작성자 : 은솔

작성일 : 2020-12-10