---
id: v8exbw49e4yl5eldvnj847r
title: '20231120个人会议及进展汇报'
desc: ''
updated: 1700505797020
created: 1700499903898
---

## **汇报大纲**


### **研究进展**
1. 对E4T架构的更深入的认知和理解
   1. 架构分析，pre-training and domain-tuning stages, 分别关注的是什么
      1. pre-training：coarse class learning
      2. domain-tuning: instance learning
   2. E4T本身对于shape和appearance的反转不理想
      1. 我们添加了Xattn-Mask loss，使得更关注center object
      2. 但是我们得到的representation 是 shape和appearance hybrid的

2. 之前的基于mask 和 DINO CLS的embedding MSE策略太hard，没有效果
   1. 画一些简图，分析一下原因

3. 我们现在的解决办法
   1. 基于domain-tuning E4T+Xattn-Mask Loss，我们观察到已经学习到了shape和appearance，令其作为teacher model。
   2. 构建另一个E4T作为Student model
   3. 设计Shape Filter Module，剔除appearance信息
   4. 输入至Student Model，要求其重建mask图像。 
4. 实验结果
   1. 同类实验
      1. dotdog
         1. dalmatian
         2. husky
         3. 德国边牧
      2. 德国边牧
   2. 跨类实验
      1. dotdog
         1. cat
         2. tigger
         3. wolf
      2. 德国边牧
         1. cat
         2. tigger
         3. wolf
   3. 文本引导换背景
   4. 等等
   5. 不同training step下的效果图，所花时间
5. Appearance的解法
   1. self-attention 的KV可以保持appearance 相关论文支撑
   2. teacher的 self-attention KV约束Student self-attention的KV 做loss

### **存在问题**

1. 目前还是一个图像对应一个model，无法一对多
2. 推理时间还是有点长 需要2min