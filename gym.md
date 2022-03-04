# gym

## 搭建一个简单的游戏

```python
import gym
env = gym.make('CartPole-v0')  #构建一个名字叫“CartPole-v0”的Gym场景
for i_episode in range(20):
    observation = env.reset()  # 得到环境给出的初始反馈
    for t in range(100):
        env.render()    #画出当前场景情况
        print(observation)
        action = env.action_space.sample()  # 产生一个允许范围内的随机行动
        observation, reward, done, info = env.step(action) # 得到该次行动的反馈
        if done:
            print("Episode finished after {} timesteps".format(t+1))
            break
env.close()
```

env.step() 有四个返回值，分别代表着 反馈，奖励，是否结束，其他信息  

每个环境所返回的observation的具体含义是不同的，需自行查询官方文档





## 自己制作gym环境

```python
#框架
class SnakeEnv(gym.Env):
    metadata = {# 元数据
        'render.modes': ['human', 'rgb_array'],
        'video.frames_per_second': 2
    }
	
    # 初始化
    def __init__(self):
     
    #动力函数 最重要的部分
    def step(self, action):# 输入为动作
        return state, rewards, done, info# 输出为 状态， 反馈， 终结标志， 调试信息
    
    # 将状态重置为初始状态
    def reset(self):
        return state# 返回初始状态
    
    # 图形化的函数部分
    def render(self, mode='human'):
    
    # 关闭GUI的
    def close(self):

```

