---
{"dg-publish":true,"permalink":"/🎓研究生/上课/数字信号处理/dsp复习/","dgPassFrontmatter":true}
---


# 注意事项

计算器、铅笔，尺、手表。
不要空白。只要题目思路对了，均给分。
# 第一、二章

## 1.信号的定义、分类

### 定义

$$y(t)=A\cos (ft+\varphi)$$

- $A$:幅度

- $f$:频率

- $\varphi$:相位

传输信息的函数。信号是信息的物理表现形式，信息是信号的具体内容。数字化是智能化和网络化的基础。

### 分类

| 信号源数量         | 自变量数目            | 信号定义域 | 自变量性质       |
| ------------------ | --------------------- | ---------- | ---------------- |
| 标量信号（单通道） | 一维（语音，T）       | 实值       | 连续（时间）信号 |
| 矢量信号（多通道） | 二维（图像，XY）      | 复值       | 离散（时间）信号 |
|                    | 三维（黑白视频，XYT） |            |                  |

是否具有唯一确定表述

- 确定信号：可以由一个完全定义的过程确定
- 随机信号：无法预测
- 信号分析手段
  - 时域：自相关（随机信号在原点相关性最强，白噪声自相关后为冲击函数）
  - 频域：功率谱
  - <img src="https://i.loli.net/2021/09/28/jM9KlSqcQF71xt3.png" alt="image-20210928200214903" style="zoom: 33%;" />

按幅值性质

-  模拟信号：连续幅值，连续时间
- 量化阶梯信号：离散幅值，连续时间
- 抽样数字信号：连续幅值，离散时间
- 数字信号：离散幅值，离散时间
- <img src="https://s2.loli.net/2022/01/01/enI5Pf2ZD6kYOrv.png" alt="image-20210928194644654" style="zoom: 33%;" />

模拟➡数字：采样、量化、保持、输出，即1324

数字➡模拟：量化、低通、平滑，即421

### 典型的信号处理计算

#### 滤波

低通滤波器、高通滤波器、带通滤波器、带阻滤波器、陷波滤波器、多频带滤波器、梳状滤波器 

#### 幅度调制

- 载波信号－高频正弦波$A\cos (\Omega_0t)$
- 调制信号－低频带限信号$x(t)$
- 相乘→已调信号$y(t)=Ax(t)\cos(\Omega_0t)$
- <img src="https://s2.loli.net/2022/01/01/gCUme8kDjv2dwqV.png" alt="image-20220101134222135" style="zoom: 50%;" />
应用
放大与滤波—压缩频带 ：信号与噪声频谱不重叠 （慢变信号）
- <img src="https://s2.loli.net/2022/01/01/jqQyai1HOSDoFNr.png" alt="image-20220101141416482" style="zoom: 50%;" />
- 调制：低频信号与载波相乘得$V_m(t)$，至中频区
- 解调： 中频区的$V_m(t)t$，与载波相乘得$V_d(t)$
- <img src="https://s2.loli.net/2022/01/01/ZEDIt3A6k2hJjiP.png" alt="image-20220101141758873" style="zoom: 50%;" />
- <img src="https://s2.loli.net/2022/01/01/1BMZ9eAEDfiQNK7.png" style="zoom:50%;" />


## 2.频率响应、系统函数、差分方程、卷积

### 卷积

#### 定义

- 若$x(t)\xrightarrow{FT}X(\omega), h(t)\xrightarrow{FT}H(\omega)$
- 时域的卷积是频域的相乘：$x(t)*h(t)\xrightarrow{FT}X(\omega)H(\omega)$
- 时域的相乘是频域卷积**乘以系数**：$x(t)h(t)\xrightarrow{FT}\frac1{2\pi}X(\omega)*H(\omega)$
- 连续：$x(t)*h(t)=\int_{-\infty}^{+\infty}x(\tau)h(t-\tau)d\tau$
- 离散：$x(n)*h(n)=\sum\limits_{m=-\infty}^{+\infty}x(m)h(n-m)$

#### 计算

 翻褶、移位、相乘、相加

<center><img src="https://s2.loli.net/2022/01/01/LjeP4yNn1R73qQU.png" alt="image-20220101114250794" style="zoom: 60%;" /><center>

### 系统函数和频率响应

系统初始状态为零，输入$\delta(n)$→输出$h(n)$（单位冲激响应）$\begin{cases}\stackrel{FT}{\longrightarrow}H(e^{j\omega})=\sum\limits_{n=-\infty}^{\infty}h(n)e^{-j\omega n}（频率响应）\\\stackrel{ZT}{\longrightarrow}H(z)=\sum\limits_{n=-\infty}^{\infty}h(n)z^{-n}（系统函数）\end{cases}$

### 定义式及转化

1. 频率响应：$H(e^{j\omega})=\sum\limits_{n=0}^{\infty}h(n)e^{-j\omega}$
2. 系统函数：$H(z)=\sum\limits_{n=0}^{\infty}h(n)z^{-n}$
3. 差分方程：$y(n)=-\sum\limits_{k=1}^Na(k)y(n-k)+\sum\limits_{r=0}^Mb(r)x(n-r)$
4. 卷积关系：$y(n)=\sum\limits_{k=-\infty}^\infty x(k)h(n-k)=x(n)*h(n)$

- (4)式两边分别求Z变换可得：$Y(z)=X(z)H(z)\to H(z)=\frac{Y(z)}{X(z)}$
- 对差分方程两边求Z变换，分离变量后两边同时除以X(z)可得到H(z)

### 数字信号处理系统的基本组成

<center><img src="https://s2.loli.net/2022/01/01/hxt6Q8RcuMOvmqa.png" alt="image-20211017212329693" style="zoom:80%;" /><center>

