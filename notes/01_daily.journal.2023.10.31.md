---
id: fxo7xyum1delnbfwl34d3jv
title: '2023-10-31'
desc: ''
updated: 1698758655386
created: 1698717520211
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
- [x]  每日论文阅读
- [x]  Contrastive loss实验 测试与分析
- [x]  新实验安排 广度优先
- [ ]  Research Proposal撰写
- [x]  自动化评测脚本

### <font color=#871F78>**不重要紧急**</font>

无


### <font color=blue>**重要不紧急**</font>

- [ ] 昨日未完成的事项
- [ ] 各种文献树的总结
- [ ] 买生活用品

### <font color=green>**不重要不紧急**</font>

无




## **工作笔记**

* **实验安排 2023年10月31日10:29:07：**
  * Mask Loss 0.1 安排实验 5000 training steps
  * CL loss 1.0 安排实验 5000 training steps
* **自动评测脚本的逻辑 2023年10月31日11:04:49：**
  * ~~每训练好一个模型，我们选取其4000 training steps时刻的预训练模型进行测试~~
  * ~~首先，左Domain-tuning，直接手动~~
  * ~~接下来，实现自动inference功能
    * ~~每次生成四张图，不固定种子，生成16次，共得到64张图，每张图命名为grid_时间戳.png~~
    * ~~自动切分功能，每张图切分为4个子图~~
    * ~~原图和重建图之间的CLIP-I相似度计算~~
    * CLIP-T相似度计算，*s直接置为None
* **定量实验结果** 
  * **chair_sofa 重建** 
    * Origin E4T baseline, a *s chair
      * CLIP-I：0.9477310180664062
      * Mask-IoU：0.6183655068264127
    * Shape E4T baseline, a chair in the shape of *s
      * CLIP-I: 0.9472274780273438
      * Mask-IoU: 0.6379574028058812
    * Mask Loss 0.1 a chair in the shape of *s   
      * CLIP-I: 0.9432754516601562
      * Mask-IoU: 0.727747119139064
    * Mask+Contrastive_0.1_0.1 a chair in the shape of *s
      * CLIP-I：0.9278030395507812
      * Mask-IoU: 0.6720695356206112
  * **chair_sofa leopard-print a leopard-print chair(测试text)**
    * Origin E4T baseline
      * CLIP-T: 0.35936737060546875
      * Mask-IoU: 0.5249998903794395
    * Shape E4T baseline
      * CLIP-T：0.3518714904785156
      * Mask-IoU：0.5598146220532607
    * Mask Loss 0.1 
      * CLIP-T: 0.3600959777832031
      * Mask-IoU: 0.6461788913916293
    * Contrastive Loss 1.0
      * CLIP-T：0.3002510070800781
      * Mask-IoU: 0.5989608784344322
    * Contrastive Loss 0.1
      * CLIP-T: 0.3130149841308594
      * Mask-IoU: 0.56978482650736
    * Mask+Contrastive_0.1_0.1
      * CLIP-T: 0.3587226867675781
      * Mask-IoU: 0.5448436822472544



## **问题记录**
* 对比学习的损失为什么没有效果？

## **今日总结**
