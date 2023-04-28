### 学习路线

![image-20230411171550522](../../assets/6子豪讲deepwalk论文/image-20230411171550522.png)

### word2vec （node2vec的父亲）

#### 两种方法构建自监督任务 将所有词映射到d维向量（低维稠密连续） 这些d维向量能较好的表现这些词的原本关系

![image-20230411174232640](../../assets/6子豪讲deepwalk论文/image-20230411174232640.png)

##### skip-gram 自监督学习

![image-20230411174625959](../../assets/6子豪讲deepwalk论文/image-20230411174625959.png)

**在deepwalk中随机游走构造的序列  相当于word2vec中的句子**

**随机游走相当于“管中窥豹“ 用部分的序列来表示图的信息 当序列足够多时就可以完全表示图的信息（随机游走的哲学）**

![image-20230411174841969](../../assets/6子豪讲deepwalk论文/image-20230411174841969.png)

**相邻结点应该具有相似的embedding 类比 word2vec中的相邻单次具有相似的embedding**

![image-20230411175145887](../../assets/6子豪讲deepwalk论文/image-20230411175145887.png)

### Deep Walk流程

![image-20230412102520262](../../assets/6子豪讲deepwalk论文/image-20230412102520262.png)

#### 伪代码deep walk 分两步：1.随机游走生成器2.迭代优化

![image-20230412165627505](../../assets/6子豪讲deepwalk论文/image-20230412165627505.png)

##### skip-gram伪代码

![image-20230412170135170](../../assets/6子豪讲deepwalk论文/image-20230412170135170.png)

**Pr（）咋得来的：使用中间节点的embedding和周围节点的embedding做数量积得来**

![image-20230412170628842](../../assets/6子豪讲deepwalk论文/image-20230412170628842.png)

##### 分层softmax(加速运算) word2vec也用到了

本来是8分类 现在是3个二分类  类似于霍夫曼树

![image-20230412171735959](../../assets/6子豪讲deepwalk论文/image-20230412171735959.png)

![image-20230412171933210](../../assets/6子豪讲deepwalk论文/image-20230412171933210.png)

##### skip-gram窗口

![image-20230412172152434](../../assets/6子豪讲deepwalk论文/image-20230412172152434.png)

#### deep walk 两套权重

1.是随机游走后使用**node2vec**得到D维矩阵(将节点映射成为d维向量)

2.是skip-gram中的**分层softmax**的二分类器

![image-20230412172307562](../../assets/6子豪讲deepwalk论文/image-20230412172307562.png)

#### deep walk 优点

1.可以多线程跑

2.将结点属性和连接属性分开 deep walk得到的d维向量是只有连接信息

3.未知全貌 盲人摸象 管中窥豹 但是效果还挺好（使用3%数据的model可以超过别的使用10%数据model）

![image-20230412173142042](../../assets/6子豪讲deepwalk论文/image-20230412173142042.png)
