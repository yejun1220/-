# Chapter 7

#### [7-1] 섯다카드 20장을 포함하는 섯다카드 한 벌(SutdaDeck클래스)을 정의한 것이다. 섯다카드 20장을 담는 SutdaCard배열을 초기화하시오. 단, 섯다카드는 1부터 10까지의 숫자가 적힌 카드가 한 쌍씩 있고, 숫자가 1, 3, 8인 경우에는 둘 중의 한 장은 광(Kwang)이어야 한다. 즉, SutdaCard의 인스턴스변수 isKwang의 값이 true이어야 한다.

```java
[연습문제]/ch7/Exercise7_1.java
class SutdaDeck {
    final int CARD_NUM = 20;
    SutdaCard[] cards = new SutdaCard[CARD_NUM];
    SutdaDeck() {
        for(int i=0; i<20; i++) {
            int num = i%10+1; // 10까지만 저장해야 하므로
            boolean isKwang = (i<10) && (num==1||num==3||num==8);

            cards[i] = new SutdaCard(num, isKwang);
        }
    }
}

class SutdaCard {
    int num;
    boolean isKwang;
    SutdaCard() {
        this(1, true);
    }

    SutdaCard(int num, boolean isKwang) {
        this.num = num;
        this.isKwang = isKwang;
}

    // info()대신 Object클래스의 toString()을 오버라이딩했다.
    public String toString() {
        return num + ( isKwang ? "K":"");
    }
}

class Exercise7_1 {
    public static void main(String args[]) {
        SutdaDeck deck = new SutdaDeck();
        for(int i=0; i < deck.cards.length;i++)
            System.out.print(deck.cards[i]+",");
    }
}
[실행결과]
1K,2,3K,4,5,6,7,8K,9,10,1,2,3,4,5,6,7,8,9,10,
```

<br>

#### [7-2] 문제7-1의 SutdaDeck클래스에 다음에 정의된 새로운 메서드를 추가하고 테스트 하시오.
[주의] Math.random()을 사용하는 경우 실행결과와 다를 수 있음.


    1. 메서드명 : shuffle
    기 능 : 배열 cards에 담긴 카드의 위치를 뒤섞는다.(Math.random()사용)
    반환타입 : 없음
    매개변수 : 없음

    2. 메서드명 : pick
    기 능 : 배열 cards에서 지정된 위치의 SutdaCard를 반환한다.
    반환타입 : SutdaCard
    매개변수 : int index - 위치

    3. 메서드명 : pick
    기 능 : 배열 cards에서 임의의 위치의 SutdaCard를 반환한다.(Math.random()사용)
    반환타입 : SutdaCard
    매개변수 : 없음

```java
[연습문제]/ch7/Exercise7_2.java
class SutdaDeck {
    final int CARD_NUM = 20;
    SutdaCard[] cards = new SutdaCard[CARD_NUM];

    SutdaDeck() {
        for(int i=0; i<20; i++) {
            int num = i%10+1; // 10까지만 저장해야 하므로
            boolean isKwang = (i<10) && (num==1||num==3||num==8);

            cards[i] = new SutdaCard(num, isKwang);
        }
    }

    void shuffle() {
        for(int i=0; i<cards.length; i++){
            int j = (int)(Math.random() * cards.length);

            SutdaCard temp = cards[i];
            cards[i] = cards[j];
            cards[j] = temp;
        }
    }

    SutdaCard pick(int index) {
        if(index < 0 || index >= cards.length)
            return null;
        else
            return cards[index];
    }

    SutdaCard pick() {
        int index = (int)(Math.random() * cards.length);
        return cards[index];
    }
} // SutdaDeck

class SutdaCard {
    int num;
    boolean isKwang;
    SutdaCard() {
        this(1, true);
    }

    SutdaCard(int num, boolean isKwang) {
        this.num = num;
        this.isKwang = isKwang;
    }

    public String toString() {
        return num + ( isKwang ? "K":"");
    }
}

class Exercise7_2 {
    public static void main(String args[]) {
        SutdaDeck deck = new SutdaDeck();
        System.out.println(deck.pick(0));
        System.out.println(deck.pick());
        deck.shuffle();
        for(int i=0; i < deck.cards.length;i++)
            System.out.print(deck.cards[i]+",");

        System.out.println();
        System.out.println(deck.pick(0));
     }
}
[실행결과]
1K
7
2,6,10,1K,7,3,10,5,7,8,5,1,2,9,6,9,4,8K,4,3K,
2
```

<br>

#### [7-3] 오버라이딩의 정의와 필요성에 대해서 설명하시오.

    오버라이딩이란 상위 클래스에서 선언된 메소드를 하위 클래스에서 재선언 하는 것
    하위 클래스에 맞게 구현할 수 있기 때문

<br>

