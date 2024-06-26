## 考试分布
1. 789各一大题，共30分
2. B树或平衡二叉树

## 第六章
### 树的算法作业
1. 用孩子兄弟表示法表示树并求树的高度。
- 孩子兄弟表示法 p195：链表中一个结点有两个指针域分别指向该结点的第一个孩子结点和下一个兄弟结点。![[Pasted image 20240523164335.png]]
- 一个节点的高度即为所有孩子的最高高度加一
2. 用孩子兄弟表示法表示树并求树的度。
- 一个节点的度为当前节点的度数与孩子的最大度数中较大的那个
3. 并查集合并时高度高的树的根做为新的根。
- 并查集 p201：![[Pasted image 20240523165930.png]]
- 再按节点个数的基础上，将权修改为高度（负数）
### 树与二叉树的转换
- 树中结点p的第一个孩子结点在二叉树中是结点p的左孩子结点，原树中结点p的右兄弟结点在二叉树中是结点p的右孩子结点。
- 一棵树采用孩子一兄弟表示法所建立的存储结构与它所对应的二叉树的二叉链表存储结构是完全相同的，只是两个指针域的名称和解释不同而己。
### 等价类作业/并查集实现
- 见上
## 第七章
### 概念
1. 若路径上各顶点均不相同，则称这路径为简单路径。
2. 在有向图中，若对于顶点 vi 。和vj，存在一条从vi 、到vj和从vj到vi的路径，则称顶点vi和顶点vj是强连通。如果有 向图中任意两个顶点都是强连通的，则称此有向图为强连通图。
### 有向图和无向图的操作不同
1. 改边
### （逆）邻接表的结构
1. ![[Pasted image 20240523202431.png]]
2. 表Vex，节点Arc，看清名字
### 最小生成树 p236
1. 克鲁斯卡尔算法：
- 每一步向F中加入 一条边（v , u )，它应是所依附的两个顶点v和u分别在森林F的两棵不同的树上的所 边中具有最小权值的边。反复n-1次
- 将所有边建最小堆，如果两个顶点在同一集合则跳过，不在则合并边数+1![[Pasted image 20240523204012.png]]
- 适用于稀疏的（顶点个数较多而边数较少）连通网络。
2. 普里姆算法：
- 每一步从一个顶点在u中，而另一个顶点在v-u中的各条边当中选择权值最小的边（u , v )，把顶点v加入到集合u中，边（v , u）加入到集合TE中。重复n-1次，即所有点都在u中。
- Iowweight中存放顶 点v到U中的各顶点的边上的当前最小权值（=0表示v在U中 ) ; nearvertex记录顶 点v到U中具有最小权值的那条边的另一个邻接顶点u ( nearvertex＝-1表示该顶点v为开始顶点）。
- 选点、更新边![[Pasted image 20240523203938.png]]
### 最短路径及应用条件 p243
1. 弧上权值为非负情形：迪杰斯特拉：求出从源点v 到其余各顶点中长度最短的一条，然后参照它 求出长度次短的一条最短路径，依此类推
- 辅助数组：![[Pasted image 20240523234035.png]]
2. 权值可能为负值+要求图中不能有路径长度为负值的回路：贝尔曼—福特：![[Pasted image 20240524000309.png]]
- 每一次需要先在辅助数组中操作，确保当前轮次的所有计算都是基于上一轮的距离值
4. 所有顶点之间的最短路径+允许图中有带负权值的弧，但不允许有路径长度为负值的回路：弗洛伊德：逐步试着在原直接路径中增加中间顶点，若加入中间点后路径变短，则修改之；否则，维持原值。![[Pasted image 20240524000925.png]]
### 活动网络 p251
1. AOV：拓扑排序
- 建立入度为零的顶点栈，空则结束，否则栈顶出栈，删除所有从其发出的弧，并将终点弧度-1，为0则入栈
2. AOE：先算每个顶点V的Ve和Vl，再计算每个活动a的e和l，相等即为关键路径
## 第八章
### 省流：
### 顺序查找：
- 监视哨：将目标元素作为一个哨兵放置在数组末尾，使得在查找过程中不需要每次都检查是否到达数组末尾
- ASL-SS：$\frac{1}{n} \times \sum_{i=1}^{n} (n+1-i)    = \frac{n+1}{2}$ 
- ASL-FA：$n+1$
### 折半查找：
- ASL-SS：$\frac{1}{n} \times (1\times 1+2\times 2 + 4\times 3+ \dots )$
- ？
### 二叉排序树：
- 中序遍历有序
- 删除节点 p279：
	- 只有右/只有左：用右孩子/左孩子代替
	- 左右都有：用左子树中最大的/右子树中最小的替代
- 只有一列时退化为顺序查找
### 平衡二叉树 p281：
1. 旋转
- LL：结点B代替原来结点A的位置，结点B原来的右孩子作为结点A的左孩子：![[Pasted image 20240525143845.png]]
- RR：结点B代替原来结点A的位置，结点B原来的左 孩子成为结点A的右孩子：![[Pasted image 20240525143915.png]]
- LR：![[c76e038bbc41ba616bf0d7a77ec8c58.jpg]]
- RL：![[Pasted image 20240525144929.png]]
2. 右子树的高度减去左子树的高度=平衡因子
3. 插入：
- 记下从根结点到插入位置的路径上离插入位 置最近的且平衡因子绝对值为1的结点a
- 对于从a结点到x结点的路径上的每一个结点（不包括x )，在左则减，在右则加
- a平衡因子为2则开转
- 有几个点的平衡因子错了阿弥诺斯![[Pasted image 20240525145744.png]]
4. 删除：
- 删除节点：
	- 左右都有：找前驱或后继替代
	- 只有一个孩子：用孩子替代；没有孩子直接删除
