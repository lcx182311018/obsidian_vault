## 模型架构
![[Pasted image 20261009031118.png]]
### Embbeding
将词转化为模型可计算的向量

### positional encoding
在词嵌入上加入位置编码
$X=\operatorname{Embedding}(tokens)+PE$ 
$(\oplus)$代表位置编码与词嵌入逐元素相加，位置编码的作用，**是让模型能够利用词在序列中的位置信息**


### 左侧编码器Encoder
由 6 个结构相同、但参数不共享的编码层堆叠而成，对应图中的 $Nx$ 
每个编码层主要包含两个核心子层

#### 多头注意力 Multi-Head Attention
考虑一个英文句子：
`The robot avoided the rock because it was large.`
其中的 `it` 与前面某个名词存在语义联系。
自注意力机制允许模型在计算 `it` 的特征时，综合其他词的信息，从而建立上下文关联。
其数学表达为：
$\operatorname{Attention}(Q,K,V) = \operatorname{softmax} \left(\frac{QK^\top}{\sqrt{d_k}}\right)V$ 
多头注意力并行进行多组注意力计算，模型能够从不同表示的子空间中建立关联。
**encoder的自注意力不使用因果掩码防止看到未来词** 因为输入给定，模型可以同时关注前后所有输入词

#### 前馈 Feed-Forward
通过自注意力，各位置的特征融合了相关上下文信息，Feed Forward 对每个位置特征分别进行非线性变换：
$FFN(x)=\max(0,xW_1+b_1)W_2+b_2$ 
**self-attention**：不同token位置之间交换信息
**Feed forward** ：对token位置已有的特征进行非线性加工

####  Add&Norm
**ADD** 残差连接：$h=x+F(x)$ 
**Norm** 层归一化$y=\operatorname{LayerNorm}(h)$   对特征进行归一化处理
原文先残差相加再进行归一化处理$\operatorname{LayerNorm}(x+\operatorname{Sublayer}(x))$ 


### 解码器Decoder
相比于Encoder，Decoder多了一个多头注意力层

#### 第一个多头注意力
**掩码和输入嵌入右移一位相结合，保证预测位置$i$ 只能依赖此前给出的目标词**

#### 第二个注意力Encoder–Decoder Attention
左侧encoder的输出连接到了decoder中间的Multi-Head Attention，该层称为 **交叉注意力** 
**decoder在生成当前词,有选择的利用Encoder提供的输入句子信息** 
与普通注意力