

# Day04作业

```text
day04作业：
1、掌握Calendar类实例化，add() set() get()三大方法
2、计算2023-1-1 这一天是星期几？
3、掌握LocalDate使用
4、计算两个日期之间有多少天？
5、给出一个年份，判断这一年是不是闰年？
6、掌握LocalDate、LocalTime、LocalDateTime类的format格式化方法()
```



```java
package day04.cn.lsy;

import java.text.SimpleDateFormat;
import java.time.DayOfWeek;
import java.time.LocalDate;
import java.time.LocalDateTime;
import java.time.LocalTime;
import java.time.format.DateTimeFormatter;
import java.time.format.TextStyle;
import java.time.temporal.ChronoUnit;
import java.util.Date;
import java.util.Locale;

public class HomeWork04 {
    public static void main(String[] args) {
        //作业：
        //1、掌握Calendar类实例化，add() set() get()三大方法
		Calendar c = Calendar.getInstance();
        c.setTime(new Date());
        //get方法
        int year = c.get(Calendar.YEAR);
        int hour = c.get(Calendar.HOUR_OF_DAY);
        int minute = c.get(Calendar.MINUTE);
        int second = c.get(Calendar.SECOND);
        int month = c.get(Calendar.MONTH) + 1;
        int day = c.get(Calendar.DATE);
        int weekDay = c.get(Calendar.DAY_OF_WEEK) - 1;
        System.out.printf("现在是%d年%d月%d日%d时%d分%d秒 星期%d", year, month, day, hour, minute, second, weekDay);
        int dayOfMonth = c.get(Calendar.DAY_OF_MONTH); // 获取今天是本月第几天
        System.out.println("今天是本月的第 " + dayOfMonth + " 天");
        int dayOfWeekInMonth = c.get(Calendar.DAY_OF_WEEK_IN_MONTH);
            // 获取今天是本月第几周
        System.out.println("今天是本月第 " + dayOfWeekInMonth + " 周");
        int many = c.get(Calendar.DAY_OF_YEAR); // 获取今天是今年第几天
        System.out.println("今天是今年第 " + many + " 天");
        //set方法
        c.set(2012, 8, 8);
        System.out.printf("%tF %<tT%n",c.getTime());

        //add方法 向后推7个小时
        c.add(Calendar.HOUR,-7);
        System.out.println(c.get(Calendar.HOUR_OF_DAY));
        
        //2、计算2023-1-1 这一天是星期几？
        //使用LocalDate
        LocalDate localDate = LocalDate.of(2023, 1, 1);
        String name = localDate.getDayOfWeek().getDisplayName(TextStyle.FULL, Locale.CHINA);
        System.out.println(name);
        //使用LocalDateTime
        LocalDateTime localDateTime = LocalDateTime.of(2023, 1, 1, 2, 2);
        System.out.println(localDateTime.getDayOfWeek().getDisplayName(TextStyle.FULL,
                Locale.CHINA));
        
        //3、掌握LocalDate使用
        LocalDate now = localDate.now();
        DayOfWeek dayOfWeek = now.getDayOfWeek();
        System.out.println(dayOfWeek.getValue());
        System.out.println(now.format(DateTimeFormatter.ofPattern("yyyy年MM月dd日")));
        
        //4、计算两个日期之间有多少天？
        //答：localDate 计算
        System.out.println(ChronoUnit.DAYS.between(localDate, now));
        
        //5、给出一个年份，判断这一年是不是闰年？ 4年一润 百年不润 400年在润
        //答：使用LocalDate类
        System.out.println(localDate.isLeapYear());//false 不是闰年
        
        //6、掌握LocalDate、LocalTime、LocalDateTime类的format格式化方法()
        //使用DateTimeFormatter格式化输出
        System.out.println("---------------------");
        DateTimeFormatter pattern = DateTimeFormatter.ofPattern("yyyy:MM:dd");
        DateTimeFormatter pattern1 = DateTimeFormatter.ofPattern("HH:mm:ss");
        DateTimeFormatter pattern2 = DateTimeFormatter.ofPattern("yyyy:MM:dd  HH:mm:ss");
        System.out.println(LocalDate.now().format(pattern));//LocalDate
        System.out.println(LocalTime.now().format(pattern1));//LocalTime
        System.out.println(LocalDateTime.now().format(pattern2));//LocalDateTime
        //使用printf格式化输出
        System.out.println("-------------------------");
        System.out.printf("%tF%n",LocalDate.now());//LocalDate
        System.out.printf("%tT%n",LocalTime.now());//LocalTime
        System.out.printf("%tF %<tT%n",LocalDateTime.now());//LocalDateTime
        //使用SimpleDateFormat格式化输出Date类
        SimpleDateFormat sdf = new SimpleDateFormat("yyyy-MM-dd HH:mm:ss");
        //java.util.Date()
        Date d = new Date();
        System.out.println(sdf.format(d));
    }
}

```

