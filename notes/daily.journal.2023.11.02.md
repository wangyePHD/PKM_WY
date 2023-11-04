---
id: 1wesiw4rr6onff97t12gijo
title: '2023-11-02'
desc: ''
updated: 1698924942173
created: 1698891434150
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
- [x]  每日Arxiv
- [ ]  每日论文阅读
- [x]  dog数据上，跑一组shape inversion
- [ ]  改写Color encoder的网络结构，在椅子和dog数据集上分别训练，进行两次实验
- [ ]  晚上十点和马老师开会，准备开会内容

### <font color=#871F78>**不重要紧急**</font>

- [ ] 学业奖学金学院填表 



### <font color=blue>**重要不紧急**</font>


### <font color=green>**不重要不紧急**</font>



## **工作笔记**
* ~~使用SAM进行图像分割的时候，有一些会分割成其他颜色，这个时候，使用mask的时候，请将非0值一律置为1。~~
  *~~ 已经修正了 ~~
* 因为color或者texture这些都属于low-level的特征。我是否需要改变encoder呢？
* 发现了一个数据增强库，https://kornia.readthedocs.io/en/latest/get-started/highlights.html
* 晚上与马老师开会讨论：
  * 现阶段的进展
    * shape inversion的方案
      * E4T的架构
      * in the shape of 引导词的作用
    * 现阶段的结果
      * shapeinversion
        * 能够实现精准的shape反转，能够完美重建原图，支持灵活的编辑。
        * 反转出来的shape不纯，还是包含了一些物体的颜色等信息
        * 可以实现给定example，我们生成example mask一致的结果
      * color inversion
        * 效果不好
        * 监督信号用什么
* 测试结果模糊
  * 由于测试图像分辨率太低，需要高分辨率的图像即可。

## **问题记录**

1.
2.
3.


## **今日总结**

1.
2.
3.
