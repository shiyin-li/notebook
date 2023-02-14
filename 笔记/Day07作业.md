# Day07作业

```text
1. 利用数组实现冒泡排序效果
2. 掌握一维数组，二维数组声明，遍历，使用
3. 掌握Arrays工具类的学用方法(toString(),sort(),fill())
4. 实现数组升序，降序，乱序（数字数组，字符串数组，对象数组，汉字排序机制，字符串长
度）
5.label标签的使用以及注意事项
```

### 1. 利用数组实现冒泡排序效果

```java
        int[] arr={1,54,6,46,7,33,45,35,34,53,46,3,554,5,};
        for (int i = 0; i < arr.length; i++) {
            boolean flag=false;
            for (int i1 = 0; i1 < arr.length-1-i; i1++) {
                if (arr[i1]<arr[i1+1]){
                    int temp=arr[i1];
                    arr[i1]=arr[i1+1];
                    arr[i1+1]=temp;
                    flag=true;
                }
            }
            //可能能节约时间 减少对比次数
            if (!flag){
                break;
            }
        }
        System.out.println(Arrays.toString(arr));
```

### 2. 掌握一维数组，二维数组声明，遍历，使用

### 3. 掌握Arrays工具类的学用方法(toString(),sort(),fill())

```java
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

        int[] arr2 = new int[5];
        //使用fill填充 数字全为5
        Arrays.fill(arr2,5);
        System.out.println("填充数字全为五");
        System.out.println(Arrays.toString(arr2));
```



### 4. 实现数组升序，降序，乱序（数字数组，字符串数组，对象数组，汉字排序机制，字符串长度）

```java
        //实现数组升序，降序，乱序（数字数组，字符串数组，对象数组，汉字排序机制，字符串长度）
        //字符串数组
        String[] strings={"java","mysql","javascript","vue","python","c","c++","c#"};
        //默认是字典序 升序
        Arrays.sort(strings);
        System.out.println("默认是字典序升序:");
        System.out.println(Arrays.toString(strings));
        //字典序降序
        Arrays.sort(strings,(a,b)->b.compareTo(a));
        System.out.println("字典序降序:");
        System.out.println(Arrays.toString(strings));

        Arrays.sort(strings,(a,b)->a.length()-b.length());
        System.out.println("按字符串长度升序:");
        System.out.println(Arrays.toString(strings));

        Arrays.sort(strings,(a,b)->b.length()-a.length());
        System.out.println("按字符串长度降序:");
        System.out.println(Arrays.toString(strings));

        //汉字排序机制 ？？？
        String[] strings1={"李四","王五了","赵六四点","李奇认为陆军","张三"};
        //默认是字典序 升序
        Arrays.sort(strings1);
        System.out.println("默认是字典序升序:");
        System.out.println(Arrays.toString(strings1));
        //字典序降序
        Arrays.sort(strings1,(a,b)->b.compareTo(a));
        System.out.println("字典序降序:");
        System.out.println(Arrays.toString(strings1));

        //对象数组
       Student[] students={
                new Student(20,"lsy",88,"河南",false),
                new Student(25,"pyq",67,"上海",true),
                new Student(26,"lhk",54,"河南",false),
                new Student(27,"yxz",81,"天津",true),
                new Student(31,"lfy",82,"河南",false),
                new Student(12,"zzy",64,"北京",true),
                new Student(4,"lsklf",100,"河南",false)
        };
        Arrays.sort(students);
        System.out.println(Arrays.toString(students));
```



```java
//学生类 实现Comparable接口
public class Student implements  Comparable<Student>{
    private int age;
    private String name;
    private int score;
    private String province;
    private boolean sex;

    public Student(int age, String name, int score, String province, boolean sex) {
        this.age = age;
        this.name = name;
        this.score = score;
        this.province = province;
        this.sex = sex;
    }

    public Student() {

    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getScore() {
        return score;
    }

    public void setScore(int score) {
        this.score = score;
    }

    public String getProvince() {
        return province;
    }

    public void setProvince(String province) {
        this.province = province;
    }

    public boolean isSex() {
        return sex;
    }

    public void setSex(boolean sex) {
        this.sex = sex;
    }

    @Override
    public String toString() {
        return "Student{" +
                "age=" + age +
                ", name='" + name + '\'' +
                ", score=" + score +
                ", province='" + province + '\'' +
                ", sex=" + sex +
                '}';
    }

    @Override
    public int compareTo(Student o) {
        //按照得分排序
        return this.score-o.score;
        //按照名字排序
        //return this.name.compareTo(o.name);
    }
}

```

### 5.label标签的使用以及注意事项

```java
        //label标签，主要出现在循环语句前，主要解决多层嵌套循环语句时，直接break 标签名;
        //continue 标签;进行执行跳转，变相实现了goto语句的作用。
        //label标签 只能现出现循环语句前
        ss:
        for (int i = 1; i <= 15; i++) {
            System.out.printf("%03d%n", i);
            System.out.println("---------------------------");
            while (Math.random() > 0.01) {
                double d = Math.random();
                System.out.println(d);
                if (d > .8) {
                    //直接跑到ss 循环语句结束
                    break ss;   
                    //continue ss; 跳转到ss 继续循环
                }
            }
            for (int a = 1; a <= 6; a++) {
                System.out.println(a);
            }
        }
```

