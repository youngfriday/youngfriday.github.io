---
title: Knowledge Graph
author: young
date: 2024-12-17 23:18:00 +0800
categories: [Blogs, AI]
tags: [Knowledge Graph]
math: true
---
# Knowledge Graph

## 知识推理

在已有知识的基础之上，推断出位置的知识的过程。

- 基于本体公理的推理
- 基于图结构的推理
- 基于表示学习的推理
- 基于逻辑结构的推理
- 基于神经网络的推理
- 混合推理

### 基于规则的推理

应用：**基于不完备知识库的关联规则挖掘算法 AMIE**

**Association Rule Mining under Incomplete Evidence**

#### 自然演绎

$$
\boldsymbol{\phi }_{\boldsymbol{1}},\boldsymbol{\phi }_{\boldsymbol{2}},\boldsymbol{\phi }_{\boldsymbol{3}},...,\boldsymbol{\phi }_{\boldsymbol{n}}\vdash \boldsymbol{\psi }
$$

- 上式为**相继式(sequent)**，如果我们可以建立证明，则称它为有效(valid)
- $\vdash$ 是**句法后承(syntactic consequence)**关系
- 读作 ：$\boldsymbol{\psi }$ 可以证明自 $\boldsymbol{\phi }_{\boldsymbol{1}},\boldsymbol{\phi }_{\boldsymbol{2}},\boldsymbol{\phi }_{\boldsymbol{3}},...,\boldsymbol{\phi }_{\boldsymbol{n}}$

#### 自然演绎规则

- 合取规则  （合取相当于 "且"，合就是二者都成立）

![image-20241103213550531](https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20241103213550531.png)

![image-20241103213730758](https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20241103213730758.png)

- 双重否定规则

![image-20241103213803447](https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20241103213803447.png)

- 蕴含消去规则/分离规则

![image-20241103214007688](https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20241103214007688.png)

- 蕴含消去规则/反证规则

![image-20241103214409244](https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20241103214409244.png)

- 蕴含引入规则/假言推导

![image-20241103215329806](https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20241103215329806.png)

方框代表在框内做假设：我们为了证明 $\phi \rightarrow \psi$ ，先假设 $\phi$ 成立，再证明 $\psi$ ，假设在框外不成立。

![image-20241103215744603](https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20241103215744603.png)

> 很好理解，你想证明一个带 $\rightarrow$ 的式子成立，并且 $\rightarrow$ 左侧的东西还不是前提，总得假设一下吧哈哈哈 

- 析取规则 （“析取”相当于“或”，析就是分开成立即可）

  1. 析取引入规则：

     ![image-20241103220902208](https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20241103220902208.png)

  2. 析取消除规则：

     ![image-20241103221504143](https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20241103221504143.png)

- 否定规则 (($\bot$ 矛盾)

不要试图去理解矛盾律  [知乎回答](https://www.zhihu.com/question/405337687/answer/1364181673)
![image-20241103224458625](https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20241103224458625.png)

反证法的运用 (proof by contradiction ,PBC)

![image-20241103224841336](https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20241103224841336.png)

- 排中律

![image-20241103224601961](https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20241103224601961.png)

对于任何 $\phi$，有 $\boldsymbol{\phi }\land \lnot \boldsymbol{\phi }$ 为真



#### 总结

![image-20241103224948987](https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20241103224948987.png)

以及一些衍生规则：

![image-20241103225406149](https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20241103225406149.png)

### 基于表示学习的推理

深度学习和表示学习的兴起启发了人们研究基于向量表示的推理方法。例如，TransE 和 DistMul 等知识图谱嵌入系列模型。

- DisMult

![image-20241103230053513](https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20241103230053513.png)

- TransE

![image-20241103230348612](https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20241103230348612.png)
