# Day09作业

```text
day09作业
1.掌握继承
2.了解重载重写
3.了解抽象类 抽象方法
4.掌握extends final abstract super this 关键字使用
```

### 1.掌握继承

java类是单继承 ,java类不支持多继承。

继承关键字 `extends`

```java
class B{
}
class A extends B{
}
//final 类为最终类，没有子类，不能被extends继承
```



### 2.了解重载重写

- 重载(overloading) 是在一个类里面，方法名字相同，而参数不同。返回类型可以相同也可以不同。

  每个重载的方法（或者构造函数）都必须有一个独一无二的参数类型列表。

  最常用的地方就是构造器的重载。

  ```java
  //重载test方法
  public class Overloading {
      public int test(){
          System.out.println("test1");
          return 1;
      }
   	//参数个数不同
      public void test(int a){
          System.out.println("test2");
      }   
   
      //以下两个参数类型顺序不同
      public String test(int a,String s){
          System.out.println("test3");
          return "returntest3";
      }   
   
      public String test(String s,int a){
          System.out.println("test4");
          return "returntest4";
      }   
   
      public static void main(String[] args){
          Overloading o = new Overloading();
          System.out.println(o.test());
          o.test(1);
          System.out.println(o.test(1,"test3"));
          System.out.println(o.test("test4",1));
      }
  }
  ```

  

- 重写(Override)：重写是子类对父类的允许访问的方法的实现过程进行重新编写, 返回值和形参都不能改变。**即外壳不变，核心重写！**

  详见菜鸟教程：https://www.runoob.com/java/java-override-overload.html

  ```java
  //重写 父类的方法
  class Animal{
     public void move(){
        System.out.println("动物可以移动");
     }
  }
   
  class Dog extends Animal{
     public void move(){
        System.out.println("狗可以跑和走");
     }
  }
   
  public class TestDog{
     public static void main(String args[]){
        Animal a = new Animal(); // Animal 对象
        Animal b = new Dog(); // Dog 对象
   
        a.move();// 执行 Animal 类的方法
   
        b.move();//执行 Dog 类的方法
     }
  }
  ```

  结果：

  ```text
  动物可以移动
  狗可以跑和走
  ```

  **`注：1.不能通过返回值的类型判断两个方法是否构成重载也就是说重载与返回值的类型无关`**

  **`2.final 类没有子类，final 属性为常量，final方法不能被子类重写`**

### 3.了解抽象方法 抽象类

- 抽象类：在面向对象的概念中，所有的对象都是通过类来描绘的，但是反过来，并不是所有的类都是用来描绘对象的，如果一个类中没有包含足够的信息来描绘一个具体的对象，这样的类就是抽象类。

  抽象类除了不能实例化对象之外，类的其它功能依然存在，成员变量、成员方法和构造方法的访问方式和普通类一样。

  由于抽象类不能实例化对象，**所以抽象类必须被继承**，才能被使用。也是因为这个原因，通常在设计阶段决定要不要设计抽象类。

  父类包含了子类集合的常见的方法，但是由于父类本身是抽象的，所以不能使用这些方法。

  **在 Java 中抽象类表示的是一种继承关系，一个类只能继承一个抽象类，而一个类却可以实现多个接口。**

  ```java
  //这就是一个抽象类
  public abstract class Book {
      //这是一个抽象方法
      public abstract void print();
  
      public int sum(int a, int b) {
          return a + b;
      }
  
      public static void main(String[] args) {
      }
  }
  ```

  

- 抽象方法：如果你想设计这样一个类，该类包含一个特别的成员方法，该方法的具体实现由它的子类确定，那么你可以在父类中声明该方法为抽象方法。

  Abstract 关键字同样可以用来声明抽象方法，**抽象方法只包含一个方法名，而没有方法体**。

  抽象方法没有定义，**方法名后面直接跟一个分号**，而不是花括号。

  ```java
  //这就是一个抽象类
  public abstract class Employee
  {
     private String name;
     private String address;
     private int number;
      
     //这是一个抽象方法
     public abstract double computePay();
     
     //其余代码
  }
  ```

#### 声明抽象方法会造成以下两个结果：

- 如果一个类包含抽象方法，那么该类必须是抽象类。
- 任何子类必须重写父类的抽象方法，或者声明自身为抽象类。

继承抽象方法的子类必须重写该方法。否则，该子类也必须声明为抽象类。最终，必须有子类实现该抽象方法，否则，从最初的父类到最终的子类都不能用来实例化对象。

**`注：1.抽象方法是不能私有的private修饰`**

**`2.有抽象方法的类必须抽象类，抽象类可有抽象方法，也可有普通方法，也可以没有抽象方法`**

**`3.抽象更像一种编程规范，一般是项目经理，架构师编写的多。`**

### 4.掌握extends final abstract super this 关键字使用

- extends :继承

- final（adj. 最终的，）：final 类没有子类，final 属性为常量，final方法不能被子类重写
- abstract ：抽象类 抽象方法

- super ：父类 

- this：代表所在类的对象 

  - this的本质是：this 是个对象

    谁调用方法  this就是谁

    哪个对象调用 方法  this 就代表那个对象.

    每一个成员方法中都自带一个this

  - this 的作用：调用本类的成员(变量,方法)

    (所有的成员 都有调用者)  正常情况下  可以以省略 this.

    什么时候必须写?	解决局部变量和 成员变量重名的问题。

- java中使用变量的原则是：  就近原则。





 ###  5.B继承A的时候静态代码块的执行

```java
//父类
public class A {
    //类的静态方法 类名.print()调用
    public static void print(){
        System.out.println("我是一个A类的静态方法");
    }
    public int id = 3;
    //类的静态变量 类名.age调用
    public static int age = 18;

    public A(int id) {
        this.id = id;
    }
    /*初始化程序块*/
    {
        System.out.println("我是A类的第一个代码块");
    }
    //方法
    public void print1() {
        System.out.println("我是一个A类的成员方法");
    }
    /*静态程序块 */
    static {
        System.out.println("我是A类静态代码块");
    }
    {
        System.out.println("我是A类第二个代码块");
    }
}
```



```java
//A的子类
public class B extends A {
    public int id = 3;
    //A类若无空参构造 则以下代码错误·
    //原因：因为先调父类的构造方法 每次new子类时
    //public B() {
    //    super();
    //}
    public B() {
        super(5);
    }
    //类的静态方法 类名.print()调用
    public static void print(){
        System.out.println("我是一个B类的静态方法");
    }
    //类的静态变量 类名.age调用
    public static int age = 20;

    /*初始化程序块*/
    {
        System.out.println("我是B类的第一个代码块");
    }
    /*静态程序块 */
    static {
        System.out.println("我是B类静态代码块");
    }
    {
        System.out.println("我是B类第二个代码块");
    }
}
```

```java
//测试类
public class TestAB {
    public static void main(String[] args) {
        B b = new B();
    }
}

```

输出结果：

```text
我是A类静态代码块
我是B类静态代码块
我是A类的第一个代码块
我是A类第二个代码块
我是B类的第一个代码块
我是B类第二个代码块
```

分析：先执行的是静态代码块 先加载父类的静态代码块然后子类的静态代码块   

​			然后是初始化代码块 也是先加载父类的 