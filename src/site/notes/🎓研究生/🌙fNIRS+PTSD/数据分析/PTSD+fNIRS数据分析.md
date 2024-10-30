---
{"dg-publish":true,"permalink":"/🎓研究生/🌙fNIRS+PTSD/数据分析/PTSD+fNIRS数据分析/","dgPassFrontmatter":true}
---

# 脑区划分
## 48通道fNIRS排布图
![48ch.png](https://s2.loli.net/2023/12/04/2YwmNPJ4D97MoWx.png)
## 10-10标准导联
1. 找出四个标志点nasion (鼻根，Nz), inion (枕骨隆起，Iz), 左侧（LPA）和右侧（RPA）耳前凹；Nz—Iz连线和LPA—RPA连线的交点即为Cz电极；
2. 沿着Nz—Iz连线，从前向后按照10%的距离，依次放置电极：Fpz, AFz, Fz, FCz, Cz, CPz, Pz, POz, Oz；
3. 沿着LPA—RPA连线，从左到右按照10%的距离，依次放置电极：T7, C5, C3,C1,Cz,C2,C4,C6,T8;
4. 从Fpz—T7—Oz画出一条线，从前向后按照10%的距离，依次可以放置电极：Fp1, AF7, F7, FT7, T7, TP7, P7, PO7, O1；同样，在右侧可确定电极为：Fp2, AF8, F8, FT8, T8, TP8, P8, PO8, O2；
5. 对于FT7-FCz-FT8连线, FT-FCz距离对半分，可以确定FC3的位置，FCz-FT8对半分，可以确定FC4位置；再在两两电极中间等距离放置一个电极，最终可以确定FC5，FC6电极，即从左到右电极依次为：FT7-FC5-FC3-FC1-FCz-FC2-FC4-FC6-FT8；按照同样的方法，对于T7-Cz-T8连线,TP7-CPz-TP8连线, P7-Pz-P8连线,AF7-AFz-AF8连线，PO7-POz-PO8连线，也可确定相应的电极位置；
6. 图2中黑色的电极表示传统10-20导联中的21个电极；因此，可以说10-10导联系统是传统10-20系统的扩展。

![10-10.jpg](https://pic3.zhimg.com/v2-8a721f9f859161ed891b8cae0302b92a_r.jpg)
## 前额叶划分
[Prefrontal Cortex (gyrus)细致划分 - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/36838023)
### 文献：What constitutes the prefrontal cortex?
对人类和动物的研究表明，大脑额叶区域在认知中发挥着核心作用。注意力、工作记忆和决策是前额皮质的常见认知功能。
- Many neuroimaging studies focus on functional localization and division of the human prefrontal cortex. The subdivisions and their extent vary, but dorsolateral, dorsomedial, ventromedial, and orbital prefrontal cortex are common functional divisions
	- 许多神经影像学研究重点关注人类前额叶皮层的功能定位和划分。细分及其范围各不相同，但背外侧、背内侧、腹内侧和眶前额叶皮层是常见的功能划分
![](https://www.science.org/cms/10.1126/science.aan8868/asset/4f89ec83-b01f-456c-884a-e81e31649aed/assets/graphic/358_478_f3.jpeg)
## 所有 fNIRS 通道的位置（使用 EasyToPo 工具箱从头皮投影到皮质表面）
### 通道对应关系
左边为mni48ch_nihe.csv从上到下序号，右边为对应的真实通道号

### mni坐标
[大话脑成像之十三：浅谈标准空间模板和空间变换 - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/35662026)
[MniTalairach - MRC CBU Imaging Wiki (cam.ac.uk)](https://imaging.mrc-cbu.cam.ac.uk/imaging/MniTalairach)
### easytopo自带坐标
![image.png](https://s2.loli.net/2024/01/17/6zZpONQTGtMP23e.png)
### 椭圆拟合
- z=11：
	- h = -3;
	- k =-10;
	- a = 70; 
	- b = 82;
- z=32：
	- h = -3;
	- k =-15;
	- a = 68; 
	- b = 77;
- z=54：
	- h = -2;
	- k =-15;
	- a = 62; 
	- b = 62;
- z=-8:
- 
- z=71:
	- h = -2;
	- k =-15;
	- a = 45; 
	- b = 45;

### 文献：Functional near-infrared spectroscopy brain imaging predicts symptom severity in youth exposed to traumatic stress

![屏幕截图 2024-01-16 141030.png](https://s2.loli.net/2024/01/16/9mjcODos1fapbP4.png)

- 结果与成人 PTSS 的 fMRI 和 fNIRS 研究结果一致，显示 dlPFC 和 vlPFC 响应负面情绪刺激而激活增加。随后的预测分析揭示了十个特征（即来自八个额皮质 fNIRS 通道的皮质反应、年龄和性别）与 PTSS 严重程度密切相关（r = 0.65，p < .001）。
- Results were consistent with findings from adult fMRI and fNIRS studies of PTSS showing increased activation in the dlPFC and vlPFC in response to negative emotion stimuli. Subsequent prediction analysis revealed ten features (i.e., cortical responses from eight frontocortical fNIRS channels, age and sex) strongly correlated with PTSS severity (r = 0.65, p < .001).
# 时间层面分析
## 步骤
### 统一步骤
1. 修改被试列表：PTSDsub_list.csv、HCsub_list.csv
2. 读取原始数据：
   1. ReadMatRawdata.py，生成mean.csv、integral.csv、variance.csv、skewness.csv、kurtosis.csv
   2. ReadMatGLM.py，生成GLM.csv
3. 插值：chazhi.py，生成mean_chazhi.csv、integral_chazhi.csv等
4. 进入特征文件夹（如01mean），依次运行ReadCSV_mean、ReadCSV_channel_result.py、ReadCSV_roi_result.py
5. 结果保存至特征文件夹result子文件夹中
6. 参数保存至fNIRS_Py-参数子文件夹中
### 均值
1. 使用ReadMatRawdata.py读取预处理后mat格式数据，分段计算各通道oxy，dxy，total均值，保存在mean.csv中。
2. 使用chazhi.py进行缺失值填补，生成mean_chazhi.csv。
3. 组间：使用ReadCSV_mean.py进行mean_chazhi.csv读取，并对每个通道每个阶段的均值进行Shapiro-Wilk 测试判断是否符合正态分布，符合正态分布进行方差齐性检验和独立样本 t 检验，否则进行Mann-Whitney U 检验。
4. 不同任务阶段之间：使用ReadCSV_mean.py进行mean_chazhi.csv读取，并对每个通道不同阶段的均值进行Shapiro-Wilk 测试判断是否符合正态分布，随后进行配对 t 检验和Wilcoxon符号秩检验。
### 积分值
**文献**
- 多任务范式下重度抑郁障碍的fNIRS特征分析与分类研究：4.3.1
将预处理后的数据进行累加（使用最短数据的长度作为累加的长度）
### 标准差
### 偏度
### 峰度
### 一般线性模型
- design_inf更新
	- 将Onset_and_Length.xlsx中对应信息填入design_inf.xlsx
	- 更新HC_Design_Inf.mat和PTSD_Design_Inf.mat
- 生成对应beta值：Task fNIRS——Individual-level Analysis
- ![image.png](https://s2.loli.net/2023/12/05/sEOQU6VMl24mC7H.png)
- 使用ReadMatGLM生成result.xlsx存放在NIRS_KIT_Individual_Analysis文件夹中
- 使用ReadGLM进行result.xlsx读取，并对每个特征进行Shapiro-Wilk 测试判断是否符合正态分布，符合正态分布进行方差齐性检验和独立样本 t 检验，否则进行Mann-Whitney U 检验。
### ALFF&fALFF
![image.png](https://s2.loli.net/2024/01/26/Xb9R6HJSn2LpVIt.png)

## 参数
### 01
- HC：

| "sub01" | "sub02" | "sub03" | "sub04" | "sub05" | "sub06" | "sub07" | "sub08" | "sub09" | "sub10" | "sub11" | "sub12" | "sub13" | "sub14" | "sub15" | "sub16" | "sub17" | "sub18" | "sub19" | "sub20" | "sub21" | "sub22" | "sub23" | "sub24" | "sub25" | "sub26" | "sub27" | "sub28" | "sub29" | "sub30" | "sub31" | "sub32" | "sub33" | "sub34" | "sub35" | "sub36" | "sub37" | "sub38" | "sub39" | "sub40" | "sub41" | "sub42" | "sub43" | "sub44" |
|---------|---------|---------|---------|---------|---------|---------|---------|---------|---------|---------|---------|---------|---------|---------|---------|---------|---------|---------|---------|---------|---------|---------|---------|---------|---------|---------|---------|---------|---------|---------|---------|---------|---------|---------|---------|---------|---------|---------|---------|---------|---------|---------|---------|
| 004     | 005     | 021     | 022     | 023     | 024     | 025     | 026     | 027     | 028     | 029     | 031     | 032     | 033     | 034     | 035     | 037     | 038     | 039     | 040     | 041     | 042     | 043     | 044     | 045     | 057     | 058     | 067     | 068     | 069     | 070     | 071     | 072     | 073     | 074     | 075     | 076     | 077     | 078     | 079     | 080     | 081     | 082     | 083     |
- PTSD：

| "sub01" | "sub02" | "sub03" | "sub04" | "sub05" | "sub06" | "sub07" | "sub08" | "sub09" | "sub10" | "sub11" | "sub12" | "sub13" | "sub14" | "sub15" | "sub16" | "sub17" | "sub18" | "sub19" | "sub20" | "sub21" | "sub22" | "sub23" | "sub24" | "sub25" | "sub26" | "sub27" | "sub28" | "sub29" | "sub30" | "sub31" |
|---------|---------|---------|---------|---------|---------|---------|---------|---------|---------|---------|---------|---------|---------|---------|---------|---------|---------|---------|---------|---------|---------|---------|---------|---------|---------|---------|---------|---------|---------|---------|
| 006     | 007     | 008     | 009     | 010     | 011     | 013     | 015     | 016     | 017     | 018     | 019     | 020     | 046     | 047     | 048     | 049     | 051     | 053     | 054     | 055     | 056     | 059     | 060     | 061     | 062     | 063     | 064     | 065     | 084     | 085     |


- roi：

| Pre-Motor and Supplementary Motor Cortex | Dorsolateral prefrontal cortex | Frontopolar area | Orbitofrontal area | Middle Temporal gyrus | Superior Temporal Gyrus | Temporopolar area | Subcentral area | pars opercularis_ part of Broca's area | pars triangularis Broca's area | Dorsolateral prefrontal cortex2 | Inferior prefrontal gyrus | Retrosubicular area |
|------------------------------------------|--------------------------------|------------------|--------------------|-----------------------|-------------------------|-------------------|-----------------|----------------------------------------|--------------------------------|---------------------------------|---------------------------|---------------------|
| 19                                       | 42                             | 8                | 7                  | 1                     | 18                      | 3                 | 20              | 46                                     | 5                              | 10                              | 4                         | 17                  |
| 38                                       | 44                             | 25               | 9                  | 2                     | 35                      | 12                | 36              | 47                                     | 22                             | 21                              | 6                         | 34                  |
| 48                                       |                                | 26               | 11                 | 13                    |                         | 14                |                 |                                        | 24                             | 23                              |                           |                     |
|                                          |                                | 27               |                    | 15                    |                         |                   |                 |                                        | 31                             | 29                              |                           |                     |
|                                          |                                | 28               |                    | 16                    |                         |                   |                 |                                        | 32                             | 30                              |                           |                     |
|                                          |                                |                  |                    | 33                    |                         |                   |                 |                                        | 37                             | 40                              |                           |                     |
|                                          |                                |                  |                    |                       |                         |                   |                 |                                        | 39                             | 41                              |                           |                     |
|                                          |                                |                  |                    |                       |                         |                   |                 |                                        |                                | 43                              |                           |                     |
|                                          |                                |                  |                    |                       |                         |                   |                 |                                        |                                | 45                              |                           |                     |


## 结果
### 01
#### 均值结果
| 分通道结果 |  |  |  |
| ---- | ---- | ---- | ---- |
| 任务间总显著性 |  |  |  |
| 类别 | 配对t检验显著 | 配对t检验显著且正态 | Wilcoxon符号秩检验显著 |
| PSTD | 125 | 13 | 232 |
| HC | 384 | 9 | 419 |
| 组间总显著性 |  |  |  |
| PSTD+HC | 43 | 2 | 33 |

| 分脑区结果 |  |  |  |
| ---- | ---- | ---- | ---- |
| 任务间总显著性 |  |  |  |
| 类别 | 配对t检验显著 | 配对t检验显著且正态 | Wilcoxon符号秩检验显著 |
| PSTD | 33 | 2 | 60 |
| HC | 155 | 15 | 177 |
| 组间总显著性 |  |  |  |
| PSTD+HC | 12 | 1 | 12 |
#### 积分值结果

| 分通道结果 |  |  |  |
| ---- | ---- | ---- | ---- |
| 任务间总显著性 |  |  |  |
| 类别 | 配对t检验显著 | 配对t检验显著且正态 | Wilcoxon符号秩检验显著 |
| PSTD | 152 | 19 | 233 |
| HC | 381 | 18 | 389 |
| 组间总显著性 |  |  |  |
| PSTD+HC | 53 | 7 | 40 |

| 分脑区结果 |  |  |  |
| ---- | ---- | ---- | ---- |
| 任务间总显著性 |  |  |  |
| 类别 | 配对t检验显著 | 配对t检验显著且正态 | Wilcoxon符号秩检验显著 |
| PSTD | 36 | 0 | 59 |
| HC | 135 | 8 | 151 |
| 组间总显著性 |  |  |  |
| PSTD+HC | 13 | 1 | 11 |
# 空间层面分析
## 绘制2d地形图（以均值为例）
### HC
![057.png](https://s2.loli.net/2023/12/14/AvC8omN9p73R1JG.png)

![057.png](https://s2.loli.net/2023/12/14/yYnJfE1p9TxkPaA.png)

### PTSD
![054.png](https://s2.loli.net/2023/12/14/IH91ok3WntOqVPr.png)

![054.png](https://s2.loli.net/2023/12/14/GtIKJ24RclSLTio.png)

## 功能连接
### 步骤
参考：Early screening model for mild cognitive impairment based on resting-state functional connectivity: a functional near-infrared spectroscopy study

1. 计算皮尔逊相关系数以确定每对测量通道之间的功能连接。因此，将为每个参与者生成一个 71 × 71 的相关矩阵。随后，应用 Fisher 的 r 到 z 变换将这些相关系数转换为 z 分数，以提高正态性。
2. 从三个角度观察功能连接的变化：全脑平均、基于感兴趣区域（ROI）和基于通道。在ROI分析中，71个测量通道根据其位置分为9个脑区（见表2），包括左前额叶（LPF）、右前额叶（RPF）、左颞叶（LT）、上顶叶（ P）、右颞叶（RT）、左下顶叶（LIP）、右下顶叶（RIP）、左枕叶（LO）和右枕叶（RO）。然后对九个 ROI 内部通道的时间序列进行平均，以获得基于 ROI 的 z 分数。
3. 采用双样本 t 检验和错误发现率 (FDR) 校正来比较 MCI 组和 HC 组之间功能连接的差异。 71 个通道为每个受试者构成了 ð71 × 70∕2Þ⁄2485 个无向连接。以基于通道的分析为例，使用未配对的 t 检验来计算这些连接的组间差异，FDR 校正后总共产生 2485 个修改的 p 值。其中p值<0.05被认为是显着差异(*p < 0.05)，而<0.01被认为是极其显着差异(**p < 0.01)。
4. 此外，采用受试者工作特征（ROC）曲线方法来评估这些差异连接的敏感性和特异性。通过 ROC 曲线下面积 (AUC) 来量化这些特征在识别 MCI 方面的表现。
5. 然后，提取具有显着差异的连接作为特征输入到线性判别分析（LDA）进行分类。根据 AUC 值和修改后的 p 值，六个基于 ROI 的 (AUC > 0.65) 和四个基于通道的 (**p < 0.01) 单独或组合参与模型训练。然后报告了 5 倍交叉验证分类精度。33,34 具体来说，62 个 MCI 样本被随机分为训练集和验证集 (4:1) 以及 HC 组。为了减少随机成分的不确定性并提高分类性能的稳定性，上述步骤重复N 1/4 10次并在呈现前取平均值。


### 基于互信息（Mutual Information, MI）
### 基于Pearson相关系数
## 网络指标
D:\\fNIRS_Data\\zishu\\Gretna\\1RESTING\\HC
### Assortativity
ar
r_All_Thres
### Hierarchy
ab
b_All_Thres

### NetworkEfficiency
aEg
Eg_All_Thres
aEloc
Eloc_All_Thres

### RichClub
phi_norm_Thres001-phi_norm_Thres010
phi_real_Thres001-phi_real_Thres010

### SmallWorld
aCp
aGamma
aLambda
aLp
aSigma
Cp_All_Thres
Gamma_All_Thres
Lambda_All_Thres
Lp_All_Thres
Sigma_All_Thres
### Synchronization
as
s_All_Thres
