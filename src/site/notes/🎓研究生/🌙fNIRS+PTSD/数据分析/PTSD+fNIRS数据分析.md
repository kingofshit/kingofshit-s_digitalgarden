---
{"dg-publish":true,"permalink":"/🎓研究生/🌙fNIRS+PTSD/数据分析/PTSD+fNIRS数据分析/","dgPassFrontmatter":true}
---


# 时间层面分析
## 均值
### 步骤
1. 使用ReadMatRawdata.py读取预处理后mat格式数据，分段计算各通道oxy，dxy，total均值，保存在mean.csv中；
2. 使用ReadCSV_mean.py进行mean.csv读取，生成各通道不同阶段均值图片，并对每个通道每个阶段的均值进行t检验和Mann-Whitney U 检验。
### 结果
#### 未插值前
##### t检验
######  oxy
channel 2 period 2 t 检验:  p value is 0.03790910141082163
channel 3 period 2 t 检验:  p value is 0.02062138400855481
channel 7 period 2 t 检验:  p value is 0.03444607385396066
channel 14 period 2 t 检验:  p value is 0.041233604337232534
channel 15 period 6 t 检验:  p value is 0.002227478549276086
channel 17 period 6 t 检验:  p value is 0.04212406718885562
channel 21 period 6 t 检验:  p value is 0.03404328104028488
channel 22 period 6 t 检验:  p value is 0.0496851466535464
channel 23 period 6 t 检验:  p value is 0.019216676584281965
channel 27 period 2 t 检验:  p value is 0.03835928968349069
channel 27 period 6 t 检验:  p value is 0.03311999306748099
channel 30 period 2 t 检验:  p value is 0.03860225657022345
channel 30 period 6 t 检验:  p value is 0.026976392926827124
channel 31 period 4 t 检验:  p value is 0.036652888373196295
channel 36 period 2 t 检验:  p value is 0.023668786502818354
channel 38 period 4 t 检验:  p value is 0.0040888325325557865
channel 42 period 2 t 检验:  p value is 0.03624116031879717
channel 42 period 4 t 检验:  p value is 0.0156511549018692
channel 43 period 3 t 检验:  p value is 0.01173982323525546
######  dxy
channel 1 period 2 t 检验:  p value is 0.030181145919394112
channel 3 period 2 t 检验:  p value is 0.02031663962241929
channel 6 period 6 t 检验:  p value is 0.012760703193732886
channel 9 period 2 t 检验:  p value is 0.035952617211347355
channel 13 period 2 t 检验:  p value is 0.01599857389791225
channel 15 period 2 t 检验:  p value is 0.02547341706138953
channel 15 period 6 t 检验:  p value is 0.010821817124031893
channel 22 period 3 t 检验:  p value is 0.03161566344830526
channel 23 period 6 t 检验:  p value is 0.04665535082511936
channel 26 period 6 t 检验:  p value is 0.04465392145811336
channel 27 period 2 t 检验:  p value is 0.02997373190069803
channel 27 period 6 t 检验:  p value is 0.0062364864252770985
channel 29 period 6 t 检验:  p value is 0.025578640438506512
channel 30 period 2 t 检验:  p value is 0.040707184362616104
channel 31 period 4 t 检验:  p value is 0.031247823252193163
channel 36 period 2 t 检验:  p value is 0.04555032708068024
channel 38 period 4 t 检验:  p value is 0.010804017790800416
channel 42 period 2 t 检验:  p value is 0.04144189044700345
channel 42 period 4 t 检验:  p value is 0.04456650057440199
channel 43 period 3 t 检验:  p value is 0.02098970033938161
######  total
channel 3 period 3 t 检验:  p value is 0.020803648920107616
channel 4 period 1 t 检验:  p value is 0.02973158833769609
channel 6 period 3 t 检验:  p value is 0.03114094411599159
channel 15 period 1 t 检验:  p value is 0.03560783774600178
channel 15 period 6 t 检验:  p value is 0.004645818689643714
channel 16 period 6 t 检验:  p value is 0.04223429515774935
channel 19 period 3 t 检验:  p value is 0.04990011832663225
channel 30 period 2 t 检验:  p value is 0.04811461848060897
channel 35 period 6 t 检验:  p value is 0.01900664086952798
channel 36 period 2 t 检验:  p value is 0.01516526078323693
channel 38 period 4 t 检验:  p value is 0.00473779299917551
channel 39 period 4 t 检验:  p value is 0.03029321757079821
channel 41 period 4 t 检验:  p value is 0.01934833010690204
channel 42 period 2 t 检验:  p value is 0.04716292663636336
channel 42 period 4 t 检验:  p value is 0.013375523566480082
channel 43 period 3 t 检验:  p value is 0.01315817335329052

