---
id: jm4lc0b4le3cl9qpcxcqvxi
title: '2023-12-07'
desc: ''
updated: 1701970561947
created: 1701924645411
traitIds:
  - journalNote
---
<!--
Based on the journaling method created by Intelligent Change:
- [Intelligent Change: Our Story](https://www.intelligentchange.com/pages/our-story)
- [The Five Minute Journal](https://www.intelligentchange.com/products/the-five-minute-journal)
-->



## **工作笔记**
* 进行大规模的case测试环节，摸清楚现在方法的局限在哪里，重建损失
  * **我在这里采用了多个prompt，然后每次随机一次, 这一点是有效的。**
    * 感觉还可以继续设计更多的prompt
* MagicAnimate 中提到的Appearance Encoder设计
  * MasaCtrl中得KV 操作
* 比较一下，前后KV的更新范围分布
  * 尝试了一下，有一些效果


* 现在我们都是基于噪音的MSE Loss进行监督学习的。然后关于
  * inference 图的纹理图
    * 重建的话，倾向于生成背景为纹理的图。而不会施加到前景物体上。
    * DINO Loss，也不行。生成了一大堆不知道什么东西的图
  * DINO Loss训练
    * 有一些效果，但是不明显，而且会导致生成的图像有些过模糊。
  * DINO + CLIP Loss训练
    * 空白图加噪，然后输入目标文本，比如a dog in the appearance of *a, *a父类注入embedding，student model解码输出一张图，这张图可以计算和文本的CLIP loss，同时计算和目标图的DINO Loss
      * finetuning全部的Unet参数
        * 不行，还是会生成一张纹理图，并且单独用CLIP Loss没用。
  * 输入inference的纹理图，使用a photo in the style of *a.
    * 2023年12月8日01:35:50现在测的结果，啥也不是。

## **问题记录**


## **今日总结**

