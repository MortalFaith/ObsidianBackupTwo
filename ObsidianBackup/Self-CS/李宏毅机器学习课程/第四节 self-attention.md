1.把向量作为输入
（[一文读懂Embedding的概念，以及它和深度学习的关系 - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/164502624)）
1.1one-hot编码
1.2embedding
2.输出
2.1输出数量=输入数量（给每个单词表词性）
2.2只输出一个（判断一句话的情绪）
2.3机器自己决定要输出多少个（Seq2seq）
3.Sequence Labeling（2.1类型）
3.1考虑前后的词汇（window）
![[Pasted image 20240102082213.png]]
但是容易引发window过大/over-fitting的问题
3.2self-attention
