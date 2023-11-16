---
id: s2krp60iyu31h2mqbrhh9xa
title: '2023-11-14'
desc: ''
updated: 1699967331875
created: 1699941191696
traitIds:
  - journalNote
---
<!--
Based on the journaling method created by Intelligent Change:
- [Intelligent Change: Our Story](https://www.intelligentchange.com/pages/our-story)
- [The Five Minute Journal](https://www.intelligentchange.com/products/the-five-minute-journal)
-->



## **待做事项**

### <font color=red>**重要紧急**</font>
- [ ]  每日Arxiv
- [ ]  每日论文阅读
- [ ]  新架构设计
  - [x]  Mask-xattn loss引导下得到得*s embedding，完美的聚合了原始图像的shape和appearance信息。同时E4T baseline1和E4T baseline2，却无法完美的得到shape和appearance，尤其是shape（当然这也是因为这些方法追求效果的多样性，而我们就是要得到一样的shape）
  - [x]  那这样的话，Mask-xattn loss model就可以作为一个完美的Asset model。
  - [x]  接下来，我需要设计子模块，分别从Asset model中学习shape和appearance信息即可。
  - [x]  每个sub-model，都有自己的weight-offset学习模块
  - [x]  监督信息，可以来自以下：
    - [x]  shape+appearance的去噪结果和Asset model的预测结果 MSE
    - [x]  shape 和 appearance之间的差异要大
    - [x]  shape要用mask约束
- [ ]  代码设计
  - [x]  每次实验必须写exp desc
  - [x]  一定要有本地化实验备份代码
  - [ ]  现在是对于shape和inversion的反转我们只提供了一组weight offset
  - [x]  添加新的token，shape用\*m，appearance 用\*a
  - [ ]  domain-tuning 阶段我们还是采用原始的e4t的方式
  - [ ]  text prompt需要两组，一组是teacher用的，另外一组是student用的。
  - [ ]  现在teacher prompt 和 student prompt之间也有gap，因为内容不同。
  - [ ]  shape domain embedding 我们采用mask的embedding进行初始化, 而appearance我们用的是原图的embedding
  - [ ] 对于loss的原则，对于student来说 有真值noise loss，有teacher soft loss，还有e4t其他的loss

### <font color=#871F78>**不重要紧急**</font>

无



### <font color=blue>**重要不紧急**</font>

无


### <font color=green>**不重要不紧急**</font>

无



## **工作笔记**

Inversion 实验日志：



## **问题记录**

1.
2.
3.


## **今日总结**

1.
2.
3.
