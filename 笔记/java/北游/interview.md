# 面试题

## 一、基本数据类型的面试题

```java
//第一题
short s = 3;
//s=s+1  错误 类型不同 需要强转
//解决  +=有类型转换功能
s += 1;
System.out.println(s);
s = (short) (s + 1);
System.out.println(s);

//第八题
System.out.println(3 - 2.6 == 0.4);//false

System.out.println("---------------");
//第十四题
int a=10;
double b=3.4;
System.out.println(a>b?a:b);//10.0
System.out.println(a);
```



```java
1、short s1 = 1; s1 = s1 + 1;有什么错? short s1 = 1; s1 +=1;有什么错?
答案：对于short s1 = 1; s1 = s1 + 1;来说，在进行s1 + 1运算时会自动提升表达式的类型为
int，那么将int类型赋值给short类型的变量s1会出现类型转换错误。
对于short s1=1;s1+=1来说， +=是java语言规定的运算符，java编译器会对它进行特殊处理，因
此可以正确编译。

2、char类型变量能不能储存一个中文的汉子，为什么？
答案：char类型变量使用的是Unicode编码的字符，Unicode字符集包含了汉字，所以char类型当然可以存
储汉字，还有一种特殊情况就是某个生僻字没有包含在unicode编码字符集中，那么就char类型就不能
存储该生僻字。

3、Integer和int的区别
答案：
int是java的8种内置的原始数据类型。Java为每个原始类型都提供了一个封装类，Integer就是int
的封装类。int变量的默认值为0，Integer变量的默认值为null，这一点说明Integer可以区分出未赋值和值为0
的区别，比如说一名学生没来参加考试，另一名学生参加考试全答错了，那么第一名考生的成绩应该是
null，第二名考生的成绩应该是0分。关于这一点Integer应用很大的。Integer类内提供了一些关于
整数操作的一些方法，例如上文用到的表示整数的最大值和最小值。

4、switch语句(开关语句)能否作用在byte上，能否作用在long上，能否作用在String上？
答案：
byte的存储范围小于int，可以向int类型进行隐式转换，所以switch可以作用在byte上
long的存储范围大于int，不能向int进行隐式转换，只能强制转换，所以switch不可以作用在long上
String在1.7版本之前不可以，1.7版本之后switch就可以作用在string上了

5、基本数据类型和引用数据类型的区别？
答案：
（1）基本类型保存的是值，引用类型保存的是对象的地址，所有基本类型赋值是按值传递（拷贝赋
值），引用类型赋值是按引用传递。
（2）基本数据类型是存放在栈中的简单数据段。
（3）引用数据类型是存放在堆内存中的对象，在栈内存中存放的是堆内存中具体内容的引用地址，
通过这个地址可以快速查找到对象。

6、64位的JVM当中，int的长度是多少？
答案：Java 中，int 类型变量的长度是一个固定值，与平台无关，都是 32 位。意思就是说，在 32
位 和 64 位 的Java 虚拟机中，int 类型的长度是相同的4字节。

7、可以将int强转为byte类型么？会产生什么问题？
答案：可以做强制转换，但是Java中int是32位的而byte是8 位的，所以,如果强制转化int类型的高
24位将会被丢弃，byte 类型的范围是从-128到127
8、判断输出结果
public static void say() {
    System.out.println(3 - 2.6 == 0.4);
}
答案：false ->int类型和float类型做运算会损失精度所以不等，可以System.out.println(3 -
        2.6 )输出结果并不等于0.4
9、java 中 float f = 3.4; 是否正确？
答案：不正确，因为3.4是双精度类型属于double类型，而double类型范围大于float类型，如果想要
赋给float类型必须强制转 换：float f=（float）3.4或者float f=3.4F
byte->short->int->long->float->double (范围从小到大)
10、输出结果？
byte a = 127;
a+=5;
System.out.println(a);
答案：124。首先byte取值范围-128~127 当a+=1时此时已经是超过了byte的临界值此时输出的
为-128 、a+=2时输出 为-127，以此类推a+=5时输出为-124，只要记住这个技巧对于这个面试题就
可以应对了。
11、为什么long l=2000000000可以，而long l=3000000000却编译报错
答案：因为在Java中二十亿和三十亿的默认类型都是int类型的，而二十亿是在int范围类的，三十亿不
在int范围内，所以后面的long l=300000000会编译报错。解决方法：在三十亿后面加上一个大写或 者小写的L
12、为什么 int a = 09；会报错
答案：因为在进制表示中0开头的表示八进制，而八进制中不能出现大于7的数！
13、int i = 3000000000; 编译能通过吗？原因是什么？（面试题）
答案：不能通过，因为三十亿在Java中的默认数据类型为int，而三十亿不在int能够表示的范围内，所
        以不能编译通过
14、输出结果？
int a=10;
double b=3.4;
System.out.println(a>b?a:b);
System.out.println(a);
//输出：10.0 10
15、输出结果？
int a=128;
byte b=(byte)a;
System.out.println(b);//输出-128，出现了数据溢出
double c=1.23;
int d=(int)c;
System.out.println(d);//输出1，精度丢失
16、输出结果？
运算时，运算结果会向较大的类型转换
int a=3;
double b=4;
System.out.println(a+b);//输出7.0
17、为什么 byte b=10b会报错？
答案：byte在java中表示字节，而b表示的是bit
```

## 二、字符串常见面试题

​	Java 程序中所有的双引号字符串，都是 String 类的对象 

​	字符串不可变，它们的值在创建后不能被更改

 	虽然 String 的值是不可变的，但是它们可以被共享    

问题：下列代码的运行结果是？

```
public class Test1{
   public static void main(String[] args){
       String s1="abc";
       String s2="abc";  
       System.out.println(s1==s2);	
   }
}
```

分析:都在常量池中

问题：下列代码的运行结果是？    

```
public class Test2{
   public static void main(String[] args){
       String s1="abc";
       String s2=new String("abc"); //创建两个对象
       System.out.println(s1==s2);	
   }
}
```

分析: s1在常量池  , s2 在  堆内存中

问题：下列代码的运行结果是？ 

```
public class Test3 {
    public static void main(String[] args) { 
        String s1 = "abc";
        String s2 = "ab";
        String s3 = s2 + "c";
      
        System.out.println(s1 == s3);  
    }
}
```

字符串对象使用"+"  拼接  会先转成StringBuildder 在进行append方法 最后toString方法  转成String对象

问题：下列代码的运行结果是？

```
public class Test4 {
	public static void main(String[] args) { 
		String s1 = "abc";
		String s2 = "a" + "b" + "c";
		System.out.println(s1 == s2);
	}
}
```

 分析: 常量优化机制

: 常量与常量之间运算  直接算结果 再赋值

### 字符串比较

使用 == 做比较
基本类型：比较的是数据值是否相同
引用类型：比较的是地址值是否相同

字符串是对象，它比较内容是否相同，是通过一个方法来实现的，这个方法叫：equals()
  public boolean equals(Object anObject)：
  将此字符串与指定对象进 行比较。由于我们比较的是字符串对象，所以参数直接传递一个字符串

public  boolean equalsIgnoreCase?(String anotherString):忽略大小写