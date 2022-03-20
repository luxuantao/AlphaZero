# AlphaZero玩N子棋的pytorch实现

参考自： https://github.com/junxiaosong/AlphaZero_Gomoku

补充了详尽的注释

## 文件说明

- game.py定义了棋盘，执行游戏中的逻辑

- human_play.py负责人机交互

- mcts_pure.py定义了蒙特卡洛树搜索的全过程（没有用到神经网络，playout中决策的时候选择各个动作的概率是相等的）

- mcts_alphaZero.py定义了蒙特卡洛树搜索的全过程（用到神经网络，playout中决策的时候选择各个动作的概率是用神经网络算出来的）

- policy_value_net_pytorch.py定义了神经网络架构，输入棋盘状态，输出各个动作概率以及当前状态的价值评估

- train.py训练神经网络（先是通过自我对弈收集训练数据，数据直接由当前最新模型生成，并用于训练更新自身。为了保证自我对弈生成的数据的多样性，动作概率分布上加上了Dirichlet noise。训练的时候，损失由策略网络和价值网络两部分组成，当然也可以加上正则项。验证的时候是看当前模型和只利用朴素蒙特卡洛树搜索的模型相比胜率有多少）

详尽的算法原理可以参考： https://zhuanlan.zhihu.com/p/32089487






