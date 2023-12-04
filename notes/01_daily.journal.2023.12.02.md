---
id: 1nzatbftdbdeqbrbb9m1wa5
title: '2023-12-02'
desc: ''
updated: 1701524047327
created: 1701450382779
traitIds:
  - journalNote
---
<!--
Based on the journaling method created by Intelligent Change:
- [Intelligent Change: Our Story](https://www.intelligentchange.com/pages/our-story)
- [The Five Minute Journal](https://www.intelligentchange.com/products/the-five-minute-journal)
-->



## **工作笔记**
* 本科毕设，图像分割，想一个问题。
* 分割模型，做什么事情
* 一般图像分割，稍微前沿一点，难度不要太大

## **问题记录**


## **今日总结**

实际上，今天所完成的工作包括：
1. 阅读了一篇论文，ADD 一步推理生成图像
2. 对核心事项Appearance Inversion 进行了分析和实验。
   1. 共进行了三组实验，发现一种无心引入错误的实验，居然有了效果。这个实验的核心是给appearance student model输入leopard inference image，然后文本是 a dog in the shape of *a。发现再训练大概300步的时候，有了效果。当然我们目前只finetuning了K，V
   2. 第二个实验是，finetuning k，v，然后文本是*a，输入给appearance student model的是纯噪音，使用DINO-CLS-Loss学习。
   3. 第三个实验是，finetuning k,v，输入文本是a leopard in the appearance of *a. 也就是Custom Diffusion的实现方式。
3. 今天经过验证得到的结论和有效方案：
   1. 之前的方法过拟合很严重，这个是由于finetuning全部Unet的参数导致的。目前改成了finetuning k，v。
   2. 很奇怪为什么实验1是有效的。实验1对cat有效吗？如果只是提供文本 the appearance of *a, 是否就具备了通用性呢？
      1. 经过实验，cat也是有效的，目前来看这个方式应该是可行的。
      2. 
