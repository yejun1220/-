# Chapter 9


#### [9-1] 다음과 같은 실행결과를 얻도록 SutdaCard클래스의 equals()를 멤버변수인 num, isKwang의 값을 비교하도록 오버라이딩하고 테스트 하시오.

```java
[연습문제]/ch9/Exercise9_1.java
class Exercise9_1 {
    public static void main(String[] args) {
        SutdaCard c1 = new SutdaCard(3,true);
        SutdaCard c2 = new SutdaCard(3,true);
        
        System.out.println("c1="+c1);
        System.out.println("c2="+c2);
        System.out.println("c1.equals(c2):"+c1.equals(c2));
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

    public boolean equals(Object obj) {
        if(obj instanceof SutdaCard) {
            SutdaCard c = (SutdaCard)obj;
            return num==c.num && isKwang==c.isKwang;
        }   

        return false;
    }

    public String toString() {
        return num + ( isKwang ? "K":"");
    }

}
[실행결과]
c1=3K
c2=3K
c1.equals(c2):true
```

<br>

#### [9-2] 다음과 같은 실행결과를 얻도록 Point3D클래스의 equals()를 멤버변수인 x, y, z의 값을 비교하도록 오버라이딩하고, toString()은 실행결과를 참고해서 적절히 오버라이딩하시오.

```java
[연습문제]/ch9/Exercise9_2.java
class Exercise9_2 {
    public static void main(String[] args) {
        Point3D p1 = new Point3D(1,2,3);
        Point3D p2 = new Point3D(1,2,3);
        
        System.out.println(p1);
        System.out.println(p2);
        System.out.println("p1==p2?"+(p1==p2));
        System.out.println("p1.equals(p2)?"+(p1.equals(p2)));
    }
}

class Point3D {
    int x,y,z;

    Point3D(int x, int y, int z) {
        this.x=x;
        this.y=y;
        this.z=z;
    }

    Point3D() {
        this(0,0,0);
    }

    public boolean equals(Object obj) {
        if(obj instanceof Point3D) {
            Point3D p =(Point3D)obj;
            return x==p.x && y==p.y && z==p.z;
        }

        return false;
    }

    public String toString() {
        return "["+x+","+y+","+z+"]";
    }
}
[실행결과]
[1,2,3]
[1,2,3]
p1==p2?false
p1.equals(p2)?true
```