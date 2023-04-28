

### 1.idea创建项目的正确流程

#### 1.正确流程

![image-20230218162851443](https://raw.githubusercontent.com/shiyin-li/pic/master/img/202302191551083.png)

![image-20230218163023161](https://raw.githubusercontent.com/shiyin-li/pic/master/img/202302191551312.png)

![image-20230218163039571](C:/Users/Administrator/AppData/Roaming/Typora/typora-user-images/image-20230218163039571.png)

![image-20230218162942914](https://raw.githubusercontent.com/shiyin-li/pic/master/img/202302191551349.png)

![image-20230218163333358](C:/Users/Administrator/AppData/Roaming/Typora/typora-user-images/image-20230218163333358.png)

![image-20230218163501649](https://raw.githubusercontent.com/shiyin-li/pic/master/img/202302191551304.png)



![image-20230218164333354](https://raw.githubusercontent.com/shiyin-li/pic/master/img/202302191551276.png)

![image-20230218164444976](C:/Users/Administrator/AppData/Roaming/Typora/typora-user-images/image-20230218164444976.png)

#### 2.以下开始错误示范

项目里面套项目

![image-20230218164509956](https://raw.githubusercontent.com/shiyin-li/pic/master/img/202302191551159.png)

模块里面套模块

![image-20230218164707600](https://raw.githubusercontent.com/shiyin-li/pic/master/img/202302191551787.png)

![image-20230218164722789](https://raw.githubusercontent.com/shiyin-li/pic/master/img/202302191551070.png)

![image-20230218164944359](https://raw.githubusercontent.com/shiyin-li/pic/master/img/202302191551172.png)

### 2.idea导入模块

![image-20230422173050962](../../assets/1.idea的项目创建流程 以及错误示范/image-20230422173050962.png)

#### 导入模块分两步

#### 先将模块复制进项目中

![image-20230422173214473](../../assets/1.idea的项目创建流程 以及错误示范/image-20230422173214473.png)

``注：.idea文件夹表示这是一个项目``

#### 再将模块导入

![image-20230422173332656](../../assets/1.idea的项目创建流程 以及错误示范/image-20230422173332656.png)

![image-20230422173418415](../../assets/1.idea的项目创建流程 以及错误示范/image-20230422173418415.png)

![image-20230422173451211](../../assets/1.idea的项目创建流程 以及错误示范/image-20230422173451211.png)

![image-20230422173520416](../../assets/1.idea的项目创建流程 以及错误示范/image-20230422173520416.png)



### 3.static关键字

#### 回顾

![image-20230422174203208](../../assets/1.idea的项目创建流程 以及错误示范/image-20230422174203208.png)

#### static 共享 类名调用好

![image-20230422174418128](../../assets/1.idea的项目创建流程 以及错误示范/image-20230422174418128.png)

#### static修饰成员变量

![image-20230422174615784](../../assets/1.idea的项目创建流程 以及错误示范/image-20230422174615784.png)

![image-20230422175537348](../../assets/1.idea的项目创建流程 以及错误示范/image-20230422175537348.png)

#### static修饰成员方法

**同一个类中，静态方法只能调用静态方法或者静态变量**

![image-20230422175804367](../../assets/1.idea的项目创建流程 以及错误示范/image-20230422175804367.png)

![image-20230422180111111](../../assets/1.idea的项目创建流程 以及错误示范/image-20230422180111111.png)

#### 案例

![image-20230422180514314](../../assets/1.idea的项目创建流程 以及错误示范/image-20230422180514314.png)

![image-20230422181022081](../../assets/1.idea的项目创建流程 以及错误示范/image-20230422181022081.png)

### 4.继承

![image-20230422182054183](../../assets/1.idea的项目创建流程 以及错误示范/image-20230422182054183.png)

#### 问题 

![image-20230422182141008](../../assets/1.idea的项目创建流程 以及错误示范/image-20230422182141008.png)

#### 继承

![image-20230422182925006](../../assets/1.idea的项目创建流程 以及错误示范/image-20230422182925006.png)

![image-20230422185832126](../../assets/1.idea的项目创建流程 以及错误示范/image-20230422185832126.png)

#### 子类继承的内存图

![image-20230422190834429](../../assets/1.idea的项目创建流程 以及错误示范/image-20230422190834429.png)

``注：几个new就几个对象``

#### 单继承

![image-20230422190946858](../../assets/1.idea的项目创建流程 以及错误示范/image-20230422190946858.png)

#### java可以多继承

![image-20230422191008903](../../assets/1.idea的项目创建流程 以及错误示范/image-20230422191008903.png)

#### 变量 方法 访问都是 就近原则访问

![](../../assets/1.idea的项目创建流程 以及错误示范/image-20230422191522770.png)

this super关键字

![image-20230422191605492](../../assets/1.idea的项目创建流程 以及错误示范/image-20230422191605492.png)

#### 方法重写 子类对父类的方法重新写一遍

孩子比爹强

![image-20230422191953919](../../assets/1.idea的项目创建流程 以及错误示范/image-20230422191953919.png)

![image-20230422192444390](../../assets/1.idea的项目创建流程 以及错误示范/image-20230422192444390.png)

![image-20230422192555876](../../assets/1.idea的项目创建流程 以及错误示范/image-20230422192555876.png)

#### 重载 在一个类中



#### 子类调用构造器

![image-20230422192942052](../../assets/1.idea的项目创建流程 以及错误示范/image-20230422192942052.png)

![image-20230422193007609](../../assets/1.idea的项目创建流程 以及错误示范/image-20230422193007609.png)

#### this调用本类构造器

![image-20230427144509465](../../assets/1.idea的项目创建流程 以及错误示范/image-20230427144509465.png)

#### this和super关键子对比

![image-20230427144750847](../../assets/1.idea的项目创建流程 以及错误示范/image-20230427144750847.png)

### 6.抽象类

![image-20230427150310535](../../assets/1.idea的项目创建流程 以及错误示范/image-20230427150310535.png)

#### 抽象方法

![image-20230427151248345](../../assets/1.idea的项目创建流程 以及错误示范/image-20230427151248345.png)

![image-20230427152552256](../../assets/1.idea的项目创建流程 以及错误示范/image-20230427152552256.png)

#### **设计模式（模板方法模式）

![image-20230427152735985](../../assets/1.idea的项目创建流程 以及错误示范/image-20230427152735985.png)

![image-20230427154113913](../../assets/1.idea的项目创建流程 以及错误示范/image-20230427154113913.png)