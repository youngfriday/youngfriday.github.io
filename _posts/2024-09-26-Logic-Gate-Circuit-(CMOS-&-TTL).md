---
title: Logic Gate Circuit  (CMOS & TTL)
author: young
date: 2024-09-26 22:43:00 +0800
categories: [VLSI, NOTES]
tags: [CMOS&TTL]
math: true
---
# Logic Gate Circuit  (CMOS & TTL)

## 1. Diode

### Properties

![image-20240919230313136](https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20240919230313136.png)

1. 开关作用

   - 正偏导通 
     $$
     U_D\approx \begin{cases}
     	0.7V\,\, \text{硅管}\\
     	0.3V\,\, \text{锗管}\\
     \end{cases}
     $$

   - 反偏截止

     ![image-20240919231538874](https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20240919231538874.png)

2. 动态特性

   ![](https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20240919231807418.png)

   

   <img src="https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20240919231825239.png" alt="image-20240919231825239" style="zoom:80%;" />

   

3. 门电路

   - 优点：**结构简单**
   - 缺点：**不实用，如电平偏移、带负载能力差**

## 2. CMOS

![image-20240919232318611](https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20240919232318611.png)

### 2.1 The structure of MOS

<img src="https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20240919232533526.png" alt="image-20240919232533526" style="zoom: 80%;" />

一般情况下：

- 源极（S）与衬底（B）是短接的（图中是一并接地的）

- 在简写符号中，箭头$\rightarrow$的方向就是$P\rightarrow N$的方向（中间那个小块是衬底B！！！）

  <img src="https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20240923203245010.png" alt="image-20240923203245010" style="zoom:80%;" />

- 在$GB$ or $GS$之间加电压即可使得$SD$之间导通
  - PMOS: $V_{GB}<0$，氧化层下方形成“+”沟道（少数载流子空穴聚集）
  - NMOS: $V_{GB}>0$，氧化层下方形成“-”沟道（少数载流子电子聚集）

### 2.2 Input & Output of MOS

1. When $V_{DS}=\text{const}$

   原因在于$V_{GS}++$，导电沟槽的截面积++，$I_{DS}++$

   ![image-20240919234219188](https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20240919234219188.png)

2. When $V_{DS}\ne\text{const}$

   ![image-20240919234553267](https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20240919234553267.png)

3. When $V_{DS}\ V_{GS} $ changing together

   ![image-20240923195638609](https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20240923195638609.png)

MOS 管的不同工作区

![image-20240923195058559](https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20240923195058559.png)

### 2.3 Basic switch circuit

![image-20240923201605221](https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20240923201605221.png)

## 3. Gate Circuits of CMOS

### 3.1 CMOS Inverter

1. CMO 反相器（非门）工作原理

<img src="https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20240923204432947.png" alt="image-20240923204432947" style="zoom:80%;" />

为了杜绝以上这种电阻大小的矛盾问题，我们构造如下CMO互补电路：

![image-20240923204614622](https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20240923204614622.png)

注意从上到下的CMO分别为PMOS、NMOS，不能颠倒！

如果要正常工作，高电平一点要高于$V_{IH}$，低电平一定要低于$V_{IL}$。

而在这两者之间，两个CMOS均导通，**该区域具有非常高的增益（输入电压$V_{IN}$的微小变化会引起输出电压$V_{OUT}$的较大变化），且电压传输特性曲线(VTC)几乎是一个阶跃函数。**

#### The Complementary of CMOS

![image-20240923212042551](https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20240923212042551.png)

Tricks:

- $P\leftrightarrow N $
- 串联 $\leftrightarrow$ 并联

### 3.2 The Other Kinds of CMOS Gate Circuit

#### 1. Logic Gate

1. 与非

   ![image-20240923212435919](https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20240923212435919.png)

2. 或非

   ![image-20240923212459000](https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20240923212459000.png)

3. 构造

   ![image-20240923212719069](https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20240923212719069.png)

- CMOS门电路**天然是反相的**，所以你**不可能使用一个CMOS门电路构建正逻辑**，例如与门。
- 其实这很好理解，比如只看下面接地的部分，一但满足导通条件(1)势必会带来输出结果为0，反相就是这么来的。
- 注意，不能将PMOS与NMOS颠倒，那样只会使得两者在输入为高低电平时都导通

，没有意义。

