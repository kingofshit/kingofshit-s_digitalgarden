---
{"dg-publish":true,"permalink":"/🎓研究生/🌙fNIRS+PTSD/数据分析/PTSD+fNIRS数据预处理/","dgPassFrontmatter":true}
---


使用工具箱[[🎓研究生/近红外/工具/NIRS_KIT\|NIRS_KIT]]

# 数据准备和质量检查 (Data Viewer)
## 数据格式转换 (Data Preparation)
将数据转换成工具包所需格式
1. 选择输入路径（NIRS_KIT_IN）
2. 选择文件类型 type11:homer2OD raw（输入“3 3 3”）
3. 选择2d probe set（probe2d_qiyuan48ch.mat）
4. 选择输出路径（NIRS_KIT_OUT）
5. 点击run（此时在输出路径已生成对应的mat文件）
## 数据剔除
1. 剔除质量差的数据（036：不完整，002数据质量不好后续重测为020）
2. Data Viewer预览预处理的效果
## 数据长度与标记onset获取
- 数据长度获取：GetDataLength.m
- 标记获取：使用homer3导出csv文件
- 将上述信息填写在Onset_and_Length.xlsx文件中，并生成FIRST_0~6、LAST_0~6
## 原始数据裁剪
保留标记前1s至标记后0.5s的数据
1. 生成Crop.mat文件
	1. 更新CropTime.xlsx（从上述Onset_and_Length.xlsx粘贴即可）
	2. 运行xlsx2mat.m（需手动填写被试编号，运行后自动生成Crop.mat）
2. 运行raw_Crop.m（保存至NIRS_KIT_0CROP文件夹）
# 数据预处理 (Preprocessing)
1. 经过[[🎓研究生/🌙fNIRS+PTSD/数据分析/PTSD+fNIRS数据预处理#数据准备和质量检查 (Data Viewer)\|#数据准备和质量检查 (Data Viewer)]]后确定预处理参数
		1. 去趋势
		2. 滤波
		3. 运动伪影矫正
2. 预处理后文件存放至NIRS_KIT_Pre文件夹
![Pasted image 20230720221018.png](/img/user/%F0%9F%93%8Cpic/Pasted%20image%2020230720221018.png)

## 数据分段
根据不同任务对数据进行分段，便于后续处理
1. 建立好分段后存放的文件夹
	- NIRS_KIT_1RESTING
		- HC
		- PTSD
	- NIRS_KIT_2COUNT
		- HC
		- PTSD
	- NIRS_KIT_3SPEAK		
		- HC
		- PTSD
	- NIRS_KIT_4COUNT
		- HC
		- PTSD
	- NIRS_KIT_5LISTEN
		- HC
		- PTSD
	- NIRS_KIT_6COUNT
		- HC
		- PTSD
1. 运行Crop.m
## 数据查看
- 可通过isChannelEmpty.m查看预处理后哪些通道为全0（数据质量差）
- 可通过DrawChannel.m绘制通道信息
## 插值坏导
- 目前是先提取特征，再进行插值
- 将通道及其相邻通道编号存储在chazhi.xlsx中
- 对于数据为空的通道，寻找其附近有数据的通道进行平均插值
- 重复上一步操作至所有通道均有数据



