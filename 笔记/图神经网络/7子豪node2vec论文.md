### Node2Vec(有偏随机游走)

**解决了deep walk仅能反应相邻结点的(或者相近节点的信息)，不能反映距离较远的功能相似的结点**

![image-20230413101837055](../../assets/7子豪node2vec论文/image-20230413101837055.png)

``1.当前v结点 有1/q的概率（权重）走向X2X3，有1/p的概率（权重）走向上一个节点t，还有1的概率（权重）走到X1（X1和t的距离等于v到t的距离 不走远也不走近）``

``2.pq取值范围不是[0,1]``



**调节pq的值 使其有偏随机游走 远行dfs  返回bfs** 

![image-20230413102720261](../../assets/7子豪node2vec论文/image-20230413102720261.png)

![image-20230413103614679](../../assets/7子豪node2vec论文/image-20230413103614679.png)

#### 2阶随机游走

- 不仅取决于当前结点还取决于上一个节点（node2vec的random walk）

- 只取决于当前的结点（deep walk中的random walk）

![image-20230413103143975](../../assets/7子豪node2vec论文/image-20230413103143975.png)

![image-20230413103351004](../../assets/7子豪node2vec论文/image-20230413103351004.png)

#### 伪代码

![image-20230413103812018](../../assets/7子豪node2vec论文/image-20230413103812018.png)

#### 和deep walk对比

![image-20230413103938000](../../assets/7子豪node2vec论文/image-20230413103938000.png)

#### sumarry

![image-20230413105232622](../../assets/7子豪node2vec论文/image-20230413105232622.png)

![image-20230413105428618](../../assets/7子豪node2vec论文/image-20230413105428618.png)

![image-20230413105453709](../../assets/7子豪node2vec论文/image-20230413105453709.png)

#### 传统的机器学习 数据重要的三个特征

![image-20230413111459779](../../assets/7子豪node2vec论文/image-20230413111459779.png)

### node2vec

![image-20230413164054722](../../assets/7子豪node2vec论文/image-20230413164054722.png)

![image-20230413164232626](../../assets/7子豪node2vec论文/image-20230413164232626.png)

#### link embedding

![image-20230413171024546](../../assets/7子豪node2vec论文/image-20230413171024546.png)

#### 正负样本的定义

正样本使用图的50% 删除这50%后图仍然保持连通性

负样本使用图中不相连的点

#### link prediction

1. 先得到node 的embedding
2. 用node embedding得到link embedding
3. 使用link embedding 进行二分类

启发式方法（并不限于以下四种）（不科学）将node embedding转换为link embedding

N（u）u结点附近的N个结点

![image-20230413173927969](../../assets/7子豪node2vec论文/image-20230413173927969.png)