4. 缺点与改进

   ![image-20240923214934119](https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20240923214934119.png)

   ![image-20240923214951063](https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20240923214951063.png)

   其实就是对每一个输入、输出进行标准化操作，我们在在电路的每一个输入端、输出端各增设一级反相器（这些具有标准参数的反相器被称为**缓冲器**）

   但值得注意的是，在添加缓冲器之后，电路的逻辑功能也会发生相应的变化

#### 2. OD Gate (Open-Drain Output Gate)

在CMOS电路中，为了满足输出**电平变换、吸收大负载电流**以及实现**线与**连接等需要，将**输出级电路结构改成一个漏极开路输出**的MOS管，构成OD门。

<img src="https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20240923232146199.png" alt="image-20240923232146199" style="zoom:80%;" />

当我们要实现线与操作时，如果还是使用上面的电路，直接连接到一起会出现短路（当上下均输出为高电平的时候）的现象，而在这里，我们将输出级改为漏极开路输出，这样即使均为高电平输出，也会有保护电阻$R_L$存在，不会出现问题。

![image-20240923232457223](https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20240923232457223.png)

#### 3. CMOS TG (Transmission Gates)

CMOS传输门其实就相当于一个开关，如下就是保证只有当$C=1$时才能导通输入的信号。

注意：由于$T_1,T_2$管的结构形式是对称的，漏极源极也没有什么本质之分，因此**CMOS传输门属于是双向组件**，输入端输出端可以交换使用。

![image-20240923233115889](https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20240923233115889.png)

- 用传输门实现**异或**

  <img src="https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20240923234301011.png" alt="image-20240923234301011" style="zoom:67%;" />

- 双向模拟开关（**也是双向对称组件**）

  <img src="https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20240923234253930.png" alt="image-20240923234253930" style="zoom:80%;" />

#### 4. Output Buffer

三态输出的CMOS门电路的三个状态：**高电平、低电平、高阻态**。

因为这种电路结构总是连接在集成电路的输出端，所有又称**输出缓冲器(Output Buffer)**。

<img src="https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20240923235038380.png" alt="image-20240923235038380" style="zoom: 80%;" />

<img src="https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20240924194522555.png" alt="image-20240924194522555" style="zoom:80%;" />

## 4. TTL

### 4.1 Triode

1. 双极型三极管基本结构

   <img src="https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20240924195240839.png" alt="image-20240924195240839" style="zoom:60%;" />

   同样的，在这里$\rightarrow$ 所指的方向也是 $P\rightarrow N$

2. 基本开关电路

   <img src="https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20240924195519068.png" alt="image-20240924195519068" style="zoom:67%;" />

   <img src="https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20240924195812300.png" alt="image-20240924195812300" style="zoom:67%;" />

3. 三极管反相器（非门）

   ![image-20240924202544292](https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20240924202544292.png)

   ![image-20240924202615121](https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20240924202615121.png)

   

4. 集成门电路按开关元件分类

   <img src="https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20240924203444230.png" alt="image-20240924203444230" style="zoom:67%;" />

### 4.2 TTL NOT Gate

#### 1. Circuit structure and working principle

![](https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20240926194427287.png)

- 输出为高电平

  <img src="https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20240926194545087.png" alt="image-20240926194545087" style="zoom: 80%;" />

  - 首先$T_1$一定是饱和导通的$\Rightarrow V_{B1}=0.9V$
  - 在$T_1$的集电极回路中，无论$T_2$导通与否，$I_C$都极小（未导通时由于电阻为$R_2$与$T_2$的$BC$反向电阻之和，电阻极大，故电流$I_C$极小），判定为深度饱和，由图像可知$V_{CE}\rightarrow 0$，故$T_2$的发射极不可能导通。
  - 因此$V_{E2}\rightarrow 0$，而$V_{C2}$为高电平，故$T_5$截止，$T_4$导通，输出为高电平。

- 输出为低电平

  <img src="https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20240926194613517.png" alt="image-20240926194613517" style="zoom:80%;" />

  - 首先假设$T_1$导通，则此时$V_{B1}=3.4V+0.7V=4.1V$，而此时又$T_2,T_5$又一定导通，如此判定$V_{B1}=0.7V+0.7V+0.7V=2.1V$。矛盾，则假设不成立，$T_1$截止！
  - 所以此时$T_2,T_5$导通，而此时$V_{C2}$降低，$V_{E2}$增加，$T_4,D_2$截止。故输出为低电平。

