# Chapter 4

#### [4-1] 다음의 문장들을 조건식으로 표현하라.
    1. int형 변수 x가 10보다 크고 20보다 작을 때 true인 조건식
    2. char형 변수 ch가 공백이나 탭이 아닐 때 true인 조건식
    3. char형 변수 ch가 ‘x' 또는 ’X'일 때 true인 조건식
    4. char형 변수 ch가 숫자(‘0’~‘9’)일 때 true인 조건식
    5. char형 변수 ch가 영문자(대문자 또는 소문자)일 때 true인 조건식
    6. int형 변수 year가 400으로 나눠떨어지거나 또는 4로 나눠떨어지고 100으로 나눠떨어지지 않을 때 true인 조건식
    7. boolean형 변수 powerOn가 false일 때 true인 조건식
    8. 문자열 참조변수 str이 “yes”일 때 true인 조건식

`1. 10 < x && x < 20`

`2. ch!=' ' && ch !='\t'`

`3. ch == 'x' || ch == 'X' ||`

`4. '0' <= ch && ch <= '9' `

`5. ('a' <= ch && ch <= 'z') || ('A' <= ch && ch <= 'Z')`

`6. (year % 400 == 0) || (year % 4 == 0) && (year % 100 != 0)`

`7. powerOn == false 또는 !powerOn`

`8. str.equals("yes")`

<br>

#### [4-2] 1부터 20까지의 정수 중에서 2 또는 3의 배수가 아닌 수의 총합을 구하시오.

```java
int sum = 0;
for (int i = 0; i <= 20; i++) {

    if(i % 2 != 0 || i % 3 != 0) {
        sum += i;
    }
}
```

<br>

#### [4-3] 1+(1+2)+(1+2+3)+(1+2+3+4)+...+(1+2+3+...+10)의 결과를 계산하시오.

```java
int sum = 0;
int total = 0;

for (int i < 0; i <= 10; i++) {
    sum += i
    total += sum
}
```

<br>

#### [4-4] 1+(-2)+3+(-4)+... 과 같은 식으로 계속 더해나갔을 때, 몇까지 더해야 총합이 100이상이 되는지 구하시오.

```java
int sum = 0;
int s = 1;
int answer = 0;

for (int i = 1; true; i++, s=-s) {
    answer = i * s;
    sum += answer 

    if (sum > 100)
        break;
}
```

<br>

#### [4-5] 다음의 for문을 while문으로 변경하시오.

```java
[연습문제]/ch4/Exercise4_5.java

public class Exercise4_5 {
    public static void main(String[] args) {
        for(int i=0; i<=10; i++) {
            for(int j=0; j<=i; j++)
                System.out.print("*");
            System.out.println();
        }
    } // end of main
} // end of class
```

```java
[답]/ch4/Exercise4_5.java
    
public class Exercise4_5 {
    public static void main(String[] args) {
        
        int i = 0;
        while(i <= 10) {
            int j = 0;

            while(j <= i) {
                System.out.print("*");
                j++;
            }

            System.out.println();
            i++;
        }
    }
}
```

<br>

#### [4-6] 두 개의 주사위를 던졌을 때, 눈의 합이 6이 되는 모든 경우의 수를 출력하는 프로그램을 작성하시오.

```java
for(int i=1;i<=6;i++)
    for(int j=1;j<=6;j++)
        if(i+j==6)
            System.out.println(i + "+" + j + "=" + (i+j));
```

<br>

#### [4-7] Math.random()을 이용해서 1부터 6사이의 임의의 정수를 변수 value에 저장하는 코드를 완성하라. (1)에 알맞은 코드를 넣으시오.

```java
[연습문제]/ch4/Exercise4_7.java
class Exercise4_7 {
    public static void main(String[] args) {
        int value = ( /* (1) */ );
            System.out.println("value:"+value);
        }
}
```

`(int)(Math.random()*6) + 1`

<br>

#### [4-8] 방정식 2x+4y=10의 모든 해를 구하시오. 단, x와 y는 정수이고 각각의 범위는 0<=x<=10, 0<=y<=10 이다.

```java
for (int x = 0; x <= 10; i++)
    for (int y = 0; y <= 10; i++)
        if(2 * x + 4 * y == 10)
            System.out.println("x=" + x + ", y=" + y);
```

<br>

#### [4-9] 숫자로 이루어진 문자열 str이 있을 때, 각 자리의 합을 더한 결과를 출력하는 코 드를 완성하라. 만일 문자열이 "12345"라면, ‘1+2+3+4+5’의 결과인 15를 출력이 출력 되어야 한다. (1)에 알맞은 코드를 넣으시오.

```java
[Hint] String클래스의 charAt(int i)을 사용
[연습문제]/ch4/Exercise4_9.java
class Exercise4_9 {
    public static void main(String[] args) {
        String str = "12345";
        int sum = 0;
        for(int i=0; i < str.length(); i++) {
            /* (1) 알맞은 코드를 넣어 완성하시오. */
        }
        System.out.println("sum="+sum);
    }
}
[실행결과]
15
```

`sum += str.charAt(i) - '0'`

<br>

#### [4-10] int타입의 변수 num 이 있을 때, 각 자리의 합을 더한 결과를 출력하는 코드를 완성하라. 만일 변수 num의 값이 12345라면, ‘1+2+3+4+5’의 결과인 15를 출력하라. (1)에 알맞은 코드를 넣으시오.

```java
[주의] 문자열로 변환하지 말고 숫자로만 처리해야 한다.
[연습문제]/ch4/Exercise4_10.java
class Exercise4_10 {
    public static void main(String[] args) {
        int num = 12345;
        int sum = 0;
        /* (1) 알맞은 코드를 넣어 완성하시오. */
        
        System.out.println("sum="+sum);
    }
}
```

```java
[답]/ch4/Exercise4_10.java
class Exercise4_10 {
    public static void main(String[] args) {
        int num = 12345;
        int sum = 0;

        while(num > 0) {
            sum += num % 10; // 첫째자리를 더하고  
            num /= 10; // 첫째자리를 없앤다.
        }
        System.out.println("sum="+sum);
    }
}
```

<br>