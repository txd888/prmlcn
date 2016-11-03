正如我们将在5.3节看到的那样，误差函数的梯度可以通过误差反向传播的方法高效地计算出来。这个梯度信息的使用可以大幅度加快找到极小值点的速度。原因如下所述：    

在式（5.28）给出的误差函数的二次近似中，误差曲面由$$ b, H $$确定，它包含了$$ W(W+3) / 2 $$个独立的元素（因为矩阵$$ H $$是对称的），其中$$ W $$是$$ w $$的维数（即网络中可调节参数的总数）。这个二次近似的局部最小值依赖于$$ O(W^2) $$个参数，并且我们不应该奢求在收集到$$ O(W^2)
$$个条独立的信息之前就能够找到最小值。如果我们不使用梯度信息，我们不得不进行$$ O(W^2) $$次函数求值，每次求值都需要$$ O(W) $$个步骤。因此，使用这种方法求最小值的计算复杂度为$$ O(W^3) $$。    

现在，把这种方法与使用梯度信息的算法做比较。由于每个$$ \nabla E $$的计算带来$$ W $$个信息，所以我们预计找到函数的最小值需要$$ O(W) $$次梯度计算，每个这样的计算只需要进行$$ O(W) $$步，所以最小值可以在$$ O(W^2) $$步内找到。由于这个原因，使用梯度信息构成了训练神经网络的实际算法的基础。    

