---
id: aljobqvjn3ycmdiui33qzrn
title: contrastive_loss
desc: ''
updated: 1698754701789
created: 1698754232893
---
- [**实验概述**](#实验概述)
- [**实验代码及训练细节**](#实验代码及训练细节)
- [**实验现象总结与分析**](#实验现象总结与分析)
- [**实验结论**](#实验结论)




## **实验概述**
这个实验是验证Contrastive loss在ShapeInversion 是否有效。我们给*s的提前设置了几个positive word，为"structure" "outline" "contour" "silhouette"。负样本我们选择的是当前\*s的embedding和CLIP Token embedding取相似度，相似度最低的1000个token embedding作为负样本。温度设置为0.07，损失权重为0.1。


## **实验代码及训练细节**
wandb实验代码备份和训练细节：[wandb](https://wandb.ai/wangye889905/shapeinversion_baseline_v4_contrastive_loss_idea?workspace=user-wangye889905)


## **实验现象总结与分析**
从定量实验上看，Contrastive loss的效果不好。请看页面[[01_daily.journal.2023.10.31]]


## **实验结论**
对比损失这个idea，我觉得挺好的。但是在shapeinversion上可能不太适用。或者是目前参数设置的有问题。以下是有可能的问题：
  - [ ]  代码是否写错了
  - [ ]  t的影响
  - [ ]  权重的影响
  - [ ]  负样本的空间大小的影响


