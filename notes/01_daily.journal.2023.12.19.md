---
id: 0w1j0o84z7hu0t89iwfscse
title: '2023-12-19'
desc: ''
updated: 1702968023428
created: 1702952641844
traitIds:
  - journalNote
---
<!--
Based on the journaling method created by Intelligent Change:
- [Intelligent Change: Our Story](https://www.intelligentchange.com/pages/our-story)
- [The Five Minute Journal](https://www.intelligentchange.com/products/the-five-minute-journal)
-->



## **工作笔记**
* 之前的prompt提示是the shape of *m
* 微调downblock，提示a dog in the shape of *m
  * 效果差，只会得到mask一样的cat
* 微调整个unet，提示a dog in the shape of *m
  * 还是只得到白色的mask

目前通过版本回退，已经找到了之前shape inversion work的代码。目前的文件夹name是ShapeInversion。然后之前的appearance Inversion的代码，目前我直接copy出来了，name是ShapeInversion copy。

接下来，我比对差异:

* 单卡训练，我发现work版本也是单卡训练的。所以**不是单卡多卡的问题**
* 对比训练参数
  * 梯度累计有差异，work用的是1，我用的是2
  * batchsize 有差异，work用的是2，我用的1

操，最后发现好像没啥问题。

star 670


## **问题记录**


## **今日总结**

