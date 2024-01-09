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
首先需要输入一个开始信号（
