# CI/CD란?

> CI/CD는 프로젝트 빌드 - 테스트 - 병합 - 배포까지의 전 과정을 말한다. 많은 경우, CI/CD라고 하면 자동화를 포함한 뜻으로 사용한다.

## CI (Continuous Integration)

**CI**는 **지속적인 통합**을 말한다.

변경하거나 추가한 소스 코드를 기존의 프로젝트와 통합하여 빌드하고 테스트하는 과정이 지속적인 통합이다. `git`과 `Travis CI`/`Jenkins`같은 툴을 연동하여 CI를 자동화할 수 있다.

CI를 자동화했을 때 얻는 이점은 크게 세 가지인 것 같다.

-   새로운 소스코드가 기존 코드와 충돌을 일으키는지 검증할 수 있기 때문에 신속한 문제 해결 가능.
    
-   테스트와 빌드를 자동화함으로써 기계적인 반복을 줄이고 빠른 검증이 가능.
    
-   이 과정을 통해 **완전한 배포** 파일을 만들 수 있다.
    
    하지만 테스트 코드를 작성하지 않았다면 CI를 구축하더라도 완전한 배포 파일이라는 것을 장담할 수 없다.
    

## CD(Code Delivery & Code Deployment)

**CD**는 **지속적인 전달**과 **지속적인 배포** 두 가지를 뜻한다. CI를 거쳐 **통합된 프로젝트를 프로덕션 환경으로 이동시키고(Delivery) 배포(Deploy)하는 것**을 말한다. 이 과정을 AWS에서 제공하는 CD서비스인 `CodeDeploy` 와 `Nginx`의 리버스 프록시 기능을 이용하여 중단 없는 배포 환경을 구성할 수 있다.

![architecture](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FwYKfv%2FbtqYfXdSOsN%2Fr3n7k6yzu97CAX1Uth2oEK%2Fimg.png)

프로젝트에 CI/CD를 적용했을 때 구조는 이렇다. 위 프로젝트에 대입하여 CI/CD를 설명해보자면 이렇다.

### CI

1.  메인 브랜치에 `push`하면 github이 `trigger`를 작동한다.
2.  Travis CI가 프로젝트를 가져와 빌드 -> 테스트 -> 병합 과정을 거친다.
3.  병합을 마친 프로젝트를 `S3`에 업로드한다.

### CD

1.  `CodeDeploy`는 배포 요청을 받으면 S3에서 프로젝트를 가져온다.
2.  프로젝트를 EC2서버로 옮기고 배포한다.
3.  Nginx를 reload한다.

여기서 `nginx`는 **리버스 프록시 서버**다. 리버스 프록시는 **클라이언트의 요청을 받아서 내부 서버로 요청을 위임**한다. 위 표에 대입해서 말하자면 [https://recipya.site](https://recipya.site%EB%A1%9C) 로 들어오는 모든 요청을 Nginx가 받아서 현재 실행되고 있는 8081(2) 포트를 사용하는 내부 서버 로 위임한다.

[##_Image|kage@cB7Qg0/btqYiC7SLOE/OJdPIY1q8NGP3pKK4bzNk1/img.png|alignCenter|data-filename="proxy-server.png" data-origin-width="350" data-origin-height="131" data-ke-mobilestyle="widthContent"|Reverse Proxy||_##]

이 방식을 사용하면 새 버전이 릴리스되면 Nginx reload를 통해 새 버전으로 들어오는 요청을 위임할 수 있다. 따라서 새 버전이 릴리스 되더라도 중단없이 서비스를 운영할 수 있다. 이것이 중간에 리버스 프록시를 두는 이유다.

만약 프록시 서버를 경유하지 않고 요청을 받는다면 기존 서버를 닫고 새 서버를 실행하는 시간 동안은 서비스가 중단될 것이다.

참고  
스프링부트와 AWS로 혼자 구현하는 웹 서비스(이동욱 저)  
[www.redhat.com/ko/topics/devops/what-cicd-pipeline](https://www.redhat.com/ko/topics/devops/what-cicd-pipeline)  
[artist-developer.tistory.com/24](https://artist-developer.tistory.com/24)  
[deveric.tistory.com/106](https://deveric.tistory.com/106)  
[ko.wikipedia.org/wiki/%EB%A6%AC%EB%B2%84%EC%8A%A4\_%ED%94%84%EB%A1%9D%EC%8B%9C](https://ko.wikipedia.org/wiki/%EB%A6%AC%EB%B2%84%EC%8A%A4_%ED%94%84%EB%A1%9D%EC%8B%9C)