# Day08作业

```text
day08作业
1)了解多维数组，了解java.util.Arrays工具类使用
2)了解面向对象 类 对象 属性 方法？
3)掌握声明类，使用类，导入import 类，实例化对象。
4)掌握入口方法编写和执行，传参
5)掌握构造方法的编写
6)编写一个方法，功能要求，传入一个日期对象，返回一个字符串，字符串结果就是前边的微信留言时间
效果
7)编写一个工具jar程序包，再编写一个程序类来调用那个程序包？
8）单例设计模式 只能new一次 要点构造方法私有化
```

### 1.了解多维数组，了解java.util.Arrays工具类使用

```java
    //二维数组 遍历 定义 以及Arrays类的使用  fill sort toString deepToString
    //静态初始化
    int[][] arr = { {2, 3, 4, 5},
                    {6, 6, 7, 8},
                    {8, 3, 2, 1},};//int[3][4]
    //输出二维数组
    System.out.println(Arrays.deepToString(arr));
    System.out.println(arr[1][2]);//7
    //动态初始化
    int[][] arr1=new int[2][2];
    for (int[] ints : arr1) {
        Arrays.fill(ints,3);
    }
    //输出二维数组
    System.out.println(Arrays.deepToString(arr1));

    //输出三维数组
    int[][][] arr2 = {  {{2, 3, 4, 5},{1,2,1,1}},
                        {{6, 6, 7, 8},{2, 3, 4, 5}},
                        {{8, 3, 2, 1},{2, 3, 4, 5}}};//int[3][2][4]
    System.out.println(Arrays.deepToString(arr2));
    //System.out.println(arr2[1][1].length);

    int[] arr={1,54,6,46,7,33,45,35,34,53,46,3,554,5};
    System.out.println(Arrays.toString(arr));
    //升序排列
    Arrays.sort(arr);
    System.out.println("升序排列：");
    System.out.println(Arrays.toString(arr));

    Integer[] arr1={1,54,6,46,7,33,45,35,34,53,46,3,554,5};
    //降序排列
    Arrays.sort(arr1,(a,b)->b-a);
    System.out.println("降序排列：");
    System.out.println(Arrays.toString(arr1));
```

### 2.了解面向对象 类 对象 属性 方法？

`User.java文件有三个类外部类User、Teacher，内部类 User.Book`

`静态代码块先执行（可能是存在堆里的静态变量区），然后是代码块 `

`创建多个对象时，静态代码块只执行一次，代码块执行多次`

```java
package day08.cn;

public class User {

    //类的静态方法 类名.print()调用
    public static void print(){
        System.out.println("我是一个类的静态方法");
    }
    //类的静态变量 类名.age调用
    public static int age = 18;

    /*初始化程序块*/
    {
        System.out.println("我是第一个代码块");
    }

    /*成员 类 内部类*/
    class Book {

    }
    //对象
    //以文件形式管理信息。
    //属性
    public int id = 3;

    //方法
    public void print1() {
        System.out.println("我是一个类的成员方法");
    }

    /*静态程序块 */
    static {
        System.out.println("我是静态代码块");
    }

    {
        System.out.println("我是第二个代码块");
    }
}
class  Teacher{

}
```

`User测试类:`

```java
package day08.cn;

public class TestUser {
    public static void main(String[] args) {
        //调用类的静态属性和方法
        User.print();
        System.out.println(User.age);

        //使用对象调用成员方法
        //new 对象时 相当于使用 new 构造器()
        User user = new User();
        user.print1();
        System.out.println(user.id);
        System.out.println("----------------");
        User user1 = new User();
    }
}

```

`输出结果：`

```cmd
我是静态代码块
我是一个类的静态方法
18
我是第一个代码块
我是第二个代码块
我是一个类的成员方法
3
----------------
我是第一个代码块
我是第二个代码块
```

### 3.掌握声明类，使用类，导入import 类，实例化对象。

见上面代码

### 4.掌握入口方法编写和执行，传参

![](https://raw.githubusercontent.com/shiyin-li/pic/master/img/202302152029977.png)

![image-20230215210634602](https://raw.githubusercontent.com/shiyin-li/pic/master/img/202302152106644.png)

### 5.掌握构造方法的编写

`尽量写空参构造，lombok 使用注解生成getter setter 构造方法等等`

```java
package day08.cn;

import lombok.AllArgsConstructor;
import lombok.Builder;
import lombok.Data;
import lombok.NoArgsConstructor;

//lombok 注解 alt+F7看类的方法和属性
@Data
@AllArgsConstructor
@NoArgsConstructor
@Builder
public class Student implements  Comparable<Student>{
    private int age;
    private String name;
    private int score;
    private String province;
    private boolean sex;

    @Override
    public int compareTo(Student o) {
        //按照得分排序
        return this.score-o.score;
        //按照名字排序
        //return this.name.compareTo(o.name);
    }
}

```

### 6.编写一个方法，功能要求，传入一个日期对象，返回一个字符串，字符串结果就是前边的微信留言时间效果

```java
package day07.cn.lsy;

import javax.xml.crypto.Data;
import java.util.Calendar;
import java.util.Date;

public class 微信信息时间显示效果案例带参数版 {
    public static void main(String[] args) {
        Date date = new Date(1676463234706L);
        wxTimeShow(date);
    }
    public static void wxTimeShow(Date date) {
        Calendar calendar = Calendar.getInstance();
        long time = calendar.getTimeInMillis();//获取当前时间戳
        //System.out.printf("%tF %<tT",time);

        long time1 = date.getTime();//获取设置时间的时间戳

        long l = time - time1;
        long minutes = l / (1000 * 60 );
        long hours = minutes/60;
        long days = hours/24;
        long months =days/30;


        String s = "你好，在吗？";
        if (minutes<1) {
            System.out.printf("刚刚：%s", s);
        } else if (minutes >= 1&&hours<1) {
            System.out.printf("%d分钟前：%s",minutes, s);
        }else if (hours >= 1&&days<1) {
            System.out.printf("%d小时前：%s",hours, s);
        }else if (days >= 1&&months<1) {
            System.out.printf("%d天前：%s",days, s);
        }else if (months >= 1&&months<3) {
            System.out.printf("%d月前：%s",months, s);
        }else {
            System.out.printf("%tF %<tT:%s",time, s);
        }
    }
}
```

### 7.编写一个工具jar程序包，再编写一个程序类来调用那个程序包？

```java
```

### 8.单例设计模式 只能new一次 要点构造方法私有化

##### 设计模式有一个开闭原则：对于扩展是开放的，但是对于修改是封闭的

`注意：`

- 1、单例类只能有一个实例。

- 2、单例类必须自己创建自己的唯一实例。 
- 3、单例类必须给所有其他对象提供这一实例。

```java
package day08.cn;

public class Stu {
    //构造方法私有
    private Stu() {
    }
	//定义Stu静态变量 存放在堆的静态变量区
    public static Stu stu;
	//如果存在对象则调用静态变量区的，后者则创建对象
    public static Stu getInstance() {
        if (stu == null) {
            stu = new Stu();
        }
        return stu;
    }
}
```

