#### 前置视频课

![image-20230411085029322](../../assets/4子豪DeepWalk/image-20230411085029322.png)

#### 这门课的核心

![image-20230411085832798](../../assets/4子豪DeepWalk/image-20230411085832798.png)

#### 学习路线

![image-20230411090147819](../../assets/4子豪DeepWalk/image-20230411090147819.png)

### 图嵌入

#### 传统的机器学习

![image-20230411090943677](../../assets/4子豪DeepWalk/image-20230411090943677.png)

#### 图表示学习 自动学习特征

![image-20230411091035199](../../assets/4子豪DeepWalk/image-20230411091035199.png)

![image-20230411091341041](../../assets/4子豪DeepWalk/image-20230411091341041.png)

![image-20230411091651506](../../assets/4子豪DeepWalk/image-20230411091651506.png)

##### DeepWalk 将图嵌入到二维矩阵中

![image-20230411091823935](../../assets/4子豪DeepWalk/image-20230411091823935.png)

![image-20230411092056340](../../assets/4子豪DeepWalk/image-20230411092056340.png)

###### node的嵌入 （encode node）

![image-20230411092245866](../../assets/4子豪DeepWalk/image-20230411092245866.png)

##### 相似度可以自己定义

![image-20230411092755032](../../assets/4子豪DeepWalk/image-20230411092755032.png)

##### 一些相似度的定义 

![image-20230411095913615](../../assets/4子豪DeepWalk/image-20230411095913615.png)

![image-20230411100016786](../../assets/4子豪DeepWalk/image-20230411100016786.png)

![image-20230411100504436](../../assets/4子豪DeepWalk/image-20230411100504436.png)

##### 浅编码（shallow encoding） 使用手动写出来

相对应的是使用深度学习model的深编码  直接输入结点 得到d维向量

![image-20230411101045532](../../assets/4子豪DeepWalk/image-20230411101045532.png)

![image-20230411101310735](../../assets/4子豪DeepWalk/image-20230411101310735.png)

![image-20230411101533853](../../assets/4子豪DeepWalk/image-20230411101533853.png)

#### Random Walk

类比NLP

![image-20230411101802972](../../assets/4子豪DeepWalk/image-20230411101802972.png)

一些定义 Notation（*n.* 记号, 标记法）

SoftMax相当于归一化处理

![image-20230411102626565](../../assets/4子豪DeepWalk/image-20230411102626565.png)

![image-20230411102813929](../../assets/4子豪DeepWalk/image-20230411102813929.png)

![image-20230411104159726](../../assets/4子豪DeepWalk/image-20230411104159726.png)

![image-20230411104014349](../../assets/4子豪DeepWalk/image-20230411104014349.png)

![image-20230411104429035](../../assets/4子豪DeepWalk/image-20230411104429035.png)

极大似然估计

![[image-20230411104950335]()](../../assets/4子豪DeepWalk/image-20230411104950335.png)

类似交叉熵

![image-20230411110051822](../../assets/5子豪DeepWalk/image-20230411110051822.png)

![image-20230411110646610](../../assets/5子豪DeepWalk/image-20230411110646610.png)

##### 损失函数

时间复杂度O(n2)

![image-20230411110813021](../../assets/5子豪DeepWalk/image-20230411110813021.png)

#### 解决softmax难算的问题 

- 分层softmax
- 负采样

##### 介绍负采样

![image-20230411111355322](../../assets/5子豪DeepWalk/image-20230411111355322.png)

直接随机采k个结点（样本）

![image-20230411111724205](../../assets/5子豪DeepWalk/image-20230411111724205.png)

#### 优化的方法 （使用随机梯度下降来求最小损失）

- ![image-20230411112230426](../../assets/5子豪DeepWalk/image-20230411112230426.png)

- ![image-20230411112329231](../../assets/5子豪DeepWalk/image-20230411112329231.png)

- 相当于自己学的三种

​		批量梯度下降 速度慢 但是准

​		随机梯度下降 快  但不一定准 次数多也能达到准确？ 

​		小批量梯度下降  两者的折中 

![image-20230411112927418](../../assets/5子豪DeepWalk/image-20230411112927418.png)

#### 将以上步骤总结

![image-20230411113048991](../../assets/5子豪DeepWalk/image-20230411113048991.png)

以上随机游走是完全随机的 可不可以优化一下

![image-20230411113216224](../../assets/5子豪DeepWalk/image-20230411113216224.png)

### Node2Vec（随机游走（random walk）的优化）

#### idea 想法

![image-20230411113412398](../../assets/5子豪DeepWalk/image-20230411113412398.png)

![image-20230411113436038](../../assets/5子豪DeepWalk/image-20230411113436038.png)

#### 2阶的随机游走

所谓的2阶是指 记得自己是从那个结点过来的

![image-20230411151432480](../../assets/5子豪DeepWalk/image-20230411151432480.png)

