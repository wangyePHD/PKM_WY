---
id: m4a63fdru77xlhscm15fuxa
title: 定量评估逻辑jilu
desc: ''
updated: 1705587097448
created: 1705587097448
---



此处记录定量评估逻辑：

* 对reference image全部padding到1：1之后，在进行训练，这样shape不变形
* 对于所有的reference image进行分割，得到mask图像
* 对reference image的mask图像，resize到512*512
* 然后将mask图像的质心移动到512*512的中心
* 对于我们生成的结果，同样做质心移动操作
  * 这样做的目的是，保证每个mask都是在中心，可比较的
* 计算IoU 分数