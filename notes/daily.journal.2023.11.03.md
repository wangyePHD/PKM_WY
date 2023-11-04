---
id: obje0575ri15do307hv0hc5
title: '2023-11-03'
desc: ''
updated: 1699017902330
created: 1698977247357
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
- [ ]  今日实验安排、推进、总结实验现象

### <font color=#871F78>**不重要紧急**</font>

- [ ] 学院填表，学业奖学金，下午完成，晚上送过去



### <font color=blue>**重要不紧急**</font>

- [ ] 


### <font color=green>**不重要不紧急**</font>

- [ ] 



## **工作笔记**
* 实验安排： 
  * **mask掉背景的狗子图像，训练in the style of *s**
  * **mask掉背景的狗子图像，训练in the style of *s+Mask Loss实验**
    * in the style这个引导词不太合适，换成color重新跑了实验
    * 不能加Mask Loss，这个损失函数太hard，他会把shape也保存下来
    * 外观信息解耦的不好，当我改变dog--》sheep后者其他动物的时候，texture会被改变。
  * 测试多样性较差的原因
    * 今天我通过各种测试，观察到的一现象是，推理shape还是要保持背景图像的存在，如果没有背景图像，就会过拟合，造成editing能力变差。
    * 数据的复杂程度
      * 可能和背景图像有关系，  
    * mask loss训练的权重影响
      * 没啥关系
    * 还有一个关键的点：weight offset，我们训练得到的weight offset与mask绑定的太严重了。如果有多个weight offset，一个来和mask绑定，另外一个保持原始的多样性
    * ~~另外一个点，就是E4T在domain-tuning的时候需要微调全部的UNet参数。很奇怪，如果只微调部分可能就没那么限制了吧~~
      * ~~研究了一下，还就是需要全部微调，不然效果就不好。~~
  * mask 作为输入 搞个encoder，然后提出S\*mask 和 S\* 的embedding做loss
  * 做多个token
  * 现阶段得实验不合理, 因为你要学shape,但是你用的事原图来提取,这一点不合理.是不是可以用所有视角得mask提特征
* 备忘记录：
  * 之前那个一张图取多个concept的论文，也用了mask-crossattn map的loss，它是如何保持多样性的
* 现在进行的实验
  * in the color of 实验
  * 


## **问题记录**

1.
2.
3.


## **今日总结**

1.
2.
3.
