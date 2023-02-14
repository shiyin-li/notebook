# Day06作业

```text
1. if 编写分时问候程序
2. switch语句及表达式使用，根据指定的年月计算输出该月有多少天？
3. 打印九九乘法表
4. 打印菱形图案
5. 编写猜数游戏 重点
6. 百钱百鸡（算法）
7. 微信信息时间显示效果案例
    一分钟内 刚刚
    一小时内 几分钟前
    一天内   几小时前
    一个月内  几天前
    其他     显示标准时间格式
    2022 10 19 17:46:30 刚刚
    5分钟前
    2小时前
    3天前
    2022 10 19 17：46：30
8.随机生成两个日期之间的日期
```

### 2. switch语句及表达式使用，根据指定的年月计算输出该月有多少天？

```java
    public static void main(String[] args) {
         //2. switch语句及表达式使用，根据指定的年月计算输出该月有多少天？
        System.out.println("输入999停止查询");
        while (true) {
            Scanner scanner = new Scanner(System.in);
            System.out.println("请输入要查询的年份：");
            int year = scanner.nextInt();
            isStop(year);
            System.out.println("请输入要查询的月份：");
            int month = scanner.nextInt();
            isStop(month);

            while (year<0){
                System.out.println("你输入的年份不存在，请重新输入：");
                year = scanner.nextInt();
                isStop(year);
            }
            while (month<0||month>12){
                System.out.println("你输入的月份不存在，请重新输入：");
                month = scanner.nextInt();
                isStop(month);
            }
            switch (month){
                case 1:
                case 3:
                case 5:
                case 7:
                case 8:
                case 10:
                case 12:
                    System.out.printf("%d年%d月有：31天%n",year,month);
                    break;
                case 2:
                    System.out.printf("%d年%d月有：%d%n",year,month, year % 4 == 0 && year % 100 != 0 || year % 400 == 0 ? 29 : 28);
                    break;
                default:
                    System.out.printf("%d年%d月有：30天%n",year,month);

            }
        }
    }

    private static void isStop(int a) {
        if (a==999) {
            System.exit(0);
        }
    }

```

### 3. 打印九九乘法表

`注意：格式化/t 制表符 直接左对齐`

```java
   //九九乘法表
        for (int a = 1; a <= 9; a++) {
            for (int b = 1; b <= a; b++) {
                System.out.printf("%d*%d=%d\t", b, a, a * b);
            }
            System.out.println();
        }
    }
```

### 4. 打印菱形图案

```java
//菱形
        int a = 20;
        for (int i = 0; i <= 10; i += 2) {
            --a;
            for (int s = a; s > 0; s--) {
                System.out.print(" ");
            }
            for (int j = 1; j < i; j++) {
                System.out.print("*");
            }
            System.out.println();
        }
        for (int i = 8; i > 0; i -= 2) {
            a++;
            for (int s = a; s > 0; s--) {
                System.out.print(" ");
            }
            for (int j = 1; j < i; j++) {
                System.out.print("*");
            }
            System.out.println();
        }
```

### 6. 百钱百鸡（算法）

```java
        //鸡翁一值钱五，鸡母一值钱三，鸡雏三值钱一。百钱买百鸡，问鸡翁、鸡母、鸡雏各几何
        int x, y, z;//x鸡翁 y母鸡 z鸡雏
        for (int k = 0; k <= 4; k++) {
            x = 4 * k;
            y = 25 - 7 * k;
            z = 3 * k + 75;
            if (x >= 0 && x % 1 == 0 && y >= 0 && y % 1 == 0) {
                System.out.printf("鸡翁：%d鸡母：%d鸡雏：%d", x, y, z);
                System.out.println();
            }
        }
```

### 7.微信信息时间显示效果案例

`注意：Calender 类的月份是：0~11`

```text
一分钟内 刚刚
一小时内 几分钟前
一天内   几小时前
一个月内  几天前
其他     显示标准时间格式

2022 10 19 17:46:30 刚刚
5分钟前
2小时前
3天前
2022 10 19 17：46：30
```

```java
        Calendar calendar = Calendar.getInstance();
        long time = calendar.getTimeInMillis();//获取当前时间戳
        //System.out.printf("%tF %<tT",time);
        calendar.set(2023, 0, 14, 18, 21, 11);
        long time1 = calendar.getTimeInMillis();//获取设置时间的时间戳
        //System.out.printf("%tF %<tT",time1);

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
```

### 8.随机生成两个日期之间的日期

```java
        Calendar calendar = Calendar.getInstance();
        //获取当前时间戳
        long timeInMillis = calendar.getTimeInMillis();
        //System.out.printf("%tF %<tT%n",timeInMillis);
        //System.out.println(timeInMillis);
        //自己设置时间
        calendar.set(-1000,1,1,0,0,0);
        long timeInMillis1 = calendar.getTimeInMillis();
        //System.out.println(timeInMillis1);
        Random random = new Random();
        //两个时间戳的差值
        long sub=timeInMillis-timeInMillis1;
        int i=0;
        //返回十个随机日期
        while (i<10) {
            i++;
            long l=sub+1;
            //直至返回 一个符合-sub~sub范围的long类型的数据
            while (l>sub){
                l = Math.abs(random.nextLong());
            }
            long suiji = l + timeInMillis1;
            System.out.printf("%tF %<tT%n",suiji);
        }

```

