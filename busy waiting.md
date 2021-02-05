# Busy Waiting에 대해  

- Busy Waiting 개념: 어떤 특정 공유자원에 대해 두 개 이상의 프로세스나 스레드가 그 이용 권한을 획득하고자 하는 동기화 상황에서 그 권한 획득을 위한 과정에서 일어나는 현상. (권한을 얻을 때까지 확인한다.)  
    + Busy Waiting을 사용하기 좋은 상황일 경우
    1.자원의 권한을 얻는데 많은 시간이 소요되지 않는 상황  
    2.Context Switcing 비용보다 성능적으로 더 우수한 상황  

    + Busy Waiting의 단점: 권한 획득을 위해 많은 CPU를 낭비

<br>

> C언어 예제
>> 다음의 C 코드 예제는 전역 정수 i를 공유하는 스레드 2개를 나타낸다. 첫 번째 스레드는 바쁜 대기를 사용하여 i의 값의 변경사항을 검사한다
``` 
#include <stdio.h>
#include <pthread.h>
#include <unistd.h>
#include <stdlib.h>

volatile int i = 0; 

/* f1 uses a spinlock to wait for i to change from 0. */
static void *f1(void *p)
{
    while (i==0) {
        /* do nothing - just keep checking over and over */
    }
    printf("i's value has changed to %d.\n", i);
    return NULL;
}

static void *f2(void *p)
{
    sleep(60);   /* sleep for 60 seconds */
    i = 99;
    printf("t2 has changed the value of i to %d.\n", i);
    return NULL;
}

int main()
{
    int rc;
    pthread_t t1, t2;

    rc = pthread_create(&t1, NULL, f1, NULL);
    if (rc != 0) {
        fprintf(stderr,"pthread f1 failed\n");
        return EXIT_FAILURE;
    }

    rc = pthread_create(&t2, NULL, f2, NULL);
    if (rc != 0) {
        fprintf(stderr,"pthread f2 failed\n");
        return EXIT_FAILURE;
    }

    pthread_join(t1, NULL);
    pthread_join(t2, NULL);
    puts("All pthreads finished.");
    return 0;
}
```


*busy waiting 대체 방법으로 sleeping과  뮤텍스 세마포어(mutual exclusion)등의 내용을 추가 확인하면 좋을 것 같네요  
  

> 참고자료  
[Waiting과 sleeping 간단 설명: https://nesoy.github.io/articles/2019-06/OS-Busy-Waiting]    
[busy waiting 위키백과: https://ko.wikipedia.org/wiki/%EB%B0%94%EC%81%9C_%EB%8C%80%EA%B8%B0]  
[뮤텍스 세마포어,모니터에 대한 내용: https://simsimjae.tistory.com/289]  

* 작성자:다정  
* 작성일:20210206