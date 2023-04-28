# Day10作业

day10作业：
1）声明定义 interface接口   

2）声明定义 类 实现 interface接口

3）掌握继承关系父类 子类（初始化块 静态块 构造方法）执行顺序 class

- 先执行的是静态代码块 先加载父类的静态代码块然后子类的静态代码块   

- 然后是初始化代码块 也是先加载父类的 

- 最后执行构造方法 也是先加载父类的

  `注：见Day09作业最后`

4）、掌握什么是抽象类？什么是抽象方法？abstract class  abstract void print(){}

- 抽象类可以没有抽象方法 也可以有抽象方法
- 有抽象方法的类必须是抽象类 
- 抽象类的一般都public，还有默认的 ， private(没啥意思)   无protected

5）、掌握接口都包括哪些内容？interface

接口声明使用interface关键字 interface Api{}

- java 1.7 之前的接口规则：接口 = 常量 + 抽象方法

- java 1.8 接口新定义规则：接口 = 常量（多个） + 抽象方法（多个） + default实现方法(多个) + static实现方法(多个)

- java 1.8 接口函数式接口规则: 接口 = 常量 + default实现方法 + static实现方法 + 抽象方法（有且只有一个抽象方法）
- 接口都public，还有默认的 ， 无private（本来就是被别人实现的私有干嘛）  无protected
- **函数式接口概念？**有且只有一个抽象方法的接口，默认是函数式接口，函数式接口可以使用lambda表达式作为方法接口参数来执行。

6）、了解声明抽象类、声明接口？

**单继承多实现** 

- 单继承是指类的继承是单继承  
- 多实现是指类可以实现多个接口 接口可以继承多个接口 

```java
   abstract class A{

   }

   interface B extends C,D,E{

   }
```

7）、了解装箱、拆箱操作，八大基本类型和相应的对象类型
    int Integer
    long Long
    boolean Boolean
    short Short
    byte Byte
    char Character
    double Double
    float Float

8）、掌握面向对象的静态static

- ​	静态方法 可以由静态方法调用

- ​	类中的静态方法可以直接类名.方法名()调用


9）、编写程序，实现如下接口功能，体会接口的使用
（1）编写 DbDao接口

```java
public interface DbDao {
boolean connect();int save();

int delById();

int update();

void query();
}
```
（2）编写DbDao接口实现类


```java
public class DbDaoMysqlImpl implements DbDao {
@Override
public boolean connect() {
    System.out.println("Mysql connect success...");
    //xx/
    //fff
    //xx
    return true;

}

@Override
public int save() {
    System.out.println("mysql 数据保存成功");
    return 0;
}

@Override
public int delById() {
    System.out.println("mysql删除完成");
    return 0;
}

@Override
public int update() {
    System.out.println("mysql修改完成");
    return 0;
}

@Override
public void query() {
    System.out.println("mysql 查询所有");
}
}
```
（3）编写DbDao接口实现类


```java
public class DbDaoPgsqlImpl implements DbDao{
    @Override
    public boolean connect() {
        System.out.println("PostgreSql Connection success...");
        return false;
    }
@Override
public int save() {
    return 0;
}

@Override
public int delById() {
    return 0;
}

@Override
public int update() {
    return 0;
}

@Override
public void query() {
    System.out.println("pgsql 查询数据成功");
}
}
```
（4）编写Demo测试程序



```java
public class Demo {
    public static void main(String[] args) {
        DbDao db = new DbDaoPgsqlImpl();
        db.connect();
        db.query();db = new DbDaoMysqlImpl();
    db.connect();
    db.query();
}
}
```




---------------------------------------------
接口 interface
  1)接口 api 程序接口  app = web前端 + 后端（程序 数据库）api

  2)java 编程接口是一种编程规范对象 interface

  3)声明接口，是一种编程规范，约束程序人员编写类的
     java 8 以前接口只能包括如下内容：
	全局静态常量
	抽象方法

 java 8开始接口包括内容如下：
全局静态常量 int i = 3 ;
	也是public final static int i =3;
抽象方法 void conn();
         自动是 public abstract void conn();

静态实现方法 static
	public static void conn(){
	}
使用的时候可以直接通过接口 Db.conn();

默认实现方法 default
	public default int pf(int i){
	      reutrn i*i;
	}
	使用的时候，通过接口的实现类的对象实例来调用执行。

函数式接口(接口中有且只有一个抽象方法的接口)
        使用的时候，是通过lambda表达式使用
	()->{} java lambda表达式

​	()=>{} javascript 

```java
public interface Db{

}

public interface A{

}
```

//B.java 编译后也是B.class

```java
public interface B{

}
```

//接口是允许多继承的。

```java
public interface MyAll extends Db,A,B{

}
```

使用接口，一般用的是接口的实现类，在java8开可以通过接口名，直接调用执行接口的静态实现方法。

```java
interface Db{
    static int pf(int i){
    return i*i;
}
}
```


接口一般情况是不直接实例化使用，用的是接口实现类 implements 
使用接口的实现类

```java
public class DbImpl implements Db,A,B,D{

}

class A extends B implements C,D,E{

}

B b = new A();
C c = new A();
D d = new A();
E e = new A();
A aa = new A();

List list = new ArrayList();  //List 接口 和 ArrayList List接口的实现类
使用接口的静态方法
System.out.println(Db.pf(3));			
```

//java 8 以前
interface A{
   //常量

   //抽象方法（）不使用abstract 
}
java 8开始
 	interface B{
    //常量
    //抽象方法
    //default 默认实现方法
    //static 静态实现方法
}

  B b = new B();

  A a = new B(); //A B关系 （1）B继承extends了A  （2）B是A接口的实现类implements