- 前置滤波器：将输入信号$x_a(t)$中高于折叠频率(等于抽样频率的一半)的分量加以滤除。**DSP缺点：不适用于高频**
- 后置滤波器：把阶梯波形平滑成预期的模拟信号，以滤除掉不需要的高频分量，生成所需的模拟信号$y_a(t)$。

## 3.四种傅里叶变换的形式

|         时域         |        傅里叶        |                      频域                      |
| :------------------: | :------------------: | :--------------------------------------------: |
|   连续周期$(T_p)$    |     傅里叶级数FS     |         非周期离散$(\frac{2\pi}{T_p})$         |
|      连续非周期      |     傅里叶变换FT     |                   非周期连续                   |
|   离散$(T)$非周期    | 序列的傅里叶变换DTFT |           周期$(\frac{2\pi}{T})$连续           |
| 离散$(T)$周期$(T_p)$ |  离散傅里叶变换DFT   | 周期$(\frac{2\pi}{T})$离散$(\frac{2\pi}{T_p})$ |

### 傅里叶级数FS

<center><img src="https://s2.loli.net/2022/01/01/lvRnzs3W8qLT1Yd.png" style="zoom: 33%;" /><center>

- 正变换：<img src="https://s2.loli.net/2022/01/01/TkB2bpKtn9vACc6.png" alt="image-20211017223604791" style="zoom:50%;" />

- 反变换：<img src="https://i.loli.net/2021/10/17/qxYmHEfzeDrNR4L.png" alt="image-20211017233017016" style="zoom: 50%;" /><img src="https://s2.loli.net/2022/01/01/wRE3nxBH89grpWk.png" alt="image-20211017223629341" style="zoom: 67%;" />

  $X(jK\Omega_0)$是频谱相邻两谱线间角频率的间隔，K为谐波序号。

### 傅里叶变换FT(CTFT)

<center><img src="https://s2.loli.net/2022/01/01/LoC89xgBFhJri2Y.png" alt="image-20220101152031931" style="zoom:50%;" /><center>

- 正变换：<img src="https://s2.loli.net/2022/01/01/37OWJuN48hfb1Uk.png" alt="image-20211017223904777" style="zoom:50%;" />

- 反变换：<img src="https://s2.loli.net/2022/01/01/TmeLPlyBNrHkvOU.png" alt="image-20211017223909350" style="zoom:50%;" />

### 序列的傅里叶变换DTFT

<center><img src="https://s2.loli.net/2022/01/01/7NCtU2ozpQxTaqL.png" alt="image-20220101152352685" style="zoom: 33%;" /><center>

- 正变换：<img src="https://s2.loli.net/2022/01/01/gyFPKzwDG8lkRWa.png" alt="image-20211017223920480" style="zoom:50%;" />

- 反变换：<img src="https://s2.loli.net/2022/01/01/OzGKuABdwcQ4qE6.png" alt="image-20211017223924824" style="zoom:50%;" />

### 离散傅里叶变换DFT

<center><img src="https://s2.loli.net/2022/01/01/7g3GMU4EQisZyXC.png" alt="image-20211017223224165" style="zoom: 80%;" /><center>

- 正变换：<img src="https://s2.loli.net/2022/01/01/jdRHBycAeftvw5O.png" alt="image-20211017224120784" style="zoom:50%;" />
- 反变换：<img src="https://s2.loli.net/2022/01/01/dGWIt7vsl9LrANT.png" alt="image-20211017224155404" style="zoom:50%;" />

### 关系

- DTFT是离散非周期时间信号的傅里叶变换，其特点是变换结果在频域连续；
- DFS是对DTFT频谱进行频域等间隔抽样后得到的结果，其特点是变换结果在频域离散；
- DFT是将DFS结果在频域主值区间变换，便于计算机进行数值计算。

## 4.采样定理、理想取样和实际取样

### 实际取样

<center><img src="https://s2.loli.net/2022/01/01/QdzIheAK9yH1kRO.png" alt="image-20220101151550015" style="zoom:40%;" /><center>


- 为防止混叠，$\omega_s-\omega_m>\omega_m，即f_s>>2f_m\to采样定理$
- 恢复信号：用$\frac{\omega_s}2$进行低通滤波

### 理想取样

<center><img src="https://s2.loli.net/2022/01/01/aRk6eCw2ErsMfI9.png" alt="image-20220101154321429" style="zoom:40%;" /><center>


### 理想取样的恢复（内插过程）

<center><img src="https://s2.loli.net/2022/01/01/9oaDil7rGv5pJYc.png" style="zoom: 33%;" /><center>
<center><img src="https://i.loli.net/2021/10/27/zRogSBUDpaVyhKW.png" alt="image-20211027161453417" style="zoom:50%;" /><center>
<center><img src="https://i.loli.net/2021/10/27/WlvYzKewPoVXIu5.png" alt="image-20211027161520600" style="zoom:50%;" /><center>


## 5.线性非移变系统⭐

### 线性系统

#### 1、概念

满足叠加原理的系统

- 可加性
设$y_1(n)=T[x_1(n)],\quad y_2(n)=T[x_2(n)]$
若$y_1(n)+y_2(n)=T[x_1(n)]+T[x_2(n)]=T[x_1(n)+x_2(n)]$
说明系统$T[\cdot]$满足可加性
- 比例性
设$y_1(n)=T[x_1(n)]$
若$a_1y_1(n)=a_1T[x_1(n)]=Ta_1[a_1x(n)]$
说明系统$T[\cdot]$满足比例性或齐次性

#### 2、验证

