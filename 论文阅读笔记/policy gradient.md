# policy gradient

Policy Gradient不通过误差反向传播，它通过观测信息选出一个行为直接进行反向传播，利用reward奖励直接对选择行为的可能性进行增强和减弱，好的行为会被增加下一次被选中的概率，不好的行为会被减弱下次被选中的概率。

policy network 输入state ，输出action









## 与value based算法的区别

### value based

有误差，通过训练进行反向传播，减少loss。从一个状态，执行一个动作，到达下一个状态并获得奖励之后就进行更新。

Value Based方法对应的最优策略通常是确定性策略，因为其是从众多行为价值中选择一个最大价值的行为



### policy based

 没有误差，根据奖励结果提高奖励大的动作的概率，降低奖励小的动作的概率。当一个episode执行完之后，获得总奖励，得到梯度，最后再进行参数更新。

policy based方法对应的随机性策略，对于某一状态，每个动作是以概率被选取 







## 特殊情况

在某些游戏中我们的期望可能永远是正的，即不好的动作也能得一分

如对于某个state下又a,b,c三个动作，三个动作得reward不同但都为正。训练过程中我们使用采样的方法，但可能只采样到b,c，没采样到a，那么b和c得概率在上升，而a得概率只能下降。

解决方法是设立baseline,计算时让期望减去baseline，让不那么好的行为得到负的反馈。









## 优缺点

优点：

- 连续的动作空间（或者高维空间）中更加高效；
- 可以实现随机化的策略；

缺点：

- 评估一个策略通常低效

