# 퀵 정렬  
Pivot을 중심으로 L 과 R 값을 지정해준다.  
L은 Pivot보다 큰 값, R은 Pivot보다 작은 값을 지정한다.  
두 개 모두 선택됐다면 자리교환을 해주면 된다.

만약 한쪽이 선택된 L이나 R이 없다면 선택된 값과 Pivot을 교환하도록 한다.

![퀵 정렬](https://t1.daumcdn.net/cfile/tistory/256F4448562E5A3022)  

```java
            p
[3, 2, 1] < 4 < [7, 5, 6]
```

```java
public class QuickSort { static int partition(int[] array,int start, int end) { 
    int pivot = array[(start+end)/2]; 
    while(start<=end) { 
        while(array[start]<pivot) start++; 
        while(array[end]>pivot) end--; 
        if(start<=end) { 
            int tmp = array[start]; 
            array[start]=array[end]; 
            array[end]=tmp; 
            start++; 
            end--; 
            } 
        } 
        return start; 
    } 
    static int[] quickSort(int[] array,int start, int end) {
         int p = partition(array, start, end);
          if(start<p-1) 
            quickSort(array,start,p-1);
         if(p<end) 
            quickSort(array,p,end);
             return array; 
    } 
    public static void main(String[] args) { 
        int[] array = {4,2,3,5,9}; 
        array = quickSort(array,0,array.length-1); 
        System.out.println(Arrays.toString(array)); 
        } 
    }

출처: https://heekim0719.tistory.com/282 [생각하며 개발하자, 별토끼의 프로그래밍]
```

```java
public class Quick {
    
    public void sort(int[] data, int l, int r){
        int left = l;
        int right = r;
        int pivot = data[(l+r)/2];
        
        do{
            while(data[left] < pivot) left++;
            while(data[right] > pivot) right--;
            if(left <= right){    
                int temp = data[left];
                data[left] = data[right];
                data[right] = temp;
                left++;
                right--;
            }
        }while (left <= right);
        
        if(l < right) sort(data, l, right);
        if(r > left) sort(data, left, r);
    }
    
    public static void main(String[] args) {
        
        int data[] = {66, 10, 1, 34, 5, -10};
        
        Quick quick = new Quick();
        quick.sort(data, 0, data.length - 1);
        for(int i=0; i<data.length; i++){
            System.out.println("data["+i+"] : "+data[i]);
        }
    }
}



```


파이썬의 list.sort() 함수나 자바의 Arrays.sort()처럼 프로그래밍 언어 차원에서 기본적으로 지원되는 내장 정렬 함수는 대부분은 퀵 정렬을 기본으로 한다.

참고자료: [https://www.daleseo.com/sort-quick/]  
[https://hahahoho5915.tistory.com/9]  
[https://heekim0719.tistory.com/282]  

작성자: 다정  
작성일:20201125