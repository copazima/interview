# 버블 정렬  

![버블 정렬](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=http%3A%2F%2Fcfile3.uf.tistory.com%2Fimage%2F9957E0355AE346722E06E3)  

* 배열을 순차탐색하여 i, i+1번째 요소를 비교하여 큰 것을 뒤로 이동한다
* 위 과정이 1번 처리되는 경우 가장 큰 수가 배열 마지막에 위치 한다.
* 다음 탐색부터는 마지막요소는 하지 않아도 된다. 그래서 내부에 있는 for문은   arr.length - i 까지만 탐색한다.

```java
public static void bubleSort(int[] arr) {
    for(int i = 0; i < arr.length; i++) {
        for(int j = 0 ; j < arr.length - i - 1 ; j++) {
            if(arr[j] > arr[j+1]) {
                int temp = arr[j+1];
                arr[j+1] = arr[j];
                arr[j] = temp;
            }
        }
    }
}
```

참고자료:https://javaplant.tistory.com/16 [자바공작소]  
작성자: 다정  
작성일: 20201123  

