### 1.hashCode()和toString()

```
hashCode()
```

> **hashCoed 的特性：**
>
> （1）[HashCode](https://gitee.com/link?target=https%3A%2F%2Fso.csdn.net%2Fso%2Fsearch%3Fq%3DHashCode%26spm%3D1001.2101.3001.7020)的存在主要是用于查找的快捷性，如Hashtable，HashMap等，HashCode经常用于确定对象的存储地址；
>
> （2）如果两个对象相同， [equals](https://gitee.com/link?target=https%3A%2F%2Fso.csdn.net%2Fso%2Fsearch%3Fq%3Dequals%26spm%3D1001.2101.3001.7020)方法一定返回true，并且这两个对象的HashCode一定相同；
>
> （3）两个对象的HashCode相同，并不一定表示两个对象就相同，即equals()不一定为true，只能够说明这两个对象在一个散列存储结构中。
>
> （4）如果对象的equals方法被重写，那么对象的HashCode也尽量重写。
>
> 面试题：两个对象的 hashCode()相同，则值一定相同吗？不一定

```java
System.out.println("Ma".hashCode());//2484
System.out.println("NB".hashCode());//2484
String s1 = new String("Ma");
String s2 = new String("NB");
System.out.println(s1.hashCode()); //2484
System.out.println(s2.hashCode()); //2484
```

> 所以有可能不同的值计算出来的hashCode()相同，但是同一个值的hashCode()是不会变的，所以可以根据字符串值推算出它的hashCode(),但是不能根据hashCode()的值推算出字符串的值。

```
作用
```

> 我们平时经常用到map来存储对象，因为map是key，value形式的，它不像list形式的集合可以有顺序的从0开始往集合里放数据，而是随意的放，但是取值的话就很麻烦，因为它存放值的时候没有顺序，所以取值的时候根据key去里面一个一个对比，等找到key相等的值就取出，这样就会造成效率问题。
>
> 当我们用到hashCode()可以看到我们将name计算为3373707，age计算为98511，这样的话我们存值的时候就根据计算后的数值进行对应位置的存储，同样当我们get取值的时候再次将key计算为hashCode()值，因为同一个字符串hashCode()值相等，这个时候我们就可以直接根据hashCode()值将对应位置的数据取出，就不需要对key一个一个进行对比了，这样大大提高了效率，这就是为什么有hashCode()存在的原因了。

```
toString()
```

> toString()方法是Object类中的方法，而Java中所有的类都继承了object类。我们在使用时可以将其重写。那么，to String方法如何使用呢？

为什么不同的对象hashcode可能相同：

​		因为当输入数据量太大，哈希值却是固定32长度的，这意味着哈希值是一个有限集合，无法建立一对一关系，所以hashcode相等是有可能会发生的。

两者的关系：

- equals()相等的两个对象，hashcode()一定相等；

- equals()不相等的两个对象，hashcode()有可能相等。
- hashcode()不等，一定能推出equals()也不等；
- hashcode()相等，equals()可能相等，也可能不等。

为什么用hashCode：
hashCode()效率是比equals()效率高的。
所以HashSet判断元素是否相等时先用hashCode()判断，如果hashCode()不同，则对象不等，如果hashCode()相同，再比较equals() ，大大提高了效率。

所以我们要保证如果重写了equals()，也要重写hashCode()。

**自己的理解：**hashCode相等 equals可能相等；hashCode不相等 equals一定不相等 。（验证密码或者身份，先使用hashCode判断再用equals判断）

 **所以为什么如果对象的equals方法被重写，那么对象的HashCode也尽量重写？为何要这样做**

### 2.enum 枚举

枚举是实例对象是固定，实例是自动new，每个枚举类会自动继承java.lang.Enum 抽象
如何声明枚举？

```java
public class EnumDemo {
    enum en1 {a, b, c}
    enum color {RED, GREEN, BLUE}
    enum num {
        //这里面的参数和构造器里的参数要一样
        SUCCESS(200, "成功"), FAIL(400, "失败"), NOTFOUND(404, "未知"), ERROR(300, "错误");
        public int code;
        public String message;
        
		//构造器
        num(int code, String message) {
            this.code = code;
            this.message = message;
        }

        public static num fromCode(int code) {
            num nn = null;
            for (num v : num.values()) {
                if (v.code == code) {
                    nn = v;
                    break;
                }
            }
            return nn;
        }

        public static num valueFrom(String name) {
            return num.valueOf(name);
        }
    }

    public static void main(String[] args) {
        num n = num.SUCCESS;
        System.out.println(n);
        System.out.println(n.message);
        System.out.println(n.code);

        num err = num.fromCode(404);
        System.out.println(err.message);

        System.out.println(num.valueFrom("ERROR"));
        System.out.println(num.valueOf("ERROR"));
    }
}
```

### 3.内部类

内部类的共性内部类分为: 成员内部类、静态嵌套类、匿名内部类（直接new 抽象类，直接new 接口）112。

```
如果是函数式接口，可以使用lambda表达，这样可以避免new 接口产生内部匿名类
```

(1)、内部类仍然是一个独立的类，在编译之后内部类会被编译成独立的.class文件，但是前面冠以外部类的类名和$符号。

(2)、内部类不能用普通的方式访问。内部类是外部类的一个成员，因此内部类可以自由地访问外部类的成员变量，无论是否是private的。

(3)、外部类不能直接访问其内部类，想要访问内部类，需实例化内部类

(4)、内部类声明成静态的，就不能随便的访问外部类的成员变量了，此时内部类只能访问外部类的静态成员变量。

(5)、其他类想要直接访问内部类，可直接实例化内部类，方法如下外部类名.内部类 对象名 = new 外部类().new 内部类();

例：Out.In in = new Out().new In();

如果内部类是静态的，当其他类调用内部类可直接通过类名调用，格式如下：

外部类.内部类 对象名 = new 外部类.内部类()

例：Out.In in2 = new Out.In();

当内部类是静态的，且方法也是静态的，此时可不需实例化对象

外部类.内部类.静态方法名();

例：Out.In.fun();

System.out.print();

```
public class Outter {
    /**
     * 成员 public 静态的内部类
     */
    public static class out{
        public static void println(Object obj){
            System.out.println(obj);
        }
    }

    class Demo{

    }

    public static void main(String[] args) {
        out.println("hello world 中文效果");

        System.out.println("hello world 中文效果");

        /* 方法体，代码中，局部内容类 */
        //@Data
        class Book{
            private int id;
            private String name;

        }
    }
}

public class Test {
    public static void main(String[] args) {
        Outter.Demo demo = new Outter().new Demo();
        //System.out.println(demo);
        //内部类实现System.out.println(demo)x
        Outter.out.println(demo);
    }
}
```