---
{"dg-publish":true,"permalink":"/🎓研究生/PSG/光照治疗睡眠障碍/光照+EEG数据处理/","dgPassFrontmatter":true}
---


# 预处理
## 时间
2023-07-25 11:15

## 文件
### 原始bdf
第一段
- 全长1768秒
- 11:03.593开始光照（663.593s）

第二段
- 全长1110秒
- 第695.593s结束光照

### eeglab分段
beforeLT：第一段0-660
duringLT：第一段670-1768，第二段0-690
afterLT：第二段700-1110

## 数据截取
beforeLT：T7T8数据噪声较多，截取后602.712s
![Pasted image 20230727152125.png](/img/user/%F0%9F%93%8Cpic/Pasted%20image%2020230727152125.png)
duringLT1：中间有一段时间噪声较大，截取后950.354s
duringLT2：截取后609.018s
afterLT：中间有波动，截取后380.268s
![Pasted image 20230727215143.png](/img/user/%F0%9F%93%8Cpic/Pasted%20image%2020230727215143.png)

## 数据结果说明
xlsx文件中各行表示不同频段，对应频率如下：
- delta1：1-2Hz
- delta2：2-3Hz
- delta：delta1+delta2，即1-3Hz
- theta：3-7Hz
- alpha：7-13Hz
- beta1：13-20Hz
- beta2：20-30Hz
- beta：beta1+beta2，即13-30Hz
- gamma：30-45Hz
energy开头的行代表不同频段的绝对功率，小数代表相对功率