# Day05

```text
day05作业
------------------------------------
1、掌握String.format() 或 System.out.printf()格式化输出方法
2、了解格式化数字
百分比
小数位
货币符号
千分位
3、掌握日期对象的格式化方法
4、使用随机编写一个中奖30%的案例
5、编写程序输出今日是星期几
6、编写程序输出 xxxx年xx月xx日 xx:xx:xx 星期几
```

### 1.掌握String.format() 或 System.out.printf()格式化输出方法

```java
 //格式化日期
        System.out.printf("%tY年%<tm月%<td日 %<ta %<tA %n", System.currentTimeMillis());
        // %tA星期
        System.out.printf("%tA%n", System.currentTimeMillis());
        System.out.printf("%tA  %<ta  %n", LocalDate.of(2000, 5, 1));

        //格式化字符串
        String name = "lsy";
        int age = 19;
        String address = "河南郑州市科学大道33号";
        String str1 = "姓名" + name + ",年龄：" + age + "岁，家庭住址：" + address + "。";
        System.out.println(str1);

        String str2 = String.format("姓名:%s,年龄：%d岁，家庭地址：%s。", name, age, address);
        System.out.println(str2);

        System.out.printf("姓名：%s ,年龄：%d，家庭住址：%s", name, age, address);
        //格式化小数
        double random = Math.random();
        System.out.println(random);
        System.out.printf("%.1f %<.3f %<.4f %<.0f %n", random);//0.6 0.607 0.6071 1
        System.out.printf("%.1f %.2f %<.3f %<.4f %<.0f %n  ", random, 134.5345);

        //格式化日期  < %tF 2023-02-10 %tc 14:01:53
        System.out.printf("%tF %<tT %<tc%n", System.currentTimeMillis());
        System.out.printf("%tY年 %<tm月 %<td %<tp %<tA %<ts %n", System.currentTimeMillis());
        //时分秒
        System.out.printf("%tH时%<tM分%<tS秒  %n", System.currentTimeMillis());


        //格式化整数 字符串
        System.out.printf("%d%n%<05d%n%<5d%n", 123);
        System.out.printf("%s%n%<10s%n%<20s%n", "lsy java");


        Random rand = new Random();
        double money = rand.nextDouble() + 99.999;
        System.out.printf("%.2f元%n", money);
        System.out.printf("%.3f元%n", money);
        System.out.printf("%.0f元%n", money);
        System.out.printf("%10.4f%n", money);
        System.out.printf("%10.4f%n", 1f);

```

### 2.了解格式化数字

```java
//格式化百分比
        double d=Math.random();
        System.out.printf("格式化：%.3f%n",d);//
        System.out.println(d);//0.2912256386404384
        NumberFormat format = NumberFormat.getPercentInstance();
        System.out.println("百分比："+format.format(d));//百分比：29%
        //格式化小数
        format.setMinimumFractionDigits(2);
        System.out.println(format.format(d));//29.12%

        //格式化货币
        double money = 85934283.9458903;
        System.out.println(money);//8.59342839458903E7
        NumberFormat format1 = NumberFormat.getCurrencyInstance(Locale.JAPAN);
        System.out.println(format1.format(money));//￥85,934,284
        NumberFormat format2 = NumberFormat.getCurrencyInstance(Locale.US);
        System.out.println(format2.format(money));//$85,934,283.95
        System.out.printf("$%.2f%n",money);//$85934283.95

        //格式化千分位
        long l = 45835678342758977L;
        double random = Math.random();
        NumberFormat format3 = NumberFormat.getCurrencyInstance();//默认china
        System.out.println(format3.format(l));//￥45,835,678,342,758,977.00
        System.out.println(random);//0.7139872054541123

        format3.setMinimumFractionDigits(4);
        System.out.println(format3.format(random));//￥0.7140
```

### 3.掌握日期对象的格式化方法

```java
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
```

### 4.使用随机编写一个中奖30%的案例

```java
Random random=new Random();
System.out.println((random.nextInt(100)+1)<=30?"恭喜你，中奖了":"请再接再厉");
```

### 5. 编写程序输出今日是星期几

```java
 System.out.printf("%tA%n",System.currentTimeMillis());
```

### 6.编写程序输出 xxxx年xx月xx日 xx:xx:xx 星期几

```java
 System.out.printf("%tY年%<tm月%<td日  %<tH时%<tM分%<tS秒  %<ta%n",System.currentTimeMillis());
```

