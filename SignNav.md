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