#### [7-4] 다음 중 오버라이딩의 조건으로 옳지 않은 것은? (모두 고르시오)

    a. 조상의 메서드와 이름이 같아야 한다.
    b. 매개변수의 수와 타입이 모두 같아야 한다.
    c. 접근 제어자는 조상의 메서드보다 좁은 범위로만 변경할 수 있다.
    d. 조상의 메서드보다 더 많은 수의 예외를 선언할 수 있다.

`c, d`

<br>

#### [7-5] 다음의 코드는 컴파일하면 에러가 발생한다. 그 이유를 설명하고 에러를 수정하기 해서는 코드를 어떻게 바꾸어야 하는가?

```java
[연습문제]/ch7/Exercise7_5.java
class Product {
    int price; // 제품의 가격
    int bonusPoint; // 제품구매 시 제공하는 보너스점수

    Product() {}

    Product(int price) {
        this.price = price;
        bonusPoint =(int)(price/10.0);
    }
}

class Tv extends Product {
    Tv() {}

    public String toString() {
        return "Tv";
    }
}

class Exercise7_5 {
    public static void main(String[] args) {
        Tv t = new Tv();
    }
}
```

    Product(int price)로 생성자가 매개변수를 받기 때문에 자식 클래스도 이를 명시해줘야 한다.
    즉 Tv() 생성자 안에 super(price) 로 넘겨주거나, Product(int price)로 생성이 안되게
    Product() {} 을 만들어주면 된다.

<br>

#### [7-6] 자손 클래스의 생성자에서 조상 클래스의 생성자를 호출해야하는 이유는 무엇인가?

    조상 클래스로부터 상속받은 메소드 및 필드들은 부모클래스에서 정의된 것이기 때문에
    상속받은 자손 클래스가 생성되면 당연히 조상 클래스도 생성된다.
    즉, 자손 클래스에서 상속받은 메소드 및 필드들을 사용하려면 조상 클래스도 생성되야 하며
    조상 클래스 생성자가 초기화시켜주어야 한다.

<br>

#### [7-7] 다음 코드의 실행했을 때 호출되는 생성자의 순서와 실행결과를 적으시오.

```java
[연습문제]/ch7/Exercise7_7.java
class Parent {
    int x=100;
    Parent() {
        this(200);
    }

    Parent(int x) {
        this.x = x;
    }

    int getX() {
        return x;
    }
}

class Child extends Parent {
    int x = 3000;

    Child() {
        this(1000);
    }

    Child(int x) {
        this.x = x;
    }
}

class Exercise7_7 {
    public static void main(String[] args) {
        Child c = new Child();
        System.out.println("x="+c.getX());
    }
}
```

`Child() -> Child(int x) -> Parent() -> Parent(int x) -> Object(), x=200`

<br>

#### [7-8] 다음 중 접근제어자를 접근범위가 넓은 것에서 좁은 것의 순으로 바르게 나열한 것은?

    a. public-protected-(default)-private
    b. public-(default)-protected-private
    c. (default)-public-protected-private
    d. private-protected-(default)-public

`a`

<br>

#### [7-9] 다음 중 제어자 final을 붙일 수 있는 대상과 붙였을 때 그 의미를 적은 것이다. 옳지 않은 것은? (모두 고르시오)

    a. 지역변수 - 값을 변경할 수 없다.
    b. 클래스 - 상속을 통해 클래스에 새로운 멤버를 추가할 수 없다.
    c. 메서드 - 오버로딩을 할 수 없다. ← 오버라이딩(overriding)을 할 수 없다.
    d. 멤버변수 - 값을 변경할 수 없다.


<br>

#### [7-10] MyTv2클래스의 멤버변수 isPowerOn, channel, volume을 클래스 외부에서 접근할 수 없도록 제어자를 붙이고 대신 이 멤버변수들의 값을 어디서나 읽고 변경할 수 있도록 getter와 setter메서드를 추가하라.

```java
[연습문제]/ch7/Exercise7_10.java
class MyTv2 {
    private boolean isPowerOn;
    private int channel;
    private int volume;
    final int MAX_VOLUME = 100;
    final int MIN_VOLUME = 0;
    final int MAX_CHANNEL = 100;
    final int MIN_CHANNEL = 1;

    void setVolume(int volume){
        if(volume > MAX_VOLUME || volume < MIN_VOLUME)
            return;

        this.volume = volume;
    }

    int getVolume(){
        return;
    }

    void setChannel(int channel) {
        if(channel > MAX_CHANNEL || channel < MIN_CHANNEL)
            return null;

        this.channel = channel;
    }

    int getChannel() {
        return channel;
    }
}

class Exercise7_10 {
    public static void main(String args[]) {
    MyTv2 t = new MyTv2();

    t.setChannel(10);
    System.out.println("CH:"+t.getChannel());
    t.setVolume(20);
    System.out.println("VOL:"+t.getVolume());
    }
}

[실행결과]
CH:10
VOL:20
```