##### Mann-Whitney U 检验
######  oxy
channel 3 period 2 Mann-Whitney U 检验:  p value is 0.016498739751220317
channel 6 period 6 Mann-Whitney U 检验:  p value is 0.04371314983512984
channel 13 period 2 Mann-Whitney U 检验:  p value is 0.02729580063665383
channel 15 period 6 Mann-Whitney U 检验:  p value is 0.00517611014376219
channel 21 period 6 Mann-Whitney U 检验:  p value is 0.03697151790711806
channel 22 period 3 Mann-Whitney U 检验:  p value is 0.01898852044073278
channel 27 period 6 Mann-Whitney U 检验:  p value is 0.023871134132462366
channel 28 period 6 Mann-Whitney U 检验:  p value is 0.014300411609102613
channel 29 period 6 Mann-Whitney U 检验:  p value is 0.04022268332418644
channel 30 period 6 Mann-Whitney U 检验:  p value is 0.02082553453578386
channel 36 period 6 Mann-Whitney U 检验:  p value is 0.041937191514878555
channel 38 period 4 Mann-Whitney U 检验:  p value is 0.02852789436665721
channel 41 period 4 Mann-Whitney U 检验:  p value is 0.041937191514878555
channel 43 period 3 Mann-Whitney U 检验:  p value is 0.04371314983512984
######  dxy
channel 1 period 2 Mann-Whitney U 检验:  p value is 0.02852789436665721
channel 2 period 2 Mann-Whitney U 检验:  p value is 0.041937191514878555
channel 3 period 2 Mann-Whitney U 检验:  p value is 0.01898852044073278
channel 6 period 6 Mann-Whitney U 检验:  p value is 0.023871134132462366
channel 13 period 2 Mann-Whitney U 检验:  p value is 0.00965007342344554
channel 15 period 6 Mann-Whitney U 检验:  p value is 0.007875304203972543
channel 22 period 3 Mann-Whitney U 检验:  p value is 0.011773050976716442
channel 27 period 6 Mann-Whitney U 检验:  p value is 0.011773050976716442
channel 28 period 6 Mann-Whitney U 检验:  p value is 0.013627347915435236
channel 29 period 6 Mann-Whitney U 检验:  p value is 0.022815572002900245
channel 30 period 6 Mann-Whitney U 检验:  p value is 0.01898852044073278
######  total
channel 3 period 2 Mann-Whitney U 检验:  p value is 0.02729580063665383
channel 3 period 3 Mann-Whitney U 检验:  p value is 0.035431665771366756
channel 12 period 2 Mann-Whitney U 检验:  p value is 0.02610989811320674
channel 15 period 6 Mann-Whitney U 检验:  p value is 0.023871134132462366
channel 21 period 3 Mann-Whitney U 检验:  p value is 0.04942633780618268
channel 24 period 3 Mann-Whitney U 检验:  p value is 0.01812433811278471
channel 31 period 4 Mann-Whitney U 检验:  p value is 0.04371314983512984
channel 35 period 6 Mann-Whitney U 检验:  p value is 0.007480027701157544
channel 36 period 2 Mann-Whitney U 检验:  p value is 0.008722429155736146
channel 36 period 4 Mann-Whitney U 检验:  p value is 0.023871134132462366
channel 36 period 6 Mann-Whitney U 检验:  p value is 0.02852789436665721
channel 38 period 4 Mann-Whitney U 检验:  p value is 0.004905474396981581
channel 39 period 4 Mann-Whitney U 检验:  p value is 0.035431665771366756
channel 41 period 4 Mann-Whitney U 检验:  p value is 0.011773050976716442
channel 42 period 4 Mann-Whitney U 检验:  p value is 0.04555220949929296
#### 插值后
##### t检验
######  oxy
channel 2 period 2 t 检验:  p value is 0.03790910141082163
channel 3 period 2 t 检验:  p value is 0.02062138400855481
channel 7 period 2 t 检验:  p value is 0.03444607385396066
channel 14 period 2 t 检验:  p value is 0.041233604337232534
channel 15 period 3 t 检验:  p value is 0.04925639690408461
channel 15 period 6 t 检验:  p value is 0.002227478549276086
channel 17 period 6 t 检验:  p value is 0.04212406718885562
channel 21 period 1 t 检验:  p value is 0.03170763571663881
channel 21 period 6 t 检验:  p value is 0.03404328104028488
channel 22 period 6 t 检验:  p value is 0.0496851466535464
channel 23 period 6 t 检验:  p value is 0.019216676584281965
channel 24 period 1 t 检验:  p value is 0.03993232934018984
channel 24 period 2 t 检验:  p value is 0.01830440764813265
channel 27 period 2 t 检验:  p value is 0.03835928968349069
channel 27 period 6 t 检验:  p value is 0.03311999306748099
channel 28 period 1 t 检验:  p value is 0.027624768580393772
channel 30 period 2 t 检验:  p value is 0.03860225657022345
channel 30 period 6 t 检验:  p value is 0.026976392926827124
channel 31 period 4 t 检验:  p value is 0.036652888373196295
channel 36 period 2 t 检验:  p value is 0.023668786502818354
channel 38 period 4 t 检验:  p value is 0.0040888325325557865
channel 42 period 2 t 检验:  p value is 0.03624116031879717
channel 42 period 4 t 检验:  p value is 0.0156511549018692
channel 43 period 3 t 检验:  p value is 0.01173982323525546
######  dxy
######  total
##### Mann-Whitney U 检验
######  oxy
######  dxy
######  total
## 一般线性模型
### 原理
### 特征提取步骤
- design_inf更新
	- 将Onset_and_Length.xlsx中对应信息填入design_inf.xlsx
	- 更新HC_Design_Inf.mat和PTSD_Design_Inf.mat
- 生成对应beta值：Task fNIRS——Individual-level Analysis
### 分析

# 空间层面分析
## 功能连接
## ALFF