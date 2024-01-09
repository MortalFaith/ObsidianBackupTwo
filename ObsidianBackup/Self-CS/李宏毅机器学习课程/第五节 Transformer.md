***encoder***
![[Pasted image 20240108221248.png]]
**解释**
1.1residual架构：output的是S-a的输出加上输入的向量
1.2Layer Norm：对一个向量的不同的dimension计算出mean和standard deviation，并以此进行处理
**流程**
S-a通过r架构得到的输出被norm之后丢到Fully Connected Network里去，再按r架构得到输出、norm，最后得到结果

按transformer的图例来解释：
![[Pasted image 20240108221819.png]]
input先加上位置信息，然后经过上面的流程（其中的S-a在这里被特定成了Multi-Head Attention）
BERT就是transformer的encoder
实际上，更换原始transformer的encoder中的顺序可能效果更好：
![[Pasted image 20240108222120.png]]
***Decoder(autoregressize)***
![[Pasted image 20240109085622.png]]
首先需要输入一个开始信号begin，然后Decoder会输出一个向量，其大小为供机器输出的所有可能字符（串）的数量，同时输出前会做softmax，因此得到的向量里是distribution（总和为1）
![[Pasted image 20240109085855.png]]
最终的结果是输出的向量中得分最高的一个字符（串），然后这个结果作为输入再过一次decoder，如此反复。
***Masked S-a***
![[Pasted image 20240109090219.png]]
在计算当前位置（a<sup>2</sup>）时，只考虑左边的向量
（a<sup>1</sup>）
***如何结束***
![[Pasted image 20240109090919.png]]
设置可供机器输出的End，标志着生成结束，从而使Transformer自己觉得输出长度。
***encoder和decoder之间的衔接***
![[Pasted image 20240109091358.png]]
将decoder的MS-a乘上矩阵得到的q与Encoder中得到的k、v进行计算得到v，最后丢入Fully Connected Network里，ye
