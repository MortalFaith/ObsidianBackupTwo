***encoder***
![[Pasted image 20240108221248.png]]
**解释**
1.1residual架构：output的是S-a的输出加上输入的向量
1.2Layer Norm：对一个向量的不同的dimension计算出mean和standard deviation，并以此进行处理
**流程**
S-a通过r架构得到的输出被norm之后丢到Fully Connected Network里去，再按r架构得到输出、norm，最后得到结果