- 正向：验证比例性，假设$x_1(n)$和$x_2(n)$，看$y_1(n)+y_2(n)=T[x_1(n)]+T[x_2(n)]$是否成立（大题）
- 反证：零输入零响应，$x(n)=0$时，若$y(n)=0$不成立，则不是线性系统（小题）

### 时不变（移不变）系统

#### 1、概念

若系统的响应与激励加于系统的时刻无关，则该系统为时不变或移不变系统。
即：若$y(n)=T[x(n)]$，则$y(n-m)=T[x(n-m)]$成立

#### 2、验证

$y(n-m)$将所有$n$换成$n-m$，$T[x(n-m)]$只将$x(n)$变成$x(n-m)$

### LSI系统

#### 1、概念

同时具有线性和移不变性的离散时间系统称为LSI(Linear Shift Invariant)系统。

#### 2、单位抽样(冲激)响应$h(n)$

当输入为$\delta(n)$时，系统输出为$h(n)=T[\delta(n)]$

#### 3、性质

##### 1、输出

输出$y(n)$可以用输入$x(n)$与单位抽样响应$h(n)$的卷积来表示:

$$y(n)=x(n)*h(n)$$

##### 2、交换律

<img src="https://i.loli.net/2021/10/25/Hp5fzmS8DGobWMl.png" alt="image-20211025192659270" style="zoom:67%;" />

##### 3、结合律

<img src="https://i.loli.net/2021/10/25/4X1ELAhHom3M8xP.png" alt="image-20211025192719679" style="zoom:67%;" />

##### 4、分配律

<img src="https://i.loli.net/2021/10/25/4iLbtIogESHNFRe.png" alt="image-20211025192748966" style="zoom:67%;" />

### 因果系统

#### 1、定义

某时刻的输出只取决于此时刻和此时刻以前的输入的系统。

#### 2、判断

根据定义判断即可。

<img src="https://s2.loli.net/2022/01/01/ERyfMhIgJmOdDCv.png" alt="image-20211025194025340" style="zoom:50%;" />

#### 3、LSI系统是因果系统的充分必要条件

$h(n)$是因果序列。
$$h(n)=0,n<0$$

- 因果序列：n<0，x(n)=0的序列

### 稳定系统

#### 1、定义

稳定系统是指：有界输入产生有界输出的系统。
即：$if\quad|x(n)|\leq M< \infty,\quad then\quad |y(n)\leq P<0|$

#### 2、LSI系统是稳定系统的充分必要条件

单位抽样响应绝对可和。
$$\sum\limits_{n=-\infty}^{\infty}|h(n)|=q<\infty$$

#### 3、判断

1. LSI系统：求$h(n)$，判断是否绝对可和
2. 以$y(n)=T[x(n)]$给出：用定义有界输入得到有界输出来证明
3. 反证法：若有界输入能得到无界的输出，则该系统肯定不稳定

### 频域

<center><img src="https://i.loli.net/2021/11/08/KApeYroF7XRgTUS.png" alt="image-20211108210207856" style="zoom: 80%;" /><center>

### 例题

线性、移不变

