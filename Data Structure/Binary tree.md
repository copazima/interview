
**[ 자료구조 / 알고리즘 기초 ]** 
# 이진트리(Binary tree) 
       모든 노드의 차수/자식이 2 이하(최대 2)인 특수한 형태의 순서 트리




<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/f/f7/Binary_tree.svg/330px-Binary_tree.svg.png">

<br>

#### 특징

  - 각 노드가 최대 2개의 자식 노드를 갖으며, 좌 우 자식 노드로 구분된다.
  - 이진 트리는 순서 트리로써, 노드 위치 및 순서가 중요한 의미를 갖는다.        
  - 루트 노드 레벨(level)은 0 으로 한다.
  - 레벨 깊이(depth) i일 경우, 갖을 수 있는 최대 노드 수는 2i - 1


***중복이 없어야 하는 이유는?***

검색 목적 자료구조인데, 굳이 중복이 많은 경우에 트리를 사용하여 검색 속도를 느리게 할 필요가 없음. (트리에 삽입하는 것보다, 노드에 count 값을 가지게 하여 처리하는 것이 훨씬 효율적)

<br>

이진탐색트리의 순회는 **'중위순회(inorder)' 방식 (왼쪽 - 루트 - 오른쪽)**

중위 순회로 **정렬된 순서**를 읽을 수 있음

<br>

#### 이진 트리의 응용
     
       ㅇ 이진 검색 트리 (Binary Search Tree, BST)
          - 이진 트리 구조를 갖으나, 자료의 검색,삭제,삽입에 효율적이게 한 트리 자료구조
          - 각 노드는 2개의 자식 노드를 각각 가리키는 2개의 포인터를 갖음
          - 최대 2개의 자식 노드를 가질 수 있음
     
       ㅇ AVL 트리 (AVL Tree, Adelson-Velskii and Landis's Tree)
          - 한 노드를 중심으로 좌우 부분의 트리 높이(height)의 차가 1 이하가 되도록 하는 이진 탐색 트리
          - 가장 초기에 나온 균형 잡힌(Balanced) 이진 탐색 트리 
     
       ㅇ B 트리 (B-Tree, Balanced Tree)
          - 이진 탐색 트리를 보다 일반화시킨 트리 자료구조를 말함
          - 데이터베이스 및 파일시스템에 널리 쓰이는 자료구조
     
  


### Reference 
[정보통신기술용어해설](http://www.ktword.co.kr/abbr_view.php?m_temp1=5423)

[[파일구조] B tree 와 B+ tree](https://wangin9.tistory.com/entry/B-tree-B-tree)

[B Tree & B+ Tree](https://github.com/gyoogle/tech-interview-for-developer/blob/master/Computer%20Science/Data%20Structure/B%20Tree%20%26%20B%2B%20Tree.md)

[[DS] 이진 트리 - binary tree (개념 및 이진 트리의 종류)](https://sean-ma.tistory.com/24)

작성자 : 은솔

작성일 : 20201115
