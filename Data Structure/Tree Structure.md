[[자료구조] 트리(Tree)란](https://gmlwjd9405.github.io/2018/08/12/data-structure-tree.html) 글의 원문을 꼭 읽어보길 추천합니다. 

# 트리구조(Tree Structure) 

### 트리(Tree)의 개념과 특징
**노드로 이루어진 자료구조**

- 트리는 하나의 루트 노드를 갖는다
- 루트 노드는 0개 이상의 자식 노트를 갖고 있다
- 그 자식 노드 또한 0개 이상의 자식 노드를 갖고 있고, 이는 반복적으로 정의된다. 
- 비선형 자료구조로 계층적 관계를 표현한 계층 모델이다.
- 그래프의 한 종류이며 '최소 연결 트리' 라고도 불린다.
- 순환구조를 갖지 않는 비방향성 연결그래프 구조이다.

즉, 각 요소가 바로 아래에 있는 하나 이상의 요소에 연결되는 데이터 구조 유형이다.  
1개이상의 노드를 갖는 노드들의 집합요소 간의 연결을 말하며, 데이터 구조에서 다루는 트리는 
일반적으로 꼭대기에 뿌리가 그려져 있으므로 거꾸로된 트리라고도 한다.  


<img src="https://w.namu.la/s/606aecc8b8a27d42129f3e13c6db9a871a4566cd88c123689585256281efb5dde5b35f4e516572f0e5f0e419f0ae2be3aedf7a9c8dbb1756d1bf635a48da67ec9d55c88cf0f718c1aefca67212cf91846d75ed400b14e75795445a68bd20751c1cbd1ff9eab4316929c78f1f8e5d46f8">

###용어 설명
|이름|설명|
|------|---|
|루트(Root) | 부모가 없는 최상위 노드, 트리의 시작점|
|노드(Node) | 마디|
|부모노드(Parent Node)| 어떤 노드와 링크로 연결돼 있는 상위노드 |
|자식노드(Child Node)|어떤 노드와 링크로 연결돼 있는 하위노드 |
|리프(Leaf) | 자식이 없는 노드|
|깊이(Depth)| 루트에서 시작해 특정노드에 도달하기 위해 거치는 간선의 수|
|레벨(Level)| 노드와 루트사이의 간선의 수+1, 또는 특정 깊이의 노드들의 집합 |
|간선(Edge, Link)| 한 노드와 다른노드 사이의 연결선|

### 트리(Tree)의 종류
 트리의 종류

  - 순서 트리 (Ordered Tree)
     - 각 자식 노드에 순서가 부여되어 저장 위치가 고정되는 트리
       
     - 통상, 좌측부터 순서 있게 위치 함  ☞ 완전 이진 트리 참조

  - 이진 트리 (Binary Tree)
     - 각 노드의 차수(자식 수)가 2 이하인 순서 트리

     - 전 이진 트리 (Full Binary Tree)
        - 각 레벨에 노드들이 꽉 차있는 이진 트리

     - 포화 이진 트리 (Perfect Binary Tree)
        - 모든 단말 노드의 레벨이 동일하며, 최하위 자식 노드들이 모두 차 있음

     - 완전 이진 트리 (Complete Binary Tree)
        - 부모,왼쪽 자식,오른쪽 자식 순으로, 채워지며 만들어지는 이진 트리

     - 힙 (Heap)
        - 부모의 값이 자식 값 보다 항상 크다 또는 작다 라는 조건을 만족하는 완전 이진 트리

  - 이진 탐색 트리 (Binary Search Tree, BST)
     - 이진 트리 구조를 갖으나, 자료의 검색,삭제,삽입에 효율적이게 한 트리 자료구조
        - 좌측 자식 노드 값이 부모 노드 값 보다 작고, 우측 자식 노드 값이 부모 노드 값 보다 큼

  - 균형 트리 (Balanced Tree)
     - 이진 트리 구조를 갖으나, 하위 노드 구조가 좌우 대칭이 되도록 한 것 (例, B-tree)
        - 이진 탐색 트리를 보다 일반화시킨 트리 자료구조

  - N항 트리 (N-ary Tree,N-way Tree)
     - 일반적으로, 자식 노드의 수(차수)가 3 이상일 때를 말함
     - 한편, 자식 노드가 3 이상인 트리 구조를 총칭해서, 다중 트리(Multi-Branch Tree)라고 함


**Reference**

[[자료구조] 트리(Tree)란](https://gmlwjd9405.github.io/2018/08/12/data-structure-tree.html)

[트리구조(Tree Structure)란?](https://spaghetti-code.tistory.com/23)

[[자료구조] 트리(Tree) - 트리의 종류, 3가지 순회방법](https://it-and-life.tistory.com/164?category=879132)

[[정보통신기술용어해설]](http://www.ktword.co.kr/abbr_view.php?m_temp1=5424)

<파이썬 알고리즘 인터뷰> p.384, 책만, 2020

작성자 : 은솔

작성일 : 2020-11-28