- 从删除结点的双亲到根结点的路径上的每一个结点p，当布尔变量isshorter的 值为true时，根据以下三种不同的情况继续步骤，直到布尔变量isshorter的值为false
	- 当结点p的平衡因子为0，如果它的左子树或右子树被缩短（i sshorter 的值为true )，则它的平衡因子改为1或-1，由于此时以结点p为根的子树高度没有缩短， 所以置isshorter的值为false![[Pasted image 20240525151030.png]]
	- 结点p的平衡因子不为0：
		- 较高的子树被缩短，因此因子变为0。此时以结点p为根的子树高度被缩短，所以isshorter的值仍为true 。![[Pasted image 20240525151055.png]]
		- 较矮的子树被缩短，记结点p的较高子树的根结点为q：
			- 如果q的平衡因子为0，则只要执行一个单旋转，被处理子树的高度没有缩短，所以置isshorter的值为false。![[Pasted image 20240525151115.png]]
			- q的平衡因子与p的平衡因子的符号相同，则只要执行一个单旋转就可恢复 结点p的平衡。处理子树的高度被缩短，所以isshorter的值仍为true。![[Pasted image 20240525151328.png]]
			- p与q的平衡因子的符号相反，则需要执行一个双旋转来恢复平衡，先围绕q转、再围绕p转。处理子树的高度被缩短，所以isshorter的值仍为true。![[Pasted image 20240525151359.png]]
5. m阶B-树：
- 性质：
	- 树中每个结点至多有m棵子树
	- 若根结点不是叶子结点,则至少有两棵子树
	- 除根之外的所有非终端结点至少有$\lceil 2 / m\rceil$ 棵子树
- 插入：｛35 , 26 , 74 , 60 , 49 , 17 , 41 ,53}![[Pasted image 20240525154214.png]]
- 删除
	- 被删关键字所在叶结点同时又是根结点且删除前该结点中关键字个数$n\ge 2$，则直接删去
	- 若被删关键字所在叶结点不是根结点，且删除前该结点中关键字个数$n \ge \lceil m / 2\rceil$ , 则可直接删除：删除53![[Pasted image 20240525154829.png]]
	- 被删关键字所在叶结点删除前关键字个数$n = \lceil m / 2\rceil -1$：
		- 若这时与该结点相邻的左 （或右）兄弟结点的关键字个数$n \ge \lceil m / 2\rceil$：
			1. 将其双亲结点中大于（或小于）该被删关键字的所有关键字最小（或最大）的一个关键字ki。下移到被删关键字所在结点中。
			2. 将左（或右）兄弟结点中的最大（或最小）关键字上移到双亲结点的ki位置。
			3. 将左（或右）兄弟结点中的最右（或最左）子树指针删除，并将结点中的关键字个数减1 。
			- ![[Pasted image 20240525155545.png]]
			- 删78：![[Pasted image 20240525155608.png]]
		- 若这时与该结点相邻的 左、右兄弟结点中的关键字个数也都为$\lceil m / 2\rceil -1$：
			1. 将双亲结点中大于（或小于）该被删关键字的所有关键字中最小（或最大）的一 个关键字Ki下移到p结点中，将p和p的左（或右）兄弟结点合并。
			2. 修改p结点和其双亲结点关键字个数。
			3. 在合并结点的过程中，双亲结点中的关键字个数减少了1 。如果双亲是根且变空了就由p来当根，如果关键字个数减到$\lceil m / 2\rceil -2$就继续向上合并
6. B+树
- 性质：
	- 树中每个非叶结点最多有m棵子树。
	- 根结点至少有2棵子树。除根结点外，其它结点至少有$\lceil m / 2\rceil$棵子树；有n棵子树的结点中含有n个关键字，且按由小到大的顺序排列。
	- 所有的叶结点都处于同一层次上，包含了全部关键字及指向相应数据元素的指针，且叶结点本身按关键字从小到大顺序链接；
- 插入：当插入后结点中的子树棵数n > m时，需要将叶结点分裂为两个结点
- 删除：
	- 若在叶结点中删除一个关键字后，其关键字的个 数仍然不少于$\lceil m / 2\rceil$，这属于简单删除，其上层索引可以不改变。
	- 否则从兄弟借，再不行就合并，记得修改索引？
1. 