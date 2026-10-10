[原论文](SignNav_Directional_Signage-Cue_Guided_Visual_Navigation_in_Large-Scale_Indoor_Environments.pdf)
## idea
作者观察到目前vln研究都集中在一个小型室内场景下，存在可见到终点以及对导航前完整的自然语言指令的要求；作者选择研究大型室内场景，如机场、医院，导航思路参考人类使用指示牌的行为，将室内环境的方向性线索作为引导，实现navi

## work
SignNav框架聚焦于具身智能体如何将方向性标志线索落地为物理导航行为，而非声称解决开放式的标志解析、复合标志推理或通用视觉标志对齐问题。
构建了LSI‑Dataset，该数据 集包含带有路牌标注的LSI环境以及自动生成的轨迹‑动 作片段。
### challenge
#### DynamicCueGrounding：
同一提示在自中心视图中出现的位置不同， 或当前可见的可通行结构不同时，可能暗示不同的动作
#### SparseOb servability
路牌稀疏，可能在对应路口变得可操 作之前就被观察到，因此需要时间记忆来保留先前观察到 的提示，并在后续使用时。









##   从 MDP 到 POMDP
[]([(54 封私信 / 1 条消息) 【Agent】从 MDP 到 POMDP：部分可观测决策框架及其在 Agent 中的应用 - 知乎](https://zhuanlan.zhihu.com/p/2066682931481929361))
### MDP
一个MDP有一个五元组定义：
![[Pasted image 20261008175103.png]]
![[Pasted image 20261008175117.png]]
#### 马尔可夫性
![[Pasted image 20261008175221.png]]

### POMDP:部分可观测马尔可夫决策过程
对MDP引入可观测性
POMDP 在 MDP 五元组的基础上多加两样东西，变成一个七元组：
![[Pasted image 20261008175704.png]]
![[Pasted image 20261008175712.png]]
其余不变
![[Pasted image 20261008180019.png]]
##### 马尔可夫性在观测层面失效
![[Pasted image 20261008183025.png]]

#### 信念状态 Belief State
既然单个观测不够，那就把「我对自己所处状态的全部认知」压缩成一个概率分布，这就是**信念状态**：
![[Pasted image 20261008183735.png]]![[Pasted image 20261008183745.png]]

#### 信念更新：贝叶斯滤波
![[Pasted image 20261008183911.png]]