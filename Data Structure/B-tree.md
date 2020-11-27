[B-Tree 개념정리](https://hyungjoon6876.github.io/jlog/2018/07/20/btree.html#:~:text=B%2DTree%20%EB%8A%94%20%EC%9D%B4%EC%A7%84%ED%8A%B8%EB%A6%AC,%ED%95%98%ED%96%A5%EC%8B%9D%EC%9C%BC%EB%A1%9C%20%ED%83%90%EC%83%89%ED%95%B4%20%EB%82%98%EA%B0%91%EB%8B%88%EB%8B%A4.)
의 블로그의 원문을 읽는 것도 좋을 것 같네요. 


# B-Tree
Binary Tree (이진트리)와 혼동하지 말 것

- 데이터베이스와 파일 시스템에서 많이 사용된다.
- 이진트리는 자식노드가 최대 2개라면, B-Tree는 자식노드가 두 개 이상인 노드가 허용된다.
- 정렬된 데이터를 유지하고 로그 시간에 검색, 순차 액세스, 삽입 및 삭제를 허용하는 자가 균형 트리 데이터 구조. 
- 이진검색트리와 달리 디스크와 같이 상대적으로 큰 데이터 블록을 읽고 쓰는 스토리지 시스템에 적합하다. 

B 트리는 대형 랜덤 액세스 파일의 인덱스 페이지를 효율적으로 관리하기 위해 보잉 연구소에서 
근무하던 중 루돌프 바이어와 에드워드 M. 맥크라이트가 발명했다. 
기본 가정은 인덱스가 너무 커서 나무의 작은 덩어리만이 기본 메모리에 들어갈 수 있다는 것이다.

B-Tree 는 이진트리와 마찬가지로 작은 값은 왼쪽 서브트리, 큰 값은 오른쪽 서브트리에 이루어져있습니다. 
탐색 하고자하는 값을 root 노드 부터 시작해 하향식으로 탐색해 나갑니다.



**Reference**

[B-tree](https://en.wikipedia.org/wiki/B-tree#:~:text=O(log%20n)-,O(log%20n),with%20more%20than%20two%20children.)

[B-Tree 개념정리](https://hyungjoon6876.github.io/jlog/2018/07/20/btree.html#:~:text=B%2DTree%20%EB%8A%94%20%EC%9D%B4%EC%A7%84%ED%8A%B8%EB%A6%AC,%ED%95%98%ED%96%A5%EC%8B%9D%EC%9C%BC%EB%A1%9C%20%ED%83%90%EC%83%89%ED%95%B4%20%EB%82%98%EA%B0%91%EB%8B%88%EB%8B%A4.)

작성자 : 은솔

작성일 : 2020-11-28