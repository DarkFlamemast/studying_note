```python
torch.distributions.Categorical
#根据概率分布来产生sample，产生的sample是输入tensor的index

import torch
from torch.distributions import Categorical
policy_net_output=torch.tensor([-1.6094,-0.2231])  #[0.2,0.8]
pdparams=policy_net_output
pd=Categorical(logits=pdparams)

a=0
for i in range(100):
    action=pd.sample()
    if action:
        a+=1
print(a)
#结果约为80左右
```





DQN有一个显著的问题，就是DQN估计的Q值往往会偏大。这是由于我们Q值是以下一个s'的Q值的最大值来估算的，但下一个state的Q值也是一个估算值，也依赖它的下一个state的Q值...，这就导致了Q值往往会有偏大的的情况出现。

两个Q网络的参数有差别，所以对于同一个动作的评估也会有少许不同。我们选取评估出来较小的值来计算目标。这样就能避免单一Q网络Q值偏大的情况







Dueling DQN网络结构与DQN相似，它有2个分支，1个用于预测state value，它是一个**标量**；另1个用于预测与状态相关的action advantage value，它是1个**矢量**，矢量的每个值对应着1个动作。这2个分支最后输出了每个动作的Q值。

Dueling DQN可直接学习哪些状态是有价值的。这个特性非常重要，因为智能体在与环境做互动的过程中，有些状态对应的动作对环境没任何影响。

Dueling DQN从Q function中剥离出state function和advantage function，state function只用于预测state的好坏，而advantage function只用于预测在该state下每个action的重要性，这样一来，各个分支各司其职，预测效果更好







在多步决策中，学习器不能频繁地得到奖励，且这种基于累积奖赏及学习方式存在非常巨大的搜索空间。

借助人类给出的示范，可以快速地达到这个目的。
