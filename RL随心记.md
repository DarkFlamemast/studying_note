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





