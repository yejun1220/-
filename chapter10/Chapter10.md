# Chapter 10

#### [10-1] Calendar클래스와 SimpleDateFormat클래스를 이용해서 2010년의 매월 두 번째 일요일의 날짜를 출력하시오.

    [실행결과]
    2010-01-10은 2번째 일요일입니다.
    2010-02-14은 2번째 일요일입니다.
    2010-03-14은 2번째 일요일입니다.
    2010-04-11은 2번째 일요일입니다.
    2010-05-09은 2번째 일요일입니다.
    2010-06-13은 2번째 일요일입니다.
    2010-07-11은 2번째 일요일입니다.
    2010-08-08은 2번째 일요일입니다.
    2010-09-12은 2번째 일요일입니다.
    2010-10-10은 2번째 일요일입니다.
    2010-11-14은 2번째 일요일입니다.
    2010-12-12은 2번째 일요일입니다.

```java
[연습문제]/ch10/Exercise10_1.java
import java.util.*;
import java.text.*;
class Exercise10_1 {
public static void main(String[] args) {
    Calendar cal = Calendar.getInstance();

    cal.set(2010,0,1);
    
    for(int i=0; i < 12;i++) {
        int weekday = cal.get(Calendar.DAY_OF_WEEK); 
        
        int secondSunday = (weekday==1) ? 8 : 16 - weekday;
        
        cal.set(Calendar.DAY_OF_MONTH, secondSunday);
        
        Date d = cal.getTime();
        System.out.println(new SimpleDateFormat("yyyy-MM-dd은 F번째 E요일입니다.").format(d));
        
       
        cal.add(Calendar.MONTH, 1);
        cal.set(Calendar.DAY_OF_MONTH,1);
}
```

<br>