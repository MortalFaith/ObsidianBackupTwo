 机器学习=找一个函数
 找的函数不同有不同的任务：
 regression：找一个输出数值的函数
 classification：从设定好的类别中选出需要的选项
 structured learning：创造有结构的东西

 1.写出一个带有未知数的函数
 like y = b + wx1   --Model
 需要一些对问题本质的了解(domain knowledge)
 2.定义损失(Loss)
 Loss是一个函数，输入为b和w，表示值的好坏
 *Label指正确的数值*
 L = 所有的误差e的平均值
 ![[Pasted image 20230412155421.png]]
 3.最佳化：找到最好的w和b——w\*和b\*
 方法：Gradient Descent
 3.1假设只有一个未知数w
 随机选一个w0，计算L对w的微分，向L低的方向移动
 移动距离=![[Pasted image 20230412160451.png]]
 