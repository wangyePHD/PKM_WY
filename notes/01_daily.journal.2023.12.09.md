---
id: 7ngchixj8ayondh2d883h38
title: '2023-12-09'
desc: ''
updated: 1702133374331
created: 1701006786469
traitIds:
  - journalNote
---
<!--
Based on the journaling method created by Intelligent Change:
- [Intelligent Change: Our Story](https://www.intelligentchange.com/pages/our-story)
- [The Five Minute Journal](https://www.intelligentchange.com/products/the-five-minute-journal)
-->



## **工作笔记**

* Appearance的学习，或许可以这样做。我们可以输入噪音给student model，然后我们使用DINO loss，来约束，这样的话，student训练完成，输入*a，就可以生成一张纹理图。
* 第二步，将纹理图应用到目标物体上。
  * 比如我需要生成的文本prompt是a *a dog is sitting on the grass.
  * 我可以先生成一个a dog is sitting on the grass，这一步的目的是，我可以获取到dog的mask。
  * 接下来，基于这个mask，我可以设置双attention架构，原始的架构来理解a dog is sitting on the grass. 另外一个理解*a，设置latents是可以更新的，使得\*a的attention map和dog mask的损失函数，目的就是应用\*a到dog的身上。

结论：
* 上述这种完全依靠textual的方式是不合理的。如果想inversion appearance这个属性，光靠文本来引导，太难了，看看是不是可以引入Image 表征。


基于视觉注入的方式：

* 


## **问题记录**


## **今日总结**

