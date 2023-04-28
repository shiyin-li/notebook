## PageRank

#### 三种算法

![image-20230414092635597](../../assets/8子豪PageRank/image-20230414092635597.png)

![image-20230414094052566](../../assets/8子豪PageRank/image-20230414094052566.png)

![image-20230414092804863](../../assets/8子豪PageRank/image-20230414092804863.png)

### 五个角度理解pagerank

**默认每个网页的初连接的PR是一样的**

**1.前三个都是以结点的重要度/出度求和得到某个节点的重要度(PR)**

2.

![image-20230414092842247](../../assets/8子豪PageRank/image-20230414092842247.png)

#### 线性方程组

**高斯消元法**

![image-20230414093209789](../../assets/8子豪PageRank/image-20230414093209789.png)

![image-20230414093735696](../../assets/8子豪PageRank/image-20230414093735696.png)

``1.B->D 是指D网页被B节点引用``

``2.A的iteration1 PR(A)=1/4/3=1/12 只有C引用了A 并且C有三条出去的线，即C被引用了三次``

#### 2.迭代左乘M矩阵

![image-20230414094508121](../../assets/8子豪PageRank/image-20230414094508121.png)

![image-20230414094857870](../../assets/8子豪PageRank/image-20230414094857870.png)

![image-20230414095028587](../../assets/8子豪PageRank/image-20230414095028587.png)

![image-20230414095104714](../../assets/8子豪PageRank/image-20230414095104714.png)

#### 矩阵的特征向量

![image-20230414095134978](../../assets/8子豪PageRank/image-20230414095134978.png)

![image-20230414095656316](../../assets/8子豪PageRank/image-20230414095656316.png)

![image-20230414095816584](../../assets/8子豪PageRank/image-20230414095816584.png)

![image-20230414095832923](../../assets/8子豪PageRank/image-20230414095832923.png)

#### 随机游走

**随机游走计数求和再归一化**

![image-20230414100204043](../../assets/8子豪PageRank/image-20230414100204043.png)

![image-20230414100649244](../../assets/8子豪PageRank/image-20230414100649244.png)

``每个网页的出连接是一样的 eg：i1有三条出连接，每条的出连接的PR都等于PR/3``

![image-20230414101030298](../../assets/8子豪PageRank/image-20230414101030298.png)

#### 马尔科夫链

状态转移链 也是概率

### 求解PageRank

![image-20230414101623364](../../assets/8子豪PageRank/image-20230414101623364.png)

**模拟随机游走消耗计算机资源 不推荐**

![image-20230414101804275](../../assets/8子豪PageRank/image-20230414101804275.png)

**L1范数收敛到一个范围**

![image-20230414102010960](../../assets/8子豪PageRank/image-20230414102010960.png)

##### example：

![image-20230414102054306](../../assets/8子豪PageRank/image-20230414102054306.png)

### 敛散性分析

![image-20230414102129864](../../assets/8子豪PageRank/image-20230414102129864.png)

#### 不是这两种马尔科夫链（reducible可减少的 和periodic周期的）就可以收敛

![image-20230414102311814](../../assets/8子豪PageRank/image-20230414102311814.png)

#### 有多个连通域是属于这两种马尔科夫链的

![image-20230414103012244](../../assets/8子豪PageRank/image-20230414103012244.png)

### 对于奇葩的连接结点是否能得到我们想要的重要度？



![image-20230414102532255](../../assets/8子豪PageRank/image-20230414102532255.png)

#### 死胡同 （dead end）

![image-20230414102830224](../../assets/8子豪PageRank/image-20230414102830224.png)

**solution：让你100%被传走**

![image-20230414103355641](../../assets/8子豪PageRank/image-20230414103355641.png)

#### 仅指向自己（spider trap）

![image-20230414102809221](../../assets/8子豪PageRank/image-20230414102809221.png)

**solution：有一定概率被传走 不让你一直在抖音**

![image-20230414103123438](../../assets/8子豪PageRank/image-20230414103123438.png)



#### 数学上的证明

![image-20230414103703242](../../assets/8子豪PageRank/image-20230414103703242.png)

![image-20230414103753261](../../assets/8子豪PageRank/image-20230414103753261.png)

![image-20230414103849366](../../assets/8子豪PageRank/image-20230414103849366.png)

### example：

![image-20230414104024559](../../assets/8子豪PageRank/image-20230414104024559.png)

![image-20230414104318275](../../assets/8子豪PageRank/image-20230414104318275.png)

1.不能自己刷高 得需要大佬引用你

![image-20230414104455748](../../assets/8子豪PageRank/image-20230414104455748.png)

**并行计算PR**

![image-20230414104521847](../../assets/8子豪PageRank/image-20230414104521847.png)

### PageRank的变种

#### 用于推荐系统

![image-20230414104647100](../../assets/8子豪PageRank/image-20230414104647100.png)

``二部图``

![image-20230414104735660](../../assets/8子豪PageRank/image-20230414104735660.png)

![image-20230414104832554](../../assets/8子豪PageRank/image-20230414104832554.png)

![image-20230414104905201](../../assets/8子豪PageRank/image-20230414104905201.png)

![image-20230414104921381](../../assets/8子豪PageRank/image-20230414104921381.png)

![image-20230414104944960](../../assets/8子豪PageRank/image-20230414104944960.png)

![image-20230414105027899](../../assets/8子豪PageRank/image-20230414105027899.png)

![image-20230414105055564](../../assets/8子豪PageRank/image-20230414105055564.png)

![image-20230414105110709](../../assets/8子豪PageRank/image-20230414105110709.png)

![image-20230414105755930](../../assets/8子豪PageRank/image-20230414105755930.png)

![image-20230414105901940](../../assets/8子豪PageRank/image-20230414105901940.png)

### 总结

![image-20230414105929069](../../assets/8子豪PageRank/image-20230414105929069.png)

![image-20230414105956600](../../assets/8子豪PageRank/image-20230414105956600.png)

PageRank、Personalized PageRank和Random Walk with Restart都是用于计算节点在图中的重要性的算法，它们的主要区别如下：

1. PageRank是一种无偏向性的算法，用于计算图中所有节点的重要性。PageRank假设所有节点的初始重要性相等，并在迭代计算中考虑节点间的连接关系，逐步更新节点的重要性得分。最终得分可以用于比较不同节点的重要性。
2. Personalized PageRank是一种有偏向性的算法，用于计算与给定节点相关的其他节点的重要性。Personalized PageRank将给定节点作为起点，计算与其相关的节点的重要性。这种算法通常用于推荐系统中，以计算用户与其他用户或物品之间的相似性和关联度。
3. Random Walk with Restart也是一种有偏向性的算法，用于计算与给定节点相关的其他节点的重要性。与Personalized PageRank不同的是，Random Walk with Restart将概率随机游走的方式作为计算节点重要性的依据。具体来说，在每一次迭代中，节点有一定概率停留在当前节点，有一定概率按照连接关系随机移动到其他节点，同时还有一定概率重新回到给定节点。最终得分可以用于比较与给定节点相关的其他节点的重要性。

需要注意的是，这三种算法都是基于图的分析方法，它们的计算效率和精度会受到图的大小、结构和稀疏性等因素的影响。在具体应用时，需要根据实际情况选择合适的算法，并结合其他算法和技术进行综合分析和处理。