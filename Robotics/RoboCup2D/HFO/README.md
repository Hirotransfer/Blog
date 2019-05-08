# [半场进攻：多智能体学习和 Ad-Hoc 协作环境](http://www.cs.utexas.edu/~AustinVilla/sim/halffieldoffense/ )

## 绪论

半场进攻是 **RoboCup** 模拟足球中的一个子任务，模拟了进攻球队试图对防守进球的情况。**HFO** 具有合作多智能体强化学习，自动化 AI 队友和对手，连续状态空间，离散，连续和参数化动作空间，部分观察和完全观察的世界状态之间的选择，进攻或防守的能力以及主动沟通。半场进攻是 **Keepaway** 的延伸，这是一项过去曾经研究过的简单任务。

### 任务描述
在半场进攻中，进攻球队必须超越防守队员，包括守门员，才能进球。任务在足球场的一半上进行，并且在半场线附近开始，球接近其中一个进攻球员。进攻球队试图保持控球，向上移动并得分。防守队员试图将球带离进攻队。任务即情景具有偶然性，当四个事件中的一个发生时，情景结束：

- 进球得分；
- 球超出界限；
- 一名后卫获得控球权（包括守门员接球）；
- 达到了情景的最大时间限制。

每个player自主行动 - 独立地感知世界，选择行动和获得奖励。但是，代理可以口头沟通。由您来设计（或学习）通信协议。
自动 AI 团队成员由[Helios](https://en.wikipedia.org/wiki/RoboCup_2D_Soccer_Simulation_League) RoboCup 团队提供，他们是 2010 年和 2012 年 RoboCup-2d 锦标赛的冠军。连续状态空间具有与环境中感兴趣对象（例如球，进球和players）的角度和距离。一个低层状态空间包含58个连续的原始特征，一个高层状态空间包含10个高信息量特征。两个状态空间的大小随着游戏中players数量的增加而增加。
 HFO 中有三种动作空间选择：a.低级参数化动作空间特征动作原语，如Dash（power，方向），Kick（power，方向），需要连续参数方向的转向（方向），power。一个b.中等水平的行动空间呈现更复杂的参数化的行动Kick_To（目标X，目标y），MOVE_TO（目标X，目标y），Dribble_To（目标X，目标y）。最后，c.高级离散动作空间包含离散动作Move，Dribble，Shoot，Pass 根据预设策略运行。
通过智能体的视锥(view cone)（从player发出的透明楔-transparent wedge）观察世界的状态。因此，默认情况下，即部分地观察世界。HFO 还具有 fullstate 模式，可提供完整，无噪声， 完全观察状态(理想情况)。
学习智能体可以进攻，防守或两者兼而有之。他们可以与 AI 队友和对手任意组合。这种灵活性为单一智能体学习(single-agent learning)，多智能学习(multi-agent learning)，Ad Hoc 团队合作(Ad Hoc teamwork)，自学习(self-play)，协同进化(coevolution)提供了机会。

### 架构-编码

![img](http://www.cs.utexas.edu/~AustinVilla/sim/halffieldoffense/HFODiagram.svg)


HFO 架构由Soccer Server组成，a.所有学习智能体(learning agents)和 AI 控制玩家（NPCs）都连接到该服务器。b.此外，Trainer训练器会跟踪 HFO 场景，并负责启动和停止游戏。c.最后，Visualizer可视化器可用于在游戏进行过程中查看游戏。HFO 版本包括示例随机，手动编码和 Sarsa 代理。

### 基准测试结果
各种 HFO 任务的基准测试结果在下面的发行版本&quot;半场进攻：多用户学习环境和特设团队合作&quot;中提供。

**随机代理**（高级状态动作空间）：

**[1v0](http://www.cs.utexas.edu/~AustinVilla/sim/halffieldoffense/random_1v0.mp4)**

**[1v1](http://www.cs.utexas.edu/~AustinVilla/sim/halffieldoffense/random_1v1.mp4)**

**[2v2](http://www.cs.utexas.edu/~AustinVilla/sim/halffieldoffense/random_2v2.mp4)**

**[3v3](http://www.cs.utexas.edu/~AustinVilla/sim/halffieldoffense/random_3v3.mp4)**

**参考文献**

[1. Half Field Offense: An Environment for Multi-agent Learning and Ad Hoc Teamwork.](http://www.cs.utexas.edu/~AustinVilla/sim/halffieldoffense/)

[2. Half Field Offense in RoboCup Soccer: A Multiagent Reinforcement Learning Case Study.](http://www.cs.utexas.edu/~AustinVilla/sim/halffieldoffense/papers/hfo.pdf")
