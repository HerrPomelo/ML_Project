[deep learning book ](http://www.deeplearningbook.org/contents/rnn.html)
# chapter 10 
# Sequence Modeling: Recurrent and Recursive Nets

循环神经网络，RNN，是用来处理序列数据的网络之一。卷积网络CNN是用来处理网格一样的数据，循环网络专门用来处理序列数据比如 $$x^{1}..x^{T}$$ 。就像CNN可以很方便的缩放长宽很大的图像，也可以处理长宽变化的图像，RNN可以缩放长度很长的**序列数据**，大多数RNN也可以处理可变长度的序列数据。

 从多层网络到循环网络，我们可以利用机器学习和统计模型中观点：在网络的不同部分**共享参数**。参数共享才能将模型应用到不同长度的数据序列中然后进行泛化。如果我们对于不同的时间索引有不同的参数，那么我们就不能在训练过程中对未知长度的序列进行泛化，也不能在不同的时间位置和不同的序列长度之间共享统计强度。当一个特殊的信息可以出现在同一序列的不同位置时，参数共享就更加重要了。比如，“I went to Nepal in 2009” 和 “In 2009,I went to Nepal.‘如果想用机器学习的方法读取序列并提取出时间，通常是先将2009看作一个信息片段，不管他的位置在哪。假设我们训练了一个前向网络可以处理固定长度的句子。传统的全连接网络对于每个输入特征都有独立的参数，所以在句子的每个位置都要学习不同的语言规则。但是在RNN中，在不同的时间片段中共享共同的参数。

近几年有把卷积神经网络应用与一维时间序列上，这种卷积的方法是时间延迟神经网络的基础。这种卷积的方法也能实现浅显的参数共享，当每个输出单元是少量输入数据临近单元的函数时，输出单元是序列数据。这种参数共享在每个时间段都应用同一个卷积核时有明显的效果。
循环神经网络的参数共享是另一种方式。RNN中，每个输出单元是先前输出单元的函数，每个输出单元都使用与先前输出单元相同的更新规则产生。这种循环的结构使得RNN中的参数共享通过一个非常深的计算图谱实现。

简便叙述下RNN。将RNN看作是由向量$$x^{t}$$组成的序列，其中t为从1到$$ \iota $$时间索引.RNN通常是作用于这样一个序列的一小部分，每一部分的序列长度也不同。

本章引入计算图谱的概念来说明循环的概念。这种循环阐述了当前变量在下一个时间点对它自身的影响。本章接下来会通过不同的方式来描述RNN网络的构建、训练和使用。






















