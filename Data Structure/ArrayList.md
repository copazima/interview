# 배열을 이용한 리스트 구현  
리스트란 n개의 element형으로 구성된 순서 있는 모임을 말한다.  
리스트를 구현하는 방법에는 배열을 이용한 구현과 연결리스트를 이용한 구현이 있다.  

![list](https://github.com/copazima/interview/blob/main/resource/ListADT.png?raw=true)  

* 배열로 구현된 리스트  
 배열로 구현된 리스트는 순차적인 메모리 공간에 할당하며 리스트의 순차적 표현(sequential representation)이다.  

```
#define MAX_LIST_SIZE 100 		// 리스트의 최대 크기

typedef int element; 			// 항목의 정의

typedef struct {
	element array[MAX_LIST_SIZE]; 	// 배열 정의
	int size; 			// 현재 리스트에 저장된 항목들의 개수
} ArrayListType;

// 오류 처리 함수
void error(char *message)	{
	fprintf(stderr, "%s\n", message);
	exit(1);
}
// 리스트 초기화 함수
void init(ArrayListType *L)	{
	L->size = 0 ;
}
// 리스트가 비어 있으면 1을 반환. 그렇지 않으면 0을 반환
int is_empty(ArrayListType *L)	{
	return (  L->size == 0 );
}
// 리스트가 가득 차 있으면 1을 반환. 그렇지 많으면 0을 반환
int is_full(ArrayListType *L)	{
	return ( L->size == MAX_LIST_SIZE  ) ;
}
// 특정 위치의 항목을 반환
element get_entry(ArrayListType *L, int pos)	{
	if (pos < 0 ||  pos >= L->size   )
		error("위치 오류");
	return L->array[pos];
}
// 리스트 출력
void print_list(ArrayListType *L)	{
	int i;
	for (i = 0;  i < L->size; i++)
		printf("%d->", L->array[i]);
	printf("\n");
}
//리스트의 끝에 항목 삽입
void insert_last(ArrayListType *L, element item)	{
	if( is_full ( L ))  {
		error("리스트 오버플로우");
	}
	L->array[ L->size++ ] = item;
}
//리스트의 특정 위치에 항목 삽입
void insert(ArrayListType *L, int pos, element item)
{
	if (!is_full(L) && (pos >= 0) && (pos <= L->size)) {
		for (int i = (L->size - 1); i >=  pos  ; i--)
			L->array[i + 1] = L->array[i];
		L->array[pos] = item ;
		L->size++  ;
	}
}
//리스트의 특정 위치의 항목을 삭제
element delete(ArrayListType *L, int pos)
{
	element item;

	if (pos < 0 || pos >= L->size)
		error("위치 오류");
	item = L->array[pos];
	for (int i =  pos ; i<(L->size - 1); i++)
		L->array[i] = L->array[i + 1];
	L->size-- ;
	return item;
}
// 메인
int main(void)
{
	// ArrayListType를 정적으로 생성하고 ArrayListType를 가리키는 포인터를 함수의 매개변수로 전달한다.
	ArrayListType list;

	init(&list);		
	insert(&list, 0, 10);	print_list(&list);	// 0번째 위치에 10 추가
	insert(&list, 0, 20);	print_list(&list);	// 0번째 위치에 20 추가
	insert(&list, 0, 30);	print_list(&list);	// 0번째 위치에 30 추가
	insert_last(&list, 40);	print_list(&list);	// 맨 끝에 40 추가
	delete(&list, 0);	print_list(&list);	// 0번째 항목 삭제
	return 0;
}

/* 실행결과
10->
20->10->
30->20->10->
30->20->10->40->
20->10->40->
*/
```
## 배열 기반 리스트의 장점  
* 데이터의 참조가 쉽다.  
* 인덱스 값을 기준으로 어디든 한 번에 참조가 가능하다.  

## 배열 기반 리스트의 단점  
* 배열의 길이가 초기에 결정되어야 한다.  
* 삭제의 과정에서 데이터의 이동이 매우 빈번하다.  

> 참고자료  
[https://rudruddl.tistory.com/111]  
[https://yjg-lab.tistory.com/117]  
작성자: 다정  
작성일: 21.6.8