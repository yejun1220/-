# Chapter 5

#### [5-1] 다음은 배열을 선언하거나 초기화한 것이다. 잘못된 것을 고르고 그 이유를 설명하시오.

    a. int[] arr[];
    b. int[] arr = {1,2,3,};
    c. int[] arr = new int[5];
    d. int[] arr = new int[5]{1,2,3,4,5};
    e. int arr[5];
    f. int[] arr[] = new int[3][];

<br>

#### [5-2] 다음과 같은 배열이 있을 때, arr[3].length의 값은 얼마인가?

    int[][] arr = {
        { 5, 5, 5, 5, 5},
        { 10, 10, 10},
        { 20, 20, 20, 20},
        { 30, 30}
    };

`30,30 2개므로 크기는 2다.`

<br>

#### [5-3] 배열 arr에 담긴 모든 값을 더하는 프로그램을 완성하시오.

```java
[연습문제]/ch5/Exercise5_3.java
class Exercise5_3
{
    public static void main(String[] args) {
        int[] arr = {10, 20, 30, 40, 50};
        int sum = 0;
        
        for(int i=0; i<arr.length; i++)
            sum += arr[i];

        System.out.println("sum="+sum);
    }
}

[실행결과]
sum=150
```

<br>

#### [5-4] 2차원 배열 arr에 담긴 모든 값의 총합과 평균을 구하는 프로그램을 완성하시오.

```java
[연습문제]/ch5/Exercise5_4.java
class Exercise5_4
{
    public static void main(String[] args) {
        int[][] arr = {
        { 5, 5, 5, 5, 5},
        {10,10,10,10,10},
        {20,20,20,20,20},
        {30,30,30,30,30}
        };
        int total = 0;
        float average = 0;
        for(int i=0; i<arr.length ; i++) {
            for(int j=0; j<arr[i].length; j++) {
                total += arr[i][j];
            }
        }
        average = total / (float)(arr.length * arr[0].length;

        System.out.println("total="+total);
        System.out.println("average="+average);
    } // end of main
} // end of class

[실행결과]
total=325
average=16.25
```

<br>