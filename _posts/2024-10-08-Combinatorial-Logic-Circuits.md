---
title: Combinatorial Logic Circuits
author: young
date: 2024-10-08 20:18:00 +0800
categories: [NOTES,VLSI]
tags: [Logic Circuits]
math: true
---

![e1616c086745128ab2e4c9e0593f773](https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/e1616c086745128ab2e4c9e0593f773.jpg)

# 组合逻辑电路

## 1. 概述

数字系统由数字电路模块构成，可分为两大类：**组合逻辑电路**、**时序逻辑电路**

组合逻辑电路的：

- 定义：

  电路任一时刻的输出状态**只取决于该时刻各输入状态的组合**，而与电路的原状态无关

- 特点：

  功能上**无记忆**，结构上**无反馈**

## 2. 组合逻辑电路的分析

![image-20241007201538293](https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20241007201538293.png)

## 3. 组合逻辑电路的设计

![image-20241007202009397](https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20241007202009397.png)

## 4. 常用的组合逻辑电路

### 4.1 编码器  译码器

#### 编码器

1. 普通编码器

   - 对某个输入端出现有效信号的状态进行编码（用二进制表示）
   - 任何时刻，**只能有一个输入端有有效信号**(类似于独热编码)

   ![image-20241007203131841](https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20241007203131841.png)

2. 优先编码器

   - 允许同时输入两个及以上的有效信号
   - 输入信号规定了优先顺序，当有多个有效信号同时出现时，只对优先级最高的信号进行编码。

   ![image-20241007203602141](https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20241007203602141.png)

#### 译码器

![image-20241007203949346](https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20241007203949346.png)

1. 二进制译码器

   ![image-20241007204321564](https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20241007204321564.png)

   ![image-20241007204342163](https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20241007204342163.png)

2. 二-十进制译码器

   ![image-20241007204559874](https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20241007204559874.png)

   ![image-20241007204750046](https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20241007204750046.png)

3. 七段显示译码器

   ![image-20241007204851305](https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20241007204851305.png)

   <img src="https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20241007204919655.png" alt="image-20241007204919655" style="zoom:50%;" />

   ![image-20241007204956489](https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20241007204956489.png)

### 4.2 数据选择器

1. 4选1数据选择器

   ![image-20241007205507392](https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20241007205507392.png)

   <img src="https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20241007205635322.png" alt="image-20241007205635322" style="zoom:70%;" />

2. 八选一数据选择器

   ![image-20241007205814085](https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20241007205814085.png)

   就是通过 $A_2A_1A_0$ 这个二进制数从 $0 \sim 7 $ 中间选一个。让对应编码的 $D_i$ 通路输出到 $Y$ 上，而 $W$ 就是 $\overline{D_i}$ 

### 4.3 加法器

1. 半加器和全加器

   ![image-20241007210535442](https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20241007210535442.png)

   1. 半加器 （其实就是异或运算）

      ![image-20241007210854954](https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20241007210854954.png)

   2. 全加器

      ![image-20241007210947154](https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20241007210947154.png)

   3. 两个半加器构成一个全加器

      ![image-20241007211333089](https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20241007211333089.png)

      - 其实很好理解，就相当于 $A_i+B_i+C_{i-1}$ ，然后再考虑下进位的事，反正不是在 $A_i+B_i$ 的时候进位，就是在 $+C_i$ 的时候进位，最大也就是 $1+1+1$ 也只能进1位，所以后面直接用或门就行了。

2. 多位数加法器

   e.g. 四位二进制相加 $A_3A_2A_1A_0+B_3B_2B_1B_0$

   1. 串行进位加法器——其实就是采用4个1位全加器组成

      ![image-20241007212424561](https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20241007212424561.png)

      缺点就是这个运算不能同时进行，后面的得等前面的进位算出来才能进行，所以速度比较慢，不实用

   2. 快速加法器、超前进位加法器

      ![image-20241007213028884](https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20241007213028884.png)

      相当于搞了个东西专门只用来算每一位的进位（脱离了原来是在加法器中一并生成的局限性），我们叫这个玩意——“进位门”

      这样就不用等待低位的进位信号了、

   3. 超前进位集成4位加法器 $74LS283$

      <img src="https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20241007215129823.png" alt="image-20241007215129823" style="zoom:67%;" />

   4. 超前进位集成4位加法器 $74LS283$ 的应用

      ![image-20241007215248857](https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20241007215248857.png)

### 4.4 数值比较器

就是比较两个输入 $A \ B$ 的大小关系的

1. 1位数值比较器

   ![image-20241008192413018](https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20241008192413018.png)

2. 2位数值比较器

   ![image-20241008192648215](https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20241008192648215.png)

   <img src="https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20241008192719311.png" alt="image-20241008192719311" style="zoom:67%;" />

3. 多位数值比较器

   ![image-20241008194008617](https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20241008194008617.png)

4. 集成数值比较器 $74LS85$

   ![image-20241008194328731](https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20241008194328731.png)

   

## 5. 常用组合逻辑电路的应用

### 5.1 译码器设计组合逻辑电路

![image-20241008195142475](https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20241008195142475.png)

- 省流：很简单，要谁就接上谁，然后用一个”与“门就行。

### 5.2 数据选择器设计组合逻辑电路

![image-20241008195414195](https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20241008195414195.png)

![image-20241008200741036](https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20241008200741036.png)

- 省流：翻译出对应的数字码，给有的项全接上1，没有的全接上0就行。

### 5.3 加法器设计组合逻辑电路

![image-20241008200126275](https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20241008200126275.png)

- 省流：想加几就在$B$ 一侧输入几就行了。









