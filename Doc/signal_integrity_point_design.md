# 电路信号完整性设计要点

[TOC]

## 信号完整性定义

泛指信号电压、电流在互联结构传输过程中 信号质量问题，包含噪声、干扰及其造成的时序影响。

## 信号完整性的物理含义

数字信号在传输过程中所有频率分量经由互联路径的模拟相应。

## 数字信号的频率分量

通过傅里叶(FFT)变换将信号特性从时域表达至频域，得到的柱状图就是该信号的频率分量表示。

## 信号完整性如何量化

通过比对信号初始状态的频域表示与通过互联路径后接收端的信号频域，可以直观看到各频率分量的变化。

信号完整性-良好：表示发出与收到的信号特性不发生变化。

## 数字信号的带宽

通过观察信号的FFT图谱，发现数字信号大部分能量都集中在$\frac{1}{\pi \times t_r}$这个频率之下，通常将这个值定义为信号带宽。工程中通常定义为$\frac{0.35}{t_r}$，对设计严格时近似为$\frac{0.5}{t_r}$。

> $t_r$:边沿时间

## 工程上如何估算一个信号的边沿时间

假如时钟信号为 $800Mhz$ 理想方波，其五次谐波即为 $800Mhz \times 5 = 4000Mhz$ ，将五次谐波集合成时域信号，其信号边沿时间约为$0.35 \div 4000Mhz = 0.0000875us = 87.5ps$

## 信号的传输效应的考虑

信号能量大部分集中在信号带宽以下，因此在考虑传输效应时，主要关注最高频率可以达到的信号带宽。

## 如何理解去加重及预加重

数字信号通过互联结构时发生随着信号频率的升高损耗加大的事件，在接收信号发生畸变。

在示波器眼图的观察时，眼图发生闭合。

处理该情况的两种方法：

* 去加重：降低信号低频能量
* 预加重：增加信号高频能量

通过以上处理确保传输后可以得到预期信号特性。

## 何为高速数字信号

* 从频域上看：

  判断是否高速信号不应只考虑该信号的基础频率作为依据，还应包含其高次谐波。

数字电路考察信号边沿速率是最直观的参数之一。

在工程上当信号边沿时间小于4~6倍互联传输延时，该信号应当作为高速信号对待。

* 从时域上看：

  信号完整性考虑的特征阻抗、反射、串扰、及同步开关噪声等问题都是信号0，1跳变是边沿变化的瞬时行为，与其边沿速率相关。