---
id: sreaf4313yjh9jyc7pzf407
title: v0
desc: ''
updated: 1704269283247
created: 1704259424849
---

## Subconcept benchmark V0版本

2024年1月3日13:24:00, 整理好了当前的benchmark v0版本，主要的信息包括：

* Shape Inversion Benchmark
  * 16张图

![图 2](assets/images/0b869cce4ef46e5adbab9cd64d2bc8ea438f0bc7873952a49b932223aa5359c0.png)  


* Appearance Inversion Benchmark
  * 14张图
![图 3](assets/images/32d4250c959b51d6f0cc6c1e2afbc2d879dd3202e7b98842e65d614e5d5e27bf.png)  






## 定量测试

对于每个参考图，测试5个text，每个text生成30张图像。
* shape： 16 \* 5 \* 30 = 2400 张图像
* appearance：14 \* 5 \* 30 = 1800 张图像

采用指标：

* CLIP I-T相似度
* DINO appearance 相似度
* Shape Mask IoU





