# 🎯 재귀호출을 사용해서 1부터 10까지 더하기

* 재귀호출 : 자기 자신을 반복적으로 호출하는 형태로 실제 프로젝트에서는 타이밍 이슈 때문에 특정 작업이 완료되었는지 체크하기 위해 재귀호출을 사용하는 경우가 있다.  

``` java

public class RecursiveCall{
    public static void main(String [] args){
        System.out.println(recursiveCallPlus(0));
    }

    static int recursiveCallPlus(int sum){
        if(sum == 10){
            return 10;
        }
        return sum + recursiveCallPlus(sum+1); 
    }
}

```
* 참고 블로그: [https://lktprogrammer.tistory.com/106]
