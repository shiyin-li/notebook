# Day09笔记

### 1.构造方法![image-20230216092623680](https://raw.githubusercontent.com/shiyin-li/pic/master/img/202302160926779.png)

### 2.[链式编程](https://www.jianshu.com/p/a8c51f220189) 

在使用`jquery`时肯定对它的链式编程惊艳到，慢慢的其它语言这种编程模式也逐渐增多。其本身并不复杂，在调用方法时，方法最后返回对象本身，以达到链式编程的效果。

链式编程比较简单，只要`return this`即可具有相应的编程模式，但是需要根据业务需求使用不同的方法方式进行实现。

#### 简单的链式编程

每次设置set时都返回Book对象

```java
//链式编程
public class Book {
    private String bookId;
    private String title;
    private String cover;

    public String getBookId() {
        return bookId;
    }

    public Book setBookId(String bookId) {
        this.bookId = bookId;
        // 返回当前对象
        return this;
    }

    public String getTitle() {
        return title;
    }

    public Book setTitle(String title) {
        this.title = title;
        // 返回当前对象
        return this;
    }

    public String getCover() {
        return cover;
    }

    public Book setCover(String cover) {
        this.cover = cover;
        // 返回当前对象
        return this;
    }

    @Override
    public String toString() {
        return "Book{" +
                "bookId='" + bookId + '\'' +
                ", title='" + title + '\'' +
                ", cover='" + cover + '\'' +
                '}';
    }
}
```

代码比较简单，就是一个图书的模型，将三个字段的Set方法都返回了对象本身。看一下调用

```java
public class TestBook {
    public static void main(String[] args) {
        Book book = new Book().setBookId("b.001").setTitle("庆余年").setCover("http://localhost/qyn.jpg");
        System.out.println(book);
    }
        // Book{bookId='b.001', title='庆余年', cover='http://localhost/qyn.jpg'}
}

```

### 3.编写一个工具jar程序包，再编写一个程序类来调用那个程序包？

1.先编写代码 建议创建一个新的项目 好操作

```java
import java.time.LocalDateTime;
import java.time.ZoneOffset;
import java.util.Calendar;
import java.util.Date;

public class WxMsgUtil {
    public static String wxTimeShow(long time1) {
        Calendar calendar = Calendar.getInstance();
        long time = calendar.getTimeInMillis();//获取当前时间戳

        long l = time - time1;
        long minutes = l / (1000 * 60);
        long hours = minutes / 60;
        long days = hours / 24;
        long months = days / 30;

        String s = "";
        if (minutes < 1) {
            s = "刚刚";
        } else if (minutes >= 1 && hours < 1) {
            s = String.format("%d分钟前", minutes);
        } else if (hours >= 1 && days < 1) {
            s = String.format("%d小时前", hours);
        } else if (days >= 1 && months < 1) {
            s = String.format("%d天前", days);
        } else if (months >= 1 && months < 3) {
            s = String.format("%d月前", months);
        } else {
            s = String.format("%tF %<tT", time1);
        }
        return s;
    }

    public static String wxTimeShow(Date date) {
        return wxTimeShow(date.getTime());
    }

    public static String wxTimeShow(Calendar calendar) {
        return wxTimeShow(calendar.getTimeInMillis());
    }

    //https://blog.51cto.com/u_15278282/2931888
    //Java8的时间转为时间戳的大概的思路就是LocalDateTime先转为Instant，设置时区，然后转timestamp(时间戳)。
    public static String wxTimeShow(LocalDateTime localDateTime) {
        return wxTimeShow(localDateTime.toInstant(ZoneOffset.of("+8")).toEpochMilli());
    }

}

```

2.打包

![image-20230216105520935](https://raw.githubusercontent.com/shiyin-li/pic/master/img/202302161147705.png)

![image-20230216110618134](https://raw.githubusercontent.com/shiyin-li/pic/master/img/202302161147139.png)

![image-20230216110649860](https://raw.githubusercontent.com/shiyin-li/pic/master/img/202302161147097.png)

![image-20230216110706648](https://raw.githubusercontent.com/shiyin-li/pic/master/img/202302161147535.png)

3.打包后的目录结构：

![image-20230216110739640](https://raw.githubusercontent.com/shiyin-li/pic/master/img/202302161147876.png)

![image-20230216111112033](https://raw.githubusercontent.com/shiyin-li/pic/master/img/202302161147779.png)

4.导jar使用自己包里的方法

![image-20230216111753865](https://raw.githubusercontent.com/shiyin-li/pic/master/img/202302161148708.png)

5.效果图

![image-20230216111948039](https://raw.githubusercontent.com/shiyin-li/pic/master/img/202302161148577.png)