---
id: 6hffhmkq43ai1nbpauce20b
title: 使用Mask对实验结果的影响
desc: ''
updated: 1698404962672
created: 1698404962673
---


## **实验概述**

此实验是为了验证，使用mask剔除掉背景，仅保留前景物体，进行训练是否有意义。

## **实验代码及训练细节**
https://wandb.ai/wangye889905/shapeinversion_baseline_v2?workspace=user-wangye889905

## **实验结论**

还是保留背景更好一些，如果完全去掉背景（使用mask），则会导致最终的效果有些过拟合，生成的结果也不好。


