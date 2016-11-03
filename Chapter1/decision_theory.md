在1.2节中我们看到，概率论是如何提供一个一致的数学框架来量化，计算不确定性。现在我们转而讨论决策论，它与概率论结合后，可以让我们在模式识别中遇到不确定的情况的时候，做出最优的决定。    

假设我们有输入向量$$ x $$和对应的目标向量$$ t $$，我们的目标是对新的输入$$ x $$预测目标变量$$ t $$。对于回归问题，$$ t $$是由连续变量组成的，而对于分类问题，$$ t $$由类别标签标识。联合概率分布$$ p(x, t) $$概括了这些变量的不确定性。从训练集中确定$$ p(x, t) $$是推断的一种。本书的大部分内容由解决这样的通常是比较困难的问题构成。然而在实际应用中，我们通常需要对$$ t $$的值做具体的预测，或更一般的，根据我们的理解$$ t
$$最可能的取值，采取具体的动作。这就是决策论的一个方面。    

举个医学诊断的例子，我们给病人拍了X光片，来诊断他是否得了癌症。在这种情形下，输入向量$$ x $$是X光片的像素的灰度值集合，输出变量$$ t $$表示病人患有癌症，记作类$$ C_1 $$或者不患癌症，记作类$$ C_2 $$。实际中，我们可能二元变量（如：$$ t = 0 $$来表示$$ C_1 $$类，$$ t = 1 $$来表示$$ C_2 $$类）来表示$$ t $$。稍后会看到，这种标记的选择在概率模型中特别方便。这样一般推断的问题就变成了确定联合分布$$ p(x, C_k) $$或等价的$$ p(x, t)
$$，这对情形做了最完整的概率描述。虽然这很有用且富含信息，但最终我们要决定是否给病人进行治疗。我们希望在某些情况下这种选择是最优的（Duda and Hart, 1973）。这就是决策（decision）步骤，也就是决策论的主题：在给定合适的概率下，做出最优的选择。一旦解决了推断问题，决策步骤就变得非常简单，甚至无聊的。     

这里我们介绍一下本书需要用到的决策论的核心思想。更多的背景知识以及更详细的讨论可以参考Berger（1985）和Bather（2000）。    

在我们给出更详细的分析前，先大致的考虑一下我们期望概率论在决定时扮演什么样的角色。当我们获得病人的X光片$$ x $$时，并根据它确定属于两类中的哪一类。我们对这个图像得出的两个类的概率非常感兴趣，标记为$$ p(C_k|x) $$。使用贝叶斯方法这些概率可以表示为：    

$$
p(C_k|x) = \frac{p(x|C_k)p(C_k)}{p(x)} \tag{1.77}
$$    

注意，贝叶斯定理中的任何一个量都可以由联合分布$$ p(x, C_k) $$通过边缘化，或根据某个合适的变量条件化得到。我们可以把$$ p(C_k) $$解释为类$$ C_k $$的先验概率，$$ p(C_k|x) $$就是对应的后验概率。$$ p(C_1) $$表示在拍X光片前病人患有癌症的概率，同样的，$$ p(C_1|x) $$表示获得X光片信息后使用贝叶斯定理修正的后验概率。我们的直觉是选择更大的后验概率，可以最小化分错$$ x $$的可能性。现在我们需要证明这种直觉的正确性。并且我们还会讨论决策的更加通用的标准。    

