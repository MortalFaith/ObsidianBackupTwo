***1.把向量作为输入***
（[一文读懂Embedding的概念，以及它和深度学习的关系 - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/164502624)）
1.1one-hot编码
1.2embedding
***2.输出***
2.1输出数量=输入数量（给每个单词表词性）
2.2只输出一个（判断一句话的情绪）
2.3机器自己决定要输出多少个（Seq2seq）
***3.Sequence Labeling（2.1类型）***
3.1考虑前后的词汇（window）
![[Pasted image 20240102082213.png]]
但是容易引发window过大/over-fitting的问题
***3.2self-attention***
考虑整个sequence的内容，然后对每个输入向量输出新的向量，再丢入FC
可以多层堆叠
![[Pasted image 20240102082640.png]]
***3.3如何计算self-attention的一个输出a1***
3.3.1计算a1与其他向量的关联度α
![[Pasted image 20240102083331.png]]
方法有很多，这里采用Dot-product
对每个向量，计算和它自己以及其他向量的α$$q^{i}k^{j}=\alpha _{i,j}$$，再过一个Soft-max（公式在上方）                                            
![[Pasted image 20240102083656.png]]
再用一个新的W<sup>v</sup>乘上a<sup>1</sup>和α，最后求和得到b<sup>1</sup>
![[Pasted image 20240102085335.png]]![[Pasted image 20240102085941.png]]
接下来把计算过程矩阵化
q、k、v：
![[Pasted image 20240107193406.png]]
α：

![[Pasted image 20240107193457.png]]
最终可得：
![[Pasted image 20240107194256.png]]


