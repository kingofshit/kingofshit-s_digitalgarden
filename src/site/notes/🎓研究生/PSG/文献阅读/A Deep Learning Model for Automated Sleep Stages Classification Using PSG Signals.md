---
{"dg-publish":true,"permalink":"/🎓研究生/PSG/文献阅读/A Deep Learning Model for Automated Sleep Stages Classification Using PSG Signals/","dgPassFrontmatter":true}
---


# 文献信息
## DOI
10.3390/ijerph16040599

## 标题
A Deep Learning Model for Automated Sleep Stages Classification Using PSG Signals

## 作者
Ozal Yildirim, Ulas Baloglu, U Acharya

## 时间
2019-02-19

## 摘要
Sleep disorder is a symptom of many neurological diseases that may signiﬁcantly affect the quality of daily life. Traditional methods are time-consuming and involve the manual scoring of polysomnogram (PSG) signals obtained in a laboratory environment. However, the automated monitoring of sleep stages can help detect neurological disorders accurately as well. In this study, a ﬂexible deep learning model is proposed using raw PSG signals. A one-dimensional convolutional neural network (1D-CNN) is developed using electroencephalogram (EEG) and electrooculogram (EOG) signals for the classiﬁcation of sleep stages. The performance of the system is evaluated using two public databases (sleep-edf and sleep-edfx). The developed model yielded the highest accuracies of 98.06%, 94.64%, 92.36%, 91.22%, and 91.00% for two to six sleep classes, respectively, using the sleep-edf database. Further, the proposed model obtained the highest accuracies of 97.62%, 94.34%, 92.33%, 90.98%, and 89.54%, respectively for the same two to six sleep classes using the sleep-edfx dataset. The developed deep learning model is ready for clinical usage, and can be tested with big PSG data.

# 注释


[Yildirim 等 - 2019 - A Deep Learning Model for Automated Sleep Stages C.pdf](zotero://open-pdf/library/items/WCYEZGWT?page=1&annotation=IFNDH4NI)

## 利用脑电图（EEG）和脑电图（EOG）信号开发了一维卷积神经网络（1D-CNN），用于对睡眠阶段进行分类。
A one-dimensional convolutional neural network (1D-CNN) is developed using electroencephalogram (EEG) and electrooculogram (EOG) signals for the classification of sleep stages.
[Yildirim 等 - 2019 - A Deep Learning Model for Automated Sleep Stages C.pdf](zotero://open-pdf/library/items/WCYEZGWT?page=1&annotation=6X4P48UA)

## 使用两个公共数据库（sleep-edf 和 sleep-edfx）对该系统的性能进行了评估
The performance of the system is evaluated using two public databases (sleep-edf and sleep-edfx)
[Yildirim 等 - 2019 - A Deep Learning Model for Automated Sleep Stages C.pdf](zotero://open-pdf/library/items/WCYEZGWT?page=1&annotation=MTMCFULU)

## 分期标准：W, NREM(S1-S4), REM
The main criteria for this process are based on the guidelines that were first proposed by Rechtschaffen and Kales (R&K) [5], and later developed by the American Academy of Sleep Medicine (AASM) [6]
[Yildirim 等 - 2019 - A Deep Learning Model for Automated Sleep Stages C.pdf](zotero://open-pdf/library/items/WCYEZGWT?page=1&annotation=T7QAAU9U)

## 根据 AASM 指南，S3 和 S4 阶段由慢波睡眠（SWS）这一单一类别表示。唤醒睡眠阶段被定义为受试者在睡眠前被唤醒的等级。NREM S1 是睡眠的第一阶段，此时大脑活动减慢，肌肉放松。S2 阶段是真正睡眠阶段开始的阶段，眼球运动在此阶段停止。S3 阶段被称为深度睡眠，因为受试者的大脑功能明显减弱。深度睡眠活动在 NREM S4 睡眠阶段继续进行。在快速眼动阶段，眼睛是闭着的，但也会快速移动[7]。
According to the AASM guidelines, the S3 and S4 stages are represented by a single class as slow-wave sleep (SWS). The wake sleep stage is defined as the class of awakening of the subject before the sleep. NREM S1 is the first stage of a sleep where the brain activity slows down, and muscles are relaxed. Stage S2 is the stage where the actual sleep phase begins, and the eye movements stop in this stage. Stage S3 is called deep sleep, because the brain function of the subject is significantly reduced. Deep sleep activity continues in the NREM S4 sleep stage. Eyes are closed in the REM stage, but they also move rapidly [7].
[Yildirim 等 - 2019 - A Deep Learning Model for Automated Sleep Stages C.pdf](zotero://open-pdf/library/items/WCYEZGWT?page=2&annotation=2KX29PK4)

## 本研究提出了一种基于一维卷积神经网络（1D-CNN）的新型深度学习模型，用于自动进行睡眠阶段分类。该模型有助于构建端到端结构，在使用原始 PSG 信号进行睡眠阶段识别时，无需使用手工制作的特征。这项研究最重要的贡献之一是，所提出的深度模型无需改变任何层参数，即可用于 2 到 6 个睡眠类别和其他类型的 PSG 信号。因此，我们的模型非常灵活，而且是利用文献中两个流行的睡眠数据库开发的。
In this study, a new deep learning model based on a one-dimensional convolutional neural network (1D-CNN) is proposed for automated sleep stage classification. This model helps construct an end-to-end structure where no handcrafted feature is used for sleep stage recognition with raw PSG signals. One of the most important contributions of the study is that the proposed deep model can be used without changing any of its layer parameters for two to six sleep classes and other types of PSG signals. Hence, our model is flexible and developed using two popular sleep databases that are available in the literature.
[Yildirim 等 - 2019 - A Deep Learning Model for Automated Sleep Stages C.pdf](zotero://open-pdf/library/items/WCYEZGWT?page=3&annotation=263RCW5P)

## 在未来的研究中，我们将使用不同的睡眠数据库对所提出的模型进行测试。在本研究中，我们根据信号级标准对模型的性能进行了评估。在未来的工作中，我们将使用患者级别的标准来评估模型的性能。此外，通过使用不同的深度学习方法（如 CNN 和 LSTM 的组合）来提高识别性能也是一个进一步的目标。
In future studies, the proposed model will be tested using different sleep databases. In this study, we have evaluated the performance of the model based on signal-level criteria. We will use patient-level criteria to evaluate the performances of the model for the future works. Furthermore, it increasing the recognition performance by using different deep learning approaches such as a combination of CNN and LSTM can be a further aim.
[Yildirim 等 - 2019 - A Deep Learning Model for Automated Sleep Stages C.pdf](zotero://open-pdf/library/items/WCYEZGWT?page=18&annotation=EQ5ZEEHY)





