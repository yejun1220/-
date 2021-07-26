# Chapter 5

[6-1] 다음과 같은 멤버변수를 갖는 SutdaCard클래스를 정의하시오.


    타 입    변수명         설 명
    int      num     카드의 숫자.(1~10사이의 정수)
    boolean  isKwang 광(光)이면 true, 아니면 false

```java
class SutdaCard {
    int num;
    boolean isKwang;
}
```

<br>

#### [6-2] 문제6-1에서 정의한 SutdaCard클래스에 두 개의 생성자와 info()를 추가해서 실행 결과와 같은 결과를 얻도록 하시오.

```java
[연습문제]/ch6/Exercise6_2.java
class Exercise6_2 {
    public static void main(String args[]) {
        SutdaCard card1 = new SutdaCard(3, false);
        SutdaCard card2 = new SutdaCard();
        System.out.println(card1.info());
        System.out.println(card2.info());
    }
}
class SutdaCard {
    int num;
    boolean isK;
    SutdaCard() {
        this(1, true);
    }

    SutdaCard(int num, boolean isK) {
        this.num = num;
        this.isKwang = isK;
    }
        String info() { 
        return num + ( isK? "K" : "");
    }
}
[실행결과]
3
1K
```