![image-20230411151458553](../../assets/5子豪DeepWalk/image-20230411151458553.png)

![image-20230411151524058](../../assets/5子豪DeepWalk/image-20230411151524058.png)

![image-20230411152339864](../../assets/5子豪DeepWalk/image-20230411152339864.png)

#### node2vec的流程

![image-20230411152747572](../../assets/5子豪DeepWalk/image-20230411152747572.png)

#### 其他的随机游走的策略

![image-20230411152829407](../../assets/5子豪DeepWalk/image-20230411152829407.png)

#### summary（核心思想）

![image-20230411153129399](../../assets/5子豪DeepWalk/image-20230411153129399.png)

![image-20230411153223181](../../assets/5子豪DeepWalk/image-20230411153223181.png)

``1.Z矩阵也就是结点映射成为d维矩阵（d也就是z的行数）``

``2.Z矩阵也就是图嵌入和矩阵分解的结果``

### 邻接矩阵的分解得到Z矩阵

![image-20230411154259587](../../assets/5子豪DeepWalk/image-20230411154259587.png)

![image-20230411155434889](../../assets/5子豪DeepWalk/image-20230411155434889.png)

#### 随机游走 node2vec也可以做矩阵分解

太复杂

![image-20230411155707969](../../assets/5子豪DeepWalk/image-20230411155707969.png)

论文推导

![image-20230411155940246](../../assets/5子豪DeepWalk/image-20230411155940246.png)

### 矩阵分解的缺点（limitation）

#### 1.每次新加入一个节点就要全部调整(图的结构被改变了) 

![image-20230411160120848](../../assets/5子豪DeepWalk/image-20230411160120848.png)

#### 2.随机游走 不能够看出结构相似 只反映地理上相近

![image-20230411160459996](../../assets/5子豪DeepWalk/image-20230411160459996.png)

``解决：匿名随机游走(Anonymous Random walk) 或者 图神经网络(GNN)``

#### 3.仅利用了连接的信息 没有利用结点的属性信息

![image-20230411160850352](../../assets/5子豪DeepWalk/image-20230411160850352.png)

![image-20230411160918871](../../assets/5子豪DeepWalk/image-20230411160918871.png)

``GNN不仅考虑到了连接信息也考虑到了属性信息``

### summary 总结

**将图转换为矩阵 使用线性代数的方法或者矩阵运算很重要**

![image-20230411161054807](../../assets/5子豪DeepWalk/image-20230411161054807.png)

#### 讨论 问题 各自的优缺点

![image-20230411161225051](../../assets/5子豪DeepWalk/image-20230411161225051.png)

![image-20230411161352316](../../assets/5子豪DeepWalk/image-20230411161352316.png)

### 嵌入整张图(子图或者整张图)

![image-20230411161726211](../../assets/5子豪DeepWalk/image-20230411161726211.png)

#### approch1：对每一个结点d维向量求和

![image-20230411161743814](../../assets/5子豪DeepWalk/image-20230411161743814.png)

#### approch2：虚拟节点 此节点与图中每一个结点相连

![image-20230411162549577](../../assets/5子豪DeepWalk/image-20230411162549577.png)

#### approch3：匿名随机游走 认号不认人

![image-20230411162734451](../../assets/5子豪DeepWalk/image-20230411162734451.png)

![image-20230411162757343](../../assets/5子豪DeepWalk/image-20230411162757343.png)

![image-20230411162825742](../../assets/5子豪DeepWalk/image-20230411162825742.png)

![image-20230411163021380](../../assets/5子豪DeepWalk/image-20230411163021380.png)

![image-20230411163129926](../../assets/5子豪DeepWalk/image-20230411163129926.png)

​     ``数学公式``

#### 匿名随机游走的另一种策略

![image-20230411164059955](../../assets/5子豪DeepWalk/image-20230411164059955.png)

![image-20230411163930727](../../assets/5子豪DeepWalk/image-20230411163930727.png)

![image-20230411164423958](../../assets/5子豪DeepWalk/image-20230411164423958.png)

#### 为何要构建这个任务（全图WG  w1 w2 w3去预测w4）因为要构建一个子监督学习任务

![image-20230411164844976](../../assets/5子豪DeepWalk/image-20230411164844976.png)

``这是一个极大似然估计的自监督学习任务``

#### summary

![image-20230411165106208](../../assets/5子豪DeepWalk/image-20230411165106208.png)

### preview

![image-20230411165240452](../../assets/5子豪DeepWalk/image-20230411165240452.png)

``神经网络也是这么做的``

![image-20230411165357084](../../assets/5子豪DeepWalk/image-20230411165357084.png)

#### 这节学习的不需要人工特征 是自监督学习任务

![image-20230411165438533](../../assets/5子豪DeepWalk/image-20230411165438533.png)

#### 问题和论文

