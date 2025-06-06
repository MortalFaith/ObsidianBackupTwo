## 第一章
### 1.2.1 编译的各个阶段 P2
- ![[编译原理-20250601154234928.heic|200]]
- ==【w疑似简答】==**五**个阶段：**词法分析-语法分析-中间代码生成-代码优化-目标代码生成**
### 编译程序&解释程序
- ![[编译原理lyc补-20250602210830669.png|800]]


## 第二章
### 程序设计语言分为两个部分
- 语法：一组规则
- 语义：
	- 静态语义：确定哪些语法合适
	- 动态语义：表明程序要做些什么
	- 文法是阐明语义的工具
### 2.2 符号串
- 由符号组成的任何有穷序列
- 长度记做$|x|$
- $\{a,b\} \cdot \{0,1\}=\left \{  aa,a1,b0,b1\right \}$
- $a^0=\varepsilon$
- $a^n = aa^{n-1} = a^{n-1}a$，故$a = a\varepsilon=\varepsilon a$
- $A=\left \{ a,b \right \}$时，$A^2=\left \{ aa,ab,ba,bb \right \}$
- $A^+=A^1\cup A^2\cup A^3\cdots \cup A^n$
- $A^*=A^0\cup A^+$
- ==多个$\varepsilon$==
### 文法里的两个概念 P22
- 文法定义为四元组：
	- VN非终结符
	- VT终结符（*字母表*）
	- P产生式
	- S开始符/识别符
	- **VN交VT为空集**
- *文法是做什么的：文法是一套形式化系统（规则），这套系统用来定义字符串的集合（语言）*
	- ==【选择】==给正规式，问文法所要识别的语言是什么
	- ==【判断】==给你文法和正规式，让你判别是不是一致的
### 推导/规约顺序
- 推导$\Rightarrow$，规约$\Leftarrow$
- 最左（最右）推导（**规范推导**）：
	- 如果在推导的任何一步a$\Rightarrow$b，其中a ∈V* ，都是对a中的最左（最右）非终结符进行替换，则称这种推导为最左（最右）推导
- **推导中间过程是句型**，若**只含有终结符(最后一步)，则为句子**
	- 句子一定是句型
### 语言：
- 是文法的一切句子的集合
### 文法的类型（**后者包含前者**）：
- 0型：至少含有1个非终结符
- 1型/上下文有关：$\alpha \to \beta ，\left |  \alpha  \right |  \le   \left |  \beta \right |，S\to \varepsilon$除外
- 2型/上下文无关：$\alpha \in V_N$，左边只有一个
- 3型/正规文法：$S\to aB | a$，终结符开头
	- $A\to bAA$不是3型
### 短语、直接短语和句柄
- ![[编译原理lyc补-20250602211102817.png|700]]

## 第三章
### 正规式与正规文法
- 正规式到正规文法：![[编译原理lyc补-20250602213307916.png|800]]
- 正规文法到正规式：![[编译原理lyc补-20250602212949347.png|800]]
### 自动机
- 有穷自动机能准确识别正规集：
	- 一个a只能到1个节点，而NFA可到多个
	- f(k,a)唯一确定下个状态
- 确定的和不确定的有穷自动机是等价的P34 ：
	- **DFA（包括字母）是一种NFA（包括字母和空串）**
	- NFA初态不唯一
- 有穷自动机中的**Z（终态集）中元素个数：可能是$\phi$（什么符号都没有），1个，n个**

## 第四章
### 自顶向下和自底向上
- LR方法是自底向上方法
### 提公因子 P77 // 消除左递归 P80
- 这两点是所有语法分析都会有的？
	- **错误！是自顶向下方法独有的问题，只在LL(1)分析中需要处理**

## 第五章
### ==【选择】==文法或句子规约的值是什么
- **按规约方法计算！**
- 表达式求值，给你一个表达式的文法，让你按照这个式子去求
### LR分析——==【选择】==判断移进or规约or接受
- 移进：$A\to \alpha . a\beta$
- 规约：$B\to \alpha .$
- 接受：$S'\to S .$
### 分析表 P136
- *期待看下成神的题来理解吧*
- LR(0)
	- 向前看，只和状态有关
	- **一行r只能一样**
### 二异文法的作用
- **LR如果程序出错了就会发现错误（表空）**，*这里指能抛出报错，而非发现具体错误的地方*
### ==【填空】==语法翻译制导包括：
1. **继承**
2. **综合性**
### 语法优化规则 P270~274
- 什么是局部优化
- ==【选择】==给代码，判断能做哪些优化
	- 基本的优化方法，给你一段程序怎么优化


## 老佛爷考试题型（黄）
### 一、填空题
- 5题10空，每空1分（送分）

### 二、（单项）选择题
- 10题10分（计算，有难度）
- 第一道是中间代码生成
- 第三题文法，语言定义：给你一个文法，让你识别她的语言，ABCD 哪个语言是文法语言
- 第五、第六、第七LR文法分析，归约
- 两道代码优化
- 两道词法分析
- 自下而上
- 下面的程序可以进行哪些优化？

### 三、判断题
- 10题10分
- 一道词法分析器
- 一道语法分析器
- 一道文法（给正规式）
- 第三题 错 涉及消除左递归，LR不需要消除左递归 。语法分析不一定要消除左递归 
- 第四题 错 编译器指定出错位置是对的还是错的 ==**（lyc存疑）**==
- 第五题 LR
- 第六题 拉链回填
- 第七题 存储分配
- 第八、九、十题 优化

### 四、计算题

词法分析
4，10，8，共22分

给出一句话，语言描述，让你自己写正规式
NFA DFA 最小化 构建和DFA等价的正规文法

语法分析
10，5，共15分

用自上而下分析

根据这个构造LR分析表，再利用构造分析表分析一段输入的字符串

### 五、计算题
共23分

LR文法：
给出文法，构造DFA，画状态转换图（7），并构造LR(0)分析表（3）：规约那一行怎么填的，有文字有说明
*构造SLR(1)分析表（5）

代码生成（这一题待定）
属性(action)文法，问到了哪一型文法
是不是文法的一个句型

### 六、综合题
共10分

代码优化
基本块优化
基本块的 DAG 表示及其应用



