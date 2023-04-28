### 1.next和nextLine的区别

**next：**

它会自动地消除有效字符之前的空格，只返回输入的字符，不会得到带空格的字符串。

也就是说如果输入了一串字符，到了有空格的时候就会停止录入，只录入空格前面的东西，空格后面的东西（包括分隔的空格都会保留在缓存区域）

除了空格以外，Tab键和Enter键都被视为分隔符（结束符）。

**nextLine:**

它返回的是Enter键之前的所有字符，它是可以得到带空格的字符串的。

也就是说输入一串字符，它就可以接受所有字符包括空格，但是遇到回车Enter就会停止录入，只录入前面的东西。

**注意：**1.next（）和nextInt（）一起使用

​			2.如果单纯的输入字符串建议使用nextLine()

​			3.如果急要录入字符串又要录入整数 

​					推荐使用next 

​					也可以使用两个对象

​					也可以使用nextLine接受 然后转换为数字

### 2.String和StringBuilder拼接字符串的效率比较

```
//String和StringBuilder 拼接字符串 效率对比
long l = System.currentTimeMillis();
StringBuilder stringBuilder = new StringBuilder("aaa");
for (int i = 0; i < 10000; i++) {
    stringBuilder.append("c");
}
long l1 = System.currentTimeMillis();
System.out.println(l1-l);

long l2 = System.currentTimeMillis();
String str="aaa";
for (int i = 0; i < 10000; i++) {
    str+="c";
}
long l3 = System.currentTimeMillis();
System.out.println(l3-l2);
```

### 3.String s< -->char[] ch 相互转换

```
//String s ->char[] ch
String s="lsy";
char[] ch = s.toCharArray();
System.out.println(Arrays.toString(ch));//[l, s, y]
//char[] ch -> String s
String s1 = new String(ch);
System.out.println(s1);//lsy
```

### 4.链式编程的例子

```
//链式编程案例 只要返回的是一个对象就可以调用对象的方法
StringBuilder sb = new StringBuilder();
System.out.println(sb.append("jfks").append("123").append(123));
```





static修饰的成员属于类，与类一起加载一次。

同一个类中,静态方法只能使用静态修饰的成员变量和成员方法