![image-20220101171348068](https://s2.loli.net/2022/01/01/hvyC4oXwYLxnZIl.png)

## 6.求解常系数线性方程⭐

### 系统的差分方程描述

#### 非递归型（FIR）

输出的现在值仅仅取决于输入的现在值与输入的过去值

![image-20220101162258681](https://s2.loli.net/2022/01/01/DfRJxIMs4kQtCv9.png)

#### 递归型（IIR）

输出的现在值不仅取决于输入的现在值与过去值，还取决于输出的过去值。

![image-20220101162047031](https://s2.loli.net/2022/01/01/qKMFGDvsg4wdu96.png)

### 迭代法

- 默认线性移不变，当为因果系统时只需向n>0方向递推，否则需要向两个方向分别递推。
  - 分别乘以$u(n)与u(-n-1)$
- 一个常系数线性差分方程并不一定代表因果系统，也不一定表示线性移不变系统。这些都由边界条件（初始）所决定。

![image-20220101165449287](https://s2.loli.net/2022/01/01/pNEHdfFsCSmPbAZ.png)

### 系统结构画法

<img src="https://s2.loli.net/2022/01/01/3C84eAVWgbXSFEh.jpg" alt="1" style="zoom:50%;" />

# 第三四五章

## 离散时间信号和系统的频域分析

### 一、Z变换与Z反变换

#### 1、Z变换的定义

$$X(z)=\sum\limits_{n=-\infty}^\infty x(n)z^{-n}, 其中z为复变量$$

#### 2、Z变换的收敛域

$$R_{x^-}<|z|<R_{x^+}$$

<center><img src="https://i.loli.net/2021/10/28/4WjR8wHdg5IOa2G.png" alt="image-20211028104113286" style="zoom:30%;" /><center>


##### 1、有限长序列

$只在|z|=0/\infty处考察$

$x(n)=\begin{cases}x(n)\neq0\quad n_1\leq n\leq n_2\\0\quad其他\end{cases}$

- $n_1<0,n_2\leq0:0\leq|z|<\infty;$
- $n_1\geq0,n_2>0:0<|z|\leq\infty;$
- $n_1<0,n_2>0:0<|z|<\infty。$

##### 2、无限长序列

###### 1、单边序列

a、右边序列

$x(n)=\begin{cases}x(n)\quad n\geq n_1\\0\quad n<n_1\end{cases}$

$拆分：X(z)=\sum\limits_{n=n_1}^{-1}x(n)z^{-n}+\sum\limits_{n=0}^{\infty}x(n)z^{-n}$

$R_{x^-}<|z|<\infty,若为因果序列则无穷处可取等号。\to 某个圆以外的z平面$

b、左边序列

$x(n)=\begin{cases}x(n)\quad n\leq n_2\\0\quad n>n_2\end{cases}$

$拆分：X(z)=\sum\limits_{n=-\infty}^{0}x(n)z^{-n}+\sum\limits_{n=1}^{n_2}x(n)z^{-n}$

$0<|z|<R_{x^+}\to 某个圆以内的z平面$

###### 2、双边序列

$拆分为左边序列和右边序列之和:X(z)=\sum\limits_{n=-\infty}^{-1}x(n)z^{-n}+\sum\limits_{n=0}^\infty x(n)z^{-n}$

左边序列收敛域：$0<|z|<R_{x^+}$
右边序列收敛域：$|z|>R_{x^-}$

若$R_{x^-}<R_{x^+}$，则收敛域为$R_{x^-}<|z|<R_{x^+}$（圆环），**否则z变换不存在**

##### 3、极点与零点

$$X(z)=\frac{P(z)}{Q(z)}$$

- $P(z)$的根为零点，$Q(z)$的根为极点
- 极点会使$X(z)\to\infty$，**极点的模为收敛半径端点**
- ✳收敛域计算：
  - ①根据Z变换定义求X(z)
  - ②根据X(z)确定收敛半径(极点的模)
  - ③根据序列类型判断收敛域

#### 3、Z反变换

$x(n)=\frac{1}{2\pi j}\oint_cX(z)z^{n-1}dz$，直接求需在收敛域内找一条闭合曲线积分

##### 1、留数法

x(n)等于围线内极点留数之和。

1. 求$X(z)z^{n-1}$，确定n取值（双边需要讨论）
2. 求$X(z)z^{n-1}$极点：$z_i+0/\infty:X(z)\cdot z^{n-1}=\frac{z^m}{\prod(z-z_i)}$
3. $\begin{cases}有无穷阶\quad求围线外极点留数取反\\无无穷阶\quad 直接求\begin{cases}单阶极点：Res[X(z)z^{n-1},z_k]=[(z-z_k)\cdot X(z)z^{n-1}]_{z=z_k}\\N阶极点：Res[X(z)z^{n-1},z_k]=\frac1{(N-1)!}\frac{d^{N-1}}{dz^{N-1}}[(z-z_k)^N\cdot X(z)z^{n-1}]_{z=z_k}\end{cases}\end{cases}$
4. 求留数和

##### 2、长除法

将X(z)展开成幂级数，单边序列有优势（P38 3.2.3）

- $|z|>R_{x^-}$，因果系列，展开成负幂级数
- $|z|<R_{x^+}$，左边序列，展开成正幂级数
- 双边序列通过收敛域拆成单边序列

##### 3、部分分式法

$X(z)=\sum\limits_i\frac{A_iz}{z-z_i}+A_0,其中：z_i为X(z)极点,A_i为Res[\frac{x(z)}{z},z_i]$

1. 求$\frac{X(z)}{z}$
2. 将$\frac{X(z)}{z}$展开为部分分式
3. 将展开的部分分式乘以$z$，得到$X(z)$的部分分式表达式
4. 对各部分分式进行反变换
5. 写出原序列

##### 4、常用Z变换对

<center><img src="https://i.loli.net/2021/11/05/UjTKEZ18NJquaA7.png" alt="image-20211105144715416" style="zoom:30%;" /><center>


#### 4、Z变换的性质

<img src="https://s2.loli.net/2022/01/02/EUC4bJeo2SWiVRG.png" alt="image-20220102135334400" style="zoom:50%;" />

#### 5、Z变换与拉普拉斯变换、傅里叶变换的关系

<center><img src="https://i.loli.net/2021/11/08/Fb7NPAYLCtVOlHB.png" alt="image-20211108095835080" style="zoom:50%;" /><center>


<center style="color:#C0C0C0;text-decoration:underline">拉普拉斯变换</center>

<center><img src="https://i.loli.net/2021/11/08/1sVk5aJt8YWzpwP.png" alt="image-20211108095919313" style="zoom:50%;" /><center>


<center style="color:#C0C0C0;text-decoration:underline">Z变换</center>

当$z=e^{st}$时，序列的z变换就等于理想抽样信号的拉氏变换。

$\begin{cases}z=re^{j\omega}\\e^{st}=e^{(\sigma+j\Omega)T}\end{cases}\to\begin{cases}r=e^{\sigma T}\quad一一对应\\\omega=\Omega T\quad多值映射\end{cases}$

<img src="https://s2.loli.net/2022/01/02/VaOHNdqKS5nYsm8.png" alt="image-20211108104517431" style="zoom:30%;" />

<img src="https://s2.loli.net/2022/01/02/qL6siEBa4SOp7ZG.png" alt="image-20211108104557520" style="zoom:30%;" />

### 二、序列傅里叶变换

#### 1、定义

$$X(e^{j\omega})=\sum\limits_{n=-\infty}^{\infty}x(n)e^{-j\omega n}$$

#### 2、反变换

$$x(n)=\frac1{2\pi}\int_{-\pi}^\pi X(e^{j\omega})e^{j\omega n}d\omega$$

#### 3、成立条件

$$x(n)绝对可和：\sum\limits_{n=-\infty}^\infty |x(n)|<\infty$$

#### 4、性质

Z变换在单位圆上的特例→Z变换性质不变

##### 1、周期性✳

<img src="https://s2.loli.net/2022/01/02/OR1xwKrEUIpba4l.png" alt="image-20211108105934238" style="zoom: 43%;" />

来自$\omega$的周期性

##### 2、线性

<img src="https://s2.loli.net/2022/01/02/4PySL5E2QseKhjw.png" alt="image-20211108110036138" style="zoom:43%;" />

同Z变换

##### 3、时移与频移

<img src="https://s2.loli.net/2022/01/02/H47WLJ1ltpnkyrh.png" alt="image-20211108110216731" style="zoom:43%;" />

时移同Z变换，频移$a=e^{j\omega_0}$

##### 4、卷积

<img src="https://s2.loli.net/2022/01/02/srt2aWpYmG1jEqP.png" alt="image-20211108110402760" style="zoom:34%;" />

##### 5、帕塞瓦尔定理

能量

<img src="https://s2.loli.net/2022/01/02/ueJUb9dILHP4kiY.png" alt="image-20211108110443578" style="zoom:43%;" />

##### 6、对称性✳

共轭对称序列：$x_e(n)=x_e^*(-n)$
共轭反对称序列：$x_o(n)=-x_e^*(-n)$

一般序列可表示为共轭对称序列和共轭反对称序列之和：$x(n)=x_e(n)+x_o(n)$
又有：$x^*(-n)=x_e(n)-x_o(n)$
可知：$\begin{cases}x_e(n)=\frac12[x(n)+x^*(-n)]\\x_o(n)=\frac12[x(n)-x^*(-n)]\end{cases}$

<img src="https://s2.loli.net/2022/01/02/neY6RIQ37UmigMz.png" alt="image-20211108120149597" style="zoom:43%;" />

## 离散傅里叶变换

### 一、周期序列

#### 1、定义

若$x(n)$满足$x(n)=x(n+mN)$，其中m为整数，N为m=1时满足关系式的最小正整数
则x(n)为周期信号，记作$\tilde x(n)$

主值区间：$n\in[0,N-1]$
主值序列：主值区间上的序列$x(n)$

$\tilde x(n)$与主值$x(n)$关系
<img src="https://s2.loli.net/2022/01/02/ewZLbBk45cKuJ2V.png" alt="image-20211108212114208" style="zoom:50%;" />

#### 2、周期序列的循环位移

$$y(n)=x((n\pm m))_NR_N(m)$$

<center><img src="https://i.loli.net/2021/11/08/DeGUj8ZyAbHzdpk.png" alt="image-20211108212313540" style="zoom:50%;" /><center>


#### 3、序列的卷积

##### 1、线性卷积

###### 1、定义

$$y_1(n)=x_1(n)*x_2(n)=\sum\limits_{m=-\infty}^\infty x_1(m)x_2(n-m)$$
当两个序列均从0开始有限长($x_1(n)$长$N_1$，$x_2(n)$长$N_2$)时，上式可写作：
$$y_1(n)=x_1(n)*x_2(n)=\sum\limits_{m=0}^{N_1+N_2-2} x_1(m)x_2(n-m)$$

###### 2、计算

<img src="https://s2.loli.net/2022/01/02/hjAx1vB5YVIgirH.png" alt="image-20211108213612869" style="zoom: 67%;" />

<center style="color:#C0C0C0;text-decoration:underline">表格法计算线性卷积</center>

##### 2、圆周卷积

###### 1、定义

设$x_1(n)$长度为$N_1，0≤n≤N_1-1$； $x_2(n)$长度为$N_2，0≤n≤N_2-1$
取圆周卷积长度$L>max(N_1,N_2)$
$$y_c(n)=x_1(n)\otimes x_2(n)=\sum\limits_{m=0}^{L-1}x_1(m)x_2((n-m))_LR_L(m)$$

###### 2、计算

<img src="https://s2.loli.net/2022/01/02/WY4eTx8KnfEmbi5.png" alt="image-20211117164412605" style="zoom:67%;" />

<center style="color:#C0C0C0;text-decoration:underline">表格法计算圆周卷积</center>

###### 3、注意事项

1. 确定圆周卷积的长度L
2. 参与圆周卷积的各个信号的长度、圆周卷积结果 的长度均为L
3. 循环移位、截取主值序列
4. 当圆周卷积长度$L ≥ + N_1+N_2-1$时，圆周卷积的结果和线性卷积相等

##### 3、圆周卷积和线性卷积的关系

$$y_c(n)=y_l((n))_LR_L(n)$$

### 二、周期序列的傅里叶级数和傅里叶变换

#### 1、傅里叶级数

周期为T的连续时间信号 x(t)，可表示为无穷级数

$x(t)=\sum\limits_{k=-\infty}^{\infty}a_k\cdot e^{jk(\frac{2\pi}T)t}，其中a_k=\frac1T\int_{-\frac{T}2}^{\frac  T2}x(t)e^{-jk(\frac{2\pi}T)t}dt$

#### 2、周期序列的傅里叶级数（DFS）

设$\tilde{x}(n)$是周期为N的信号，则

$\tilde{X}(k)=DFS[\tilde{x}(n)]=\sum\limits_{n=0}^{N-1}\tilde{x}(n)e^{-jk(\frac{2\pi}T)t}$

$\tilde{x}(n)=IDFS[\tilde{X}(k)]=\frac1N\sum\limits_{n=0}^{N-1}\tilde{X}(k)e^{jk(\frac{2\pi}T)t}$

### 三、离散傅里叶变换（DFT）

#### 1、定义

$$X(k)=DFT[x(n)]=\sum\limits_{n=0}^{N-1}x(n)W_N^{kn}\quad 0\leq k\leq N-1$$

$x(n)=IDFT[x(k)]=\frac1N\sum\limits_{n=0}^{N-1}x(n)W_N^{-kn}\quad 0\leq k\leq N-1$

$其中W_N=e^{-j\frac{2\pi}{N}}$

##### 物理意义

- 序列的离散傅里叶变换是序列的Z变换在单位圆上的N个等间隔采样值
- 序列的离散傅里叶变换是序列的傅里叶变换在频率主值区间[0, 2π]上的N个等间隔采样值

#### 2、性质

周期性、线性、时移和频移、圆周卷积、共轭性、对称性

*即序列的傅里叶变换卷积→圆周卷积，-k→N-k，-n→N-n*

#### 3、频域采样

只有当频率采样点数N ≥序列长度M时，才能保留原信号的全部信息。

#### 4、应用

##### 用DFT计算卷积

<img src="https://s2.loli.net/2022/01/02/6MU9tloc2zLJbQ4.png" alt="image-20220102141636815" style="zoom:33%;" />

##### 用DFT进行信号的频谱分析

混叠：同时满足时域（$f_s>>2f_c$）和频域采样定理（$F\leq\frac1{T_P}$）时，信号在时域和频域都不会出现混叠

## 快速傅里叶变换

### 1.DFT和FFT的运算量

<img src="https://s2.loli.net/2022/01/02/58EAG2lNPCBFbof.png" alt="image-20220102142243840" style="zoom: 50%;" />

### 2.$W_N^k$性质

.$W_4^1=-j$

<img src="https://s2.loli.net/2022/01/02/xRW2zXwSGg4tKEN.png" alt="image-20220102142323543" style="zoom:50%;" />

### 3.时域抽取基2FFT算法

旋转因子的的确定

倒序（二进制）输入正序输出

<img src="https://s2.loli.net/2022/01/02/b8EGUIjm7ocYgKp.png" alt="image-20220102142930509" style="zoom: 50%;" />

### 4.频域抽取基2FFT算法

与时域抽取算法对称

<img src="https://s2.loli.net/2022/01/02/9LOvS2keQqcaA5g.png" alt="image-20220102142951330" style="zoom:50%;" />

# 第六、七章

## 0.概念

### 数字滤波器工作原理

<img src="https://s2.loli.net/2022/01/01/WJh8dpyxZljE39s.png" alt="image-20220101195756994" style="zoom: 33%;" />

### 数字滤波器表示方法

<img src="https://s2.loli.net/2022/01/01/Bmyr8zDvETLHCJn.png" alt="image-20220101200239953" style="zoom:33%;" />

<img src="https://s2.loli.net/2022/01/01/A7Jvyt4QloPIRYa.png" alt="image-20220101200555777" style="zoom: 25%;" />

### 三个基本运算单元

加法器，单位延时，乘常数的乘法器

### 数字滤波器的分类

| 功能 | 实现方法 | 设计方法 | 处理信号   | 数字模拟   |
| ---- | -------- | -------- | ---------- | ---------- |
| 低通 | FIR      | 切比雪夫 | 经典滤波器 | 数字滤波器 |
| 高通 | IIR      | 巴特沃斯 | 现代滤波器 | 模拟滤波器 |
| 带通 |          |          |            |            |
| 带阻 |          |          |            |            |

<img src="https://s2.loli.net/2022/01/01/ACKa1RrWoIjLmBb.jpg" alt="1" style="zoom:50%;" />

## 1.IIR DF

### IIR DF特点

1. 单位冲激响应h(n)是无限长的
2. 系统函数H(z)在有限长Z平面（0<|Z|<∞)有极点存在
3. 结构上存在输出到输入的反馈，也即结构上是递归型的
4. 因果稳定的IIR滤波器其全部极点一定在单位圆内

### 系统函数及差分方程

![image-20220101203816679](https://s2.loli.net/2022/01/01/E2zLvX864GklJVy.png)

### 直接型⭐

#### 直接Ⅰ型

##### 原理

直接根据差分方程得出

##### 流图

<img src="https://s2.loli.net/2022/01/01/vLBwKWMbe6I3Fix.jpg" alt="2" style="zoom: 33%;" />

##### 特点

1. 两个网络级联：第一个横向结构M节延延时网络实现零点，第二个有反馈的N节延时网络实现极点。
2. 共需(N+M)级延时单元
3. 系数ai,bi不是直接决定单个零极点，因而不能很好地进行滤波器性能控制
4. 极点对系数的变化过于灵敏，从而使系统频率响应对系统变化过于灵敏，也就是对有限精度（有限字长）运算过于灵敏，容易出现不稳定或产生较大误差

#### 直接Ⅱ型

##### 原理

对调+合并

##### 流图

<img src="https://s2.loli.net/2022/01/01/zbdoW9MiZXnhuEH.jpg" alt="3" style="zoom:50%;" />

##### 特点

1. 实现N阶滤波器（一般N>=M)只需N级延时单元，所需延时单元最少。故称典范型
2. 同直接I型一样，具有直接型实现的一般缺点

![image-20220101210048436](https://s2.loli.net/2022/01/01/z6qn9xfwi73IuY8.png)

### 级联型⭐

#### 原理

用若干个基本二阶节级联起来构成滤波器

每个二阶节含一对零极点：$H(z)=\frac{1+\beta_{1i}z^{-1}+\beta_{2i}z^{-1}}{1-\alpha_{1i}z^{-1}-\alpha_{2i}z^{-2}}$

<img src="https://s2.loli.net/2022/01/01/lU1Y6C3BExZ7Ki2.jpg" alt="4" style="zoom: 40%;" />

#### 流图

<img src="https://s2.loli.net/2022/01/01/eaXqwVUYQsj5P2v.jpg" alt="5" style="zoom:67%;" />

#### 特点

1. 每个二阶节系数单独控制一对零点或一对极点，有利于控制频率响应
2. 组合可互换，选接近的零极点组合
3. 误差累积（相乘）

![image-20220101212245091](https://s2.loli.net/2022/01/01/UI9QL3WN4BGJjMo.png)

### 并联型⭐

#### 原理

用若干个基本二阶节级联起来构成滤波器

并联型的基本二阶节的形式（要求分子比分母小一阶）：$H(z)=\frac{\beta_{0}+\beta_{1}z^{-1}}{1-\alpha_{1}z^{-1}-\alpha_{2}z^{-2}}$

**缺右下角**

<img src="https://s2.loli.net/2022/01/01/ek1NFcfAJXO6Tsv.jpg" alt="6" style="zoom:50%;" />

#### 流图

<img src="https://s2.loli.net/2022/01/01/axnFpBUN9buqV8G.jpg" alt="7" style="zoom:67%;" />

#### 特点

1. 可以单独调整极点位置，但不能和级联那样单独控制零点
2. 其误差最小。因为并联型各基本节的误差互不影响，所以比级联误差还少

![image-20220101215750899](https://s2.loli.net/2022/01/01/7jqRiNoASwH5GWn.png)

## 2.FIR DF

### FIR DF特点

1. 系统的h(n)是个有限长序列
2. 系统函数|H(z)|在|z|>0处收敛，极点全部在z=0处(**即FIR一定为稳定系统**)
3. 结构上主要是非递归结构，没有输出到输入反馈。但有些结构中（例如频率抽样结构）也包含有反馈的递归部分

### 系统函数及差分方程

<img src="https://s2.loli.net/2022/01/01/iSeTfBGP5cgoYxd.png" alt="image-20220101220542204" style="zoom: 40%;" />

### 直接型

卷积型、横截型。转置可用于验算

#### 流图

<img src="https://s2.loli.net/2022/01/01/EqhD5kuQoBe6vfc.jpg" alt="8" style="zoom:50%;" />

### 级联型

#### 原理

当需要控制滤波器的传输零点时，可将H(z)系统函数分解成二阶实系数因子的形成

#### 流图

<img src="https://s2.loli.net/2022/01/01/IBlZwG4e7vVcPdD.jpg" alt="9" style="zoom:67%;" />

#### 特点

1. 由于这种结构所需的系数比直接型多，所需乘法运算也比直接型多，很少用
2. 由于这种结构的每一节控制一对零点，因而只能在需要控制传输零点时用

### 线性相位⭐

#### 满足条件及相频特性

- 偶对称（第一类）：$h(n)=h(N-1-n)，对称中心\tau=\frac{N-1}2$
  - $\theta(\omega)=-\tau\omega$
- 奇对称（第二类）：$h(n)=-h(N-1-n)，对称中心\tau=\frac{N-1}2，\beta_0=\pm\frac\pi2$
  - $\theta(\omega)=\beta_0-\tau\omega$

#### 四种情况的结构流图

- $N$的奇偶性改变的是滤波器结构，即有没有单独的中间项；
- $h(n)$的奇偶性改变的是滤波器的正负符号。

1. $h(n)$为偶对称，$N=$偶数

   <img src="https://s2.loli.net/2022/01/01/96CJFByvsegbhXD.jpg" alt="10" style="zoom: 33%;" />

   <img src="https://s2.loli.net/2022/01/01/jQdz2kep6c7AIFi.jpg" alt="14" style="zoom: 50%;" />

2. $h(n)$为奇对称，$N=$偶数

   <img src="https://s2.loli.net/2022/01/01/JIy5164VgGrTnPf.jpg" alt="11" style="zoom: 33%;" />

   <img src="https://s2.loli.net/2022/01/01/uGkxbLd1Wej39QE.jpg" alt="15" style="zoom: 50%;" />

3. $h(n)$为偶对称，$N=$奇数

   <img src="https://s2.loli.net/2022/01/01/JIy5164VgGrTnPf.jpg" style="zoom: 33%;" />

   <img src="https://s2.loli.net/2022/01/01/ezhlm8xIH52NGZJ.jpg" alt="16" style="zoom: 50%;" />

4. $h(n)$为奇对称，$N=$奇数

   <img src="https://s2.loli.net/2022/01/01/5tVYmw1aZXjWuML.jpg" alt="13" style="zoom: 33%;" />

   <img src="https://s2.loli.net/2022/01/02/o7uh2HvmDdyctZN.jpg" alt="17" style="zoom:50%;" />

### 频率抽样型

#### 原理

![image-20220101230119459](https://s2.loli.net/2022/01/01/sFETQHajPzkvS7B.png)

#### 流图

![18](https://s2.loli.net/2022/01/01/JVW5zlQcGDiwpnR.jpg)

梳状滤波器+谐振柜

#### 特点

##### 优点

系数H(k)直接就是滤波器在$\omega_k=\frac{2\pi}Nk$处的频率响应。因此，控制滤波器的频率响应是很直接的

##### 缺点

- 所有的相乘系数及H(k)都是复数，应将它们先化成二阶的实数，这样乘起来较复杂，增加乘法次数，存储量
- 所有谐振器的极点都是在单位圆上,由$\omega_N^{-k}$决定考虑到系数量化的影响，当系数量化时，极点会移动，有些极点就不能被梳状滤波器的零点所抵消。（零点由延时单元决定，不受量化的影响）系统就不稳定了

## 3.间接法设计IIR DF

### 技术指标

<img src="https://s2.loli.net/2022/01/02/u3627kXNfLmUMwQ.png" alt="image-20220102091751095" style="zoom: 33%;" />



### 由模拟滤波器设计数字滤波器条件

1. S平面的虚轴jΩ必须映射到Z平面的单位圆上
2. 为保持滤波器稳定性，S平面的左半平面必须映射到Z平面的单位圆内

#### 采用幅度平方函数求解模拟传函Ha(S)⭐

![image-20220102094149014](https://s2.loli.net/2022/01/02/ibFRzmUyoXCEIdr.png)

### Butterworth低通滤波器

#### 特点

1. 通带内，幅频很平坦，随着频率的升高而单调下降。
2. 全 极点型滤波器，且极点均匀分布在Ωc的圆上，并且与虚轴对称。

#### 幅度平方函数

<img src="https://s2.loli.net/2022/01/02/HmM2wFSZuV1iKsn.png" alt="image-20220102095128358" style="zoom: 33%;" />

其中$N$为整数，为滤波器阶次，$\Omega_C$为截止频率（-3dB，$\frac{1}{\sqrt{2}}$）

#### 系统函数求解

##### 已知$\Omega_C,N$

![image-20220102103238838](https://s2.loli.net/2022/01/02/8zuL7J3DBlfqhXb.png)

##### 已知Ωc 、 Ωs和Ω=Ωp的衰减Ap

![image-20220102104714686](https://s2.loli.net/2022/01/02/UyEku1BbCjfrTv9.png)

##### 已知Ωp 、 Ωs和Ω=Ωp的衰减Ap 和As

![image-20220102105225067](https://s2.loli.net/2022/01/02/9snPA7CQpHEyJDz.png)

**注：N向上取整**

### 冲激响应不变法⭐

#### 特点

1. 时域逼近良好，频域逼近良好(模拟频率Ω和数字频率w之间呈线性关系)$\to$*线性相位模拟滤波器（如贝塞尔滤波器）可以映射成线性相位数字滤波器。
2. 由于有频率混叠效应，只能设计带限滤波器（低通、带通）。
3. 若要对高通和带阻实行冲激不变法，则必须先对高通和带阻滤波器加一**保护滤波器**，滤掉高于折叠频率以上的频带。它会增加设计的复杂性和滤波器的阶数，因而只有在一定要追求频率线性关系或保持网络瞬态响应不变时才使用。
4. 对于带通和低通滤波器，需充分限带，**若阻带衰减越大，则混叠效应越小**。

#### 映射规则

$$z=e^{sT}$$

<img src="https://s2.loli.net/2022/01/02/1KE3yWfPCwZY6nH.png" alt="image-20220102121716604" style="zoom:33%;" />

1. S平面上每一条宽为$\frac{2\pi}{T}$的横带部分，将重叠映射到z平面的整个平面上
2. 每一横条的左半边映射到z平面单位圆内，每一横条的右半边映射到z平面单位圆外
3. S平面的虚轴$(j\Omega)$轴映射到z平面单位圆上，虚轴上每一段长为$\frac{2\pi}{T}$的线段都映射到z平面单位圆上一周
4. 数字滤波器的频响并不是简单地重现模拟滤波器的频响，而是模拟滤波器频响的周期延拓

#### 设计流程

1. 根据设计要求，设定指标
2. 将数字滤波器性能指标变换为中间模拟滤波器的性能指标
3. 设计出符合要求的中间模拟滤波器的系统函数Ha(s)
4. 将Ha(s)展成部分分式的并联形式，利用$H_a(s)=\sum\limits_{k=1}^N\frac{A_k}{s-s_k}\to H(z)=\sum\limits_{k=1}^N\frac{A_k}{1-e^{s_k T}z^{-1}}$设计H(z)
5. 将 H(z)乘 以  抽 样 周 期T， 完  成  数 字 滤 波 器 系 统 函 数H(z) 的 设 计

![image-20220102124334667](https://s2.loli.net/2022/01/02/fZ7Ep1P6kY9Jtlu.png)

### 双线性变换法⭐

#### 特点

1. 解决了冲激不变法的混叠失真问题
2. 设计十分方便
3. 模拟角频率与数字角频率存在非线性关系。避免了混叠失真，却又带来了非线性的频率失真。
4. 设计要求AF的幅频响应是分段常数型，在各个分段边缘的临界频率点产生畸变，可通过频率**预畸变**加以校正。

#### 映射关系

<img src="https://s2.loli.net/2022/01/02/4cYzPVxb6N9lqCF.jpg" alt="1" style="zoom: 33%;" />

**频率压缩**：把整个S平面压缩变换到某一中介的S1平面的一条横带里。

<img src="https://s2.loli.net/2022/01/02/axIAOhw7UoeRdVQ.jpg" alt="2" style="zoom:43%;" />

**数字化**：将S1平面通过标准变换关系$z=e^{s_1T}$变换到z平面。

<img src="https://s2.loli.net/2022/01/02/ZOrfNPCXMtEqbAz.png" alt="image-20220102130154571" style="zoom:30%;" />



**变换常数C的选择**：使AF与DF在低频处有较确切的对应关系:$C=\frac 2T$

#### 设计流程

1. 根据要求，设定指标。
2. 将制定中间模拟滤波器的性能指标转换为数字滤波器的性能指标。**（2域）**
3. 将各分段频率临界点预畸变：$\Omega=Ctg(\frac\omega2)|_{低频处}=\frac2Ttg(\frac\omega2)$。**（1域）**
4. 根据设计要求，选定双线性变换常数C。
5. 设计中间模拟滤波器的系统函数Ha(s)。
6. 将$s=C\frac{1-z^{-1}}{1+z^{-1}}$代入Ha(s)中，得到DF 的H(z)。

![image-20220102134032172](https://s2.loli.net/2022/01/02/6mjUtAieTCX1Kuc.png)

## 4.IIR VS FIR

<img src="https://s2.loli.net/2022/01/02/4MOQhfev367nRcA.jpg" alt="3" style="zoom:50%;" />
