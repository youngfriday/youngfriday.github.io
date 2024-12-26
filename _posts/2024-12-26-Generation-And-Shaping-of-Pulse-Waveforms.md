---
title: Generation And Shaping of Pulse Waveforms
author: young
date: 2024-12-26 23:25:00 +0800
categories: [NOTES,VLSI]
tags: [Pulse Waveforms]
math: true
---

![006StrhYly1hwykr2hwowj31ww2pg4qr](https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/006StrhYly1hwykr2hwowj31ww2pg4qr.jpg)

—— 今日长缨在手，何时缚住苍龙？

# 脉冲波形的产生和整形

## 1. 概述

## 矩形脉冲的波形参数

![image-20241203201617441](https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20241203201617441.png)

- 脉冲幅度$U_m$ ：脉冲高低电平之间电压的最大变化值
- 脉冲宽度$t_w$ ：脉冲幅度 $0.5U_m$ 处，脉冲前后沿之间的时间间隔
- 脉冲周期$T$ ：在周期性重复脉冲序列两个相邻脉冲间的事件间隔
- 上升时间$t_r$ ：脉冲上升沿从$0.1U_m$ 上升到 $0.9U_m$ 所需时间
- 下降时间$t_f$ ：脉冲下降沿从$0.9U_m$ 下降到$0.1U_m$ 所需时间
- 占空比：脉冲宽度与周期之比，$D=t_w/T$

## 获取矩形脉冲波形（时钟）的途径

1. 用整形电路把已有的周期性变化波形整形产生
   - 整形电路：施密特触发电路、单稳态电路
2. 用振荡器电路直接产生
   - 振荡器电路：对称式、非对称式、石英晶体振荡器、环形振荡器，用施密特触发电路构成的振荡器

> 用门电路可以构成施密特触发电路、单稳态电路与多谐振荡器
>
> 用555定时器也可以构成施密特触发电路、单稳态电路与多稳态振荡器

## 2. 施密特触发器

![image-20241203203839409](https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20241203203839409.png)

### 特点

1. 双稳态
2. 电平触发
3. 电压波形很陡
4. 电压传输特性有回差 :$\Delta V_T=V_{T+}-V_{T-}$
5. 抗干扰能力强

### 结构和工作原理

![image-20241225111528527](https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20241225111528527.png)

### 应用

1. 波形变换——三角波、正弦波变成方波

   ![image-20241225113409728](https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20241225113409728.png)

2. 波形整形——消除噪声干扰

   ![image-20241225113543093](https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20241225113543093.png)

3. 幅度鉴别

   ![image-20241225114030518](https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20241225114030518.png)

## 3. 单稳态触发器

### 特点

1. 有一个稳态和一个暂稳态
2. 在外界触发信号作用下，能从稳态 $\rightarrow$ 暂稳态，维持一段时间后自动返回稳态
3. 暂稳态维持的时间长短取决于电路内部参数

### 结构和工作原理

1. 微分型 —— CMOS门电路

   <img src="https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20241226143617352.png" alt="image-20241226143617352" style="zoom:67%;" />

2. 积分型 ——TTL门电路

   <img src="https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20241226143637071.png" alt="image-20241226143637071" style="zoom:67%;" />

### 应用

1. 声控灯：停止声音，并不会立马熄灭

   <img src="https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20241225114602866.png" alt="image-20241225114602866" style="zoom: 80%;" />

2. 感应水龙头：一旦撤回，立马会回到稳态

   <img src="https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20241225114745914.png" alt="image-20241225114745914" style="zoom:80%;" />

## 4. 多谐振荡器

### 特点

- 无需外加触发信号，电源接通后，就可以产生自激振荡
- 是无稳态电路
- 也称矩形脉冲发生器，因含丰富的谐波分量，又称多谐振荡器

### 最简单的环形振荡器

![image-20241226210911890](https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20241226210911890.png)

> $t_{pd}$ 不可控

### 实用的环形振荡器 （TTL）

![image-20241226211020590](https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20241226211020590.png)

![image-20241226211801067](https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20241226211801067.png)

### 用施密特触发器构成的多谐振荡器

![image-20241226212127743](https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20241226212127743.png)

### 对称式多谐振荡器 (TTL)

> 注意稳态的位置，都是(output/input)变化率极其大的时候

![image-20241226212942438](https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20241226212942438.png)

![image-20241226213009865](https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20241226213009865.png)

![image-20241226213911915](https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20241226213911915.png)

### 非对称多谐振荡器 (CMOS)

> 注意稳态的位置，都是(output/input)变化率极其大的时候

<img src="https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20241226220741181.png" alt="image-20241226220741181" style="zoom:80%;" />

<img src="https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/d186126f960fbac607acd51a0188053.jpg" alt="d186126f960fbac607acd51a0188053" style="zoom: 33%;" />

## 5. 555定时器

### 组成与特点

- 3个5 $k \varOmega $  电阻——名字的由来
- 比较器 $C_1$ 和 $C_2$
- 基本RS触发器
- 输出缓冲器 $G_3$ 与 $G_4$
- 放电管 $T_D$ 组成  

![image-20241226222453575](https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20241226222453575.png)

![image-20241226222510200](https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20241226222510200.png)

结构图的等效简化电路如下：

![image-20241226222544672](https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20241226222544672.png)

> 放电管 $T_D$ 的作用：
>
> - 给外接电容C提供放电通路，之后可以看到
> - 经过电阻借电源，$T_D$ 等效 $v_0$

![image-20241226223144694](https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20241226223144694.png)

#### 口诀:

- 大大出小
- 小小出大
- 小大保持

#### 补充说明:

<img src="https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20241226223325471.png" alt="image-20241226223325471" style="zoom:67%;" />

#### 电路符号：

<img src="https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20241226223441634.png" alt="image-20241226223441634" style="zoom:67%;" />

### 用555组成施密特触发器

$$
U_2=U_6=U_I
$$

![image-20241226223545344](https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20241226223545344.png)

回差电压：

$$
\Delta U_T=U_{T+}-U_{T-}=\frac{2}{3}V_{CC}-\frac{1}{3}V_{CC}=\frac{1}{3}V_{CC}
$$

回差可调：

![image-20241226224107653](https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20241226224107653.png)

### 用555定时器接成多谐振荡器

![image-20241226230234117](https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20241226230234117.png)

![image-20241226230244691](https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20241226230244691.png)

关于充放电：

<img src="https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20241226230506682.png" alt="image-20241226230506682" style="zoom:67%;" />

<img src="https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20241226231124076.png" alt="image-20241226231124076" style="zoom:67%;" />

![image-20241226231305834](https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20241226231305834.png)

### 用555组成单稳态触发器

![image-20241226231502213](https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20241226231502213.png)

![image-20241226231540385](https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20241226231540385.png)