#### 2. Voltage transmission characteristics

![image-20240926202412612](https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20240926202412612.png)

$AB$ ：截止区

![image-20240926202547926](https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20240926202547926.png)

$BC$：

![image-20240926202645954](https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20240926202645954.png)

分析为什么是线性：

$$
V_{E2}=V_{I}-0.7
$$

$$
由于在放大区\Rightarrow I_{C2}\propto I_{E2}=\frac{V_{I}-0.7}{R_2}
$$

$$
V_O=V_{CC}-I_{C2}R_2-1.4
$$

显然是$V_O$是关于$V_I$的线性减函数。

$CD$：

![image-20240926205540245](https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20240926205540245.png)

$DE$：

![image-20240926205653687](https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20240926205653687.png)

#### 3. Input Noise Tolerance

![image-20240926205906733](https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20240926205906733.png)

#### 4. Conclusion of the Structure & Principle

![image-20240926210430674](https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20240926210430674.png)

$T_2$的倒相级：

- 当$T_2$截止时，$V_{E2}\rightarrow0$，$V_{C2}\rightarrow V_{CC}$
- 当$T_2$导通时，可通过上下的分压分析，电流越来越大，两者越来越解决，一减一增

#### 5. Input Load Characteristics  

<img src="https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20240926211318605.png" alt="image-20240926211318605" style="zoom:80%;" />

<img src="https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20240926211336728.png" alt="image-20240926211336728" style="zoom:67%;" />

> 注意这里有一个特例，就是当为与门时，只要有一个输入端是低电平，就会将电压钳制，另外的端口即使接的是大电阻也不能等效为高电平
{: .prompt-tip }

<img src="https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20240928165813381.png" alt="image-20240928165813381" style="zoom:67%;" />

![image-20240926212314658](https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20240926212314658.png)

### 4.3 The Other Gates of TTL

1. 与非

   ![image-20240926212841829](https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20240926212841829.png)

   ![image-20240926212956332](https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20240926212956332.png)

   - 只要$A$或者$B$有一个为低电平，就能将$T_1$“钳住”——从而使得$T_2,T_5$截止，$T_4$导通输出高电平。

2. 或非

   ![image-20240926213221996](https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20240926213221996.png)

   - 相当于接了两个输入级和倒相级，任何一个为高电平都能使得最终输出低电平。

3. 异或

   ![image-20240926213408363](https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20240926213408363.png)

### 4.4 OC Gate (Open Collector Gate)

![image-20240926214208170](https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20240926214208170.png)

1. 原本推拉式输出电路结构的局限性：

   - 不能线与
   - 不能满足大电流与高电压负载要求
   - 输出的高电平的值是固定的

   （其实与上面普通CMOS电路的缺点一致，这也是为什么后来有了OD门）

2. OC门结构

   ![](https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20240926214527249.png)

3. 线与的实现

   ![image-20240926214726554](https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20240926214726554.png)

4. 外接电阻$R_L$的计算

   - 输出为高电平，电阻有最大值，分压不能高！

     ![image-20240926214819544](https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20240926214819544.png)

   - 输出为低电平，电阻有最小值，分压不能低！

     ![image-20240926215034344](https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20240926215034344.png)
     >  **注意：**这里在计算输出为低电平时的$m^{\prime}$时，需要分类讨论：
     {: .prompt-tip }
     
      a. 当之后是**与**门时，两输入端同时接低电平可以先并联再连接，不影响结果，这样就造成了$m^{\prime}$最小应该取输出端的“与”门数！

      b. 当之后是**或**门时，$m^{\prime}$取值为输入端的总个数

      c. 当为高电平输出时，同样不能省略，$m^{\prime}$取值为输入端的总个数
     
     ​ ![image-20240926222714495](https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20240926222714495.png)

### 4.5 TS Gate

TTL中的三态门，和3.2.4中的CMOS的三态输出门一致。

![image-20240926223307007](https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20240926223307007.png)

还是相当于有一个使能端$EN$，当**图标不带圈时，说明高电平对应正常的与非输出**！！！

原理很简单，相当于$E$极再并联一个二极管$EN$，由$EN$的导通与否来钳制电压。

![image-20240926223319281](https://youngfriday-1328789051.cos.ap-beijing.myqcloud.com/Typora/image-20240926223319281.png)
