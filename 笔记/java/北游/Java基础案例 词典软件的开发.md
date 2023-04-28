# Java基础案例 词典软件的开发

## 1.idea建立项目

![image-20230209145818745](https://raw.githubusercontent.com/shiyin-li/pic/master/img/202302091946311.png)

## 2.填加项目依赖

下载jsoup组件

![image-20230209151551851](https://raw.githubusercontent.com/shiyin-li/pic/master/img/202302091950265.png)



导jar包

![image-20230209151522057](https://raw.githubusercontent.com/shiyin-li/pic/master/img/202302091950105.png)

## 3.编写主程序测试

![image-20230209152348490](https://raw.githubusercontent.com/shiyin-li/pic/master/img/202302091950333.png)

  测试

![image-20230209152411166](https://raw.githubusercontent.com/shiyin-li/pic/master/img/202302091959173.png)

![image-20230209152417498](https://raw.githubusercontent.com/shiyin-li/pic/master/img/202302091955017.png)

## 4.打jar包

![image-20230209155300338](https://raw.githubusercontent.com/shiyin-li/pic/master/img/202302091958815.png)

![image-20230209165213233](https://raw.githubusercontent.com/shiyin-li/pic/master/img/202302091955728.png)

bulid一下

![image-20230209165424389](https://raw.githubusercontent.com/shiyin-li/pic/master/img/202302091955712.png)

![image-20230209165442321](https://raw.githubusercontent.com/shiyin-li/pic/master/img/202302091959869.png)

文件目录结构

![image-20230209165504964](https://raw.githubusercontent.com/shiyin-li/pic/master/img/202302091959401.png)

## 5.将jar包放到桌面的dict文件夹

使用黑窗口运行

```cmd
java -jar javase.jar
```



![image-20230209170111421](https://raw.githubusercontent.com/shiyin-li/pic/master/img/202302091955880.png)

## 6.建立jre运行环境，使软件独立运行

```cmd
jdk9以后没有jre，如下命令建立jre程序目录
bin\jlink --module-path jmods --add-modules java.desktop,java.base --output jre
```

我用的是jdk1.8 直接copy过来使用

![image-20230209170605914](https://raw.githubusercontent.com/shiyin-li/pic/master/img/202302091955580.png)



## 7.建立启动软件文件方式

创建 dict.bat 文件

```java
start ./jre/bin/javaw -jar javase.jar
```

![image-20230209171032731](https://raw.githubusercontent.com/shiyin-li/pic/master/img/202302091959533.png)

