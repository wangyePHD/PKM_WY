---
id: 426m1eouvrzmuvy9wlsc6vl
title: Subconcept Inversion Summary
desc: ''
updated: 1701095729381
created: 1701060354036
---

## Sub-Concept Inversion工作总结

![图 0](assets/images/6b4f3ceb1324dbe84f4b0314864fa62c6fca2432ff14aaf808895dd039df706d.png)  

> **本次工作总结，共涉及上述三篇文章。**


### **什么是Sub-Concept Inversion?**

对于传统的Textual Inversion来说，给定一张或多张Reference Images，网络需要学习一个token的embedding，从而表示当前的参考图（be like）。**而Sub-Concept Inversion指的是，利用多个token，反转Reference Image中的子属性，主要包括style，color，object，layout等。**


### **现阶段Sub-Concept Inversion的主流工作及技术路线**

目前共包括三篇工作：
* P+: Extended Textual Conditioning in Text-to-Image Generation，2023-07-15
* ProSpect: Expanded Conditioning for the Personalization of Attribute-aware Image Generation，ACM MM 2023
* MATTE：An Image is Worth Multiple Words: Multi-attribute Inversion for Constrained Text-to-Image Synthesis，AAAI2024


三个工作之间的关系如下图所示：

![图 1](assets/images/11788e3b6e8c5a19a908673eb0db815145bbefd24a10b261a5a47d00a750e2bb.png)  

**在Prospect中，该工作认为：**

* the **initial generation stages** of the diffusion model tend to generate **overall layout** and **color**
* the **middle stages** tend to generate **structured appearances**
* the **final stages** tend to generate **detailed textures**

**在P+中，该工作认为：**

* **object: coarse层**

* **pose或者latout：coarse层**

* **color 或者 style：moderate层**


**在MATTE中，一切都被汇总成一张表：**


![图 6](assets/images/6f27448f3ca9b7ff44ba4702767a532ed56b2602a3f6edfe72b2a471b6ab703d.png)  


### **这些方法的详细比较**


![图 2](assets/images/2757df0a47457f4879b8f1fed52e213b0f332eb7f67b8226854c12c99c79b1f5.png)  


### **指标细化**

**MATTE**
* 评估color，style，object inversion的准确度
  * GT怎么来：
    * color的话，直接使用Color Thief提取图像颜色，将得到图像的主要颜色分布
    * object和style的话，采用了在CLIP Image Embedding空间中，查找最近邻
    * louout无法评测，没有GT（这个可能是因为layout的定义本身就不清晰）
  * 评测过程：
    * 对于color，object，style来说，给定一张reference图像，分别对color，object，style反转合成64张图像，这里使用了不同的seed。然后和GT reference图像计算CLIP 图像相似度
    * 还计算了合成的prompt和GT text之间的CLIP文本相似度
    * 还算了一个两个属性之间的解耦程度（略过）

**Prospect**
* CLIP-Image 相似度
  * 生成图像和参考图像之间的CLIP图像相似度，评估content fidelity
* CLIP-Text 相似度
  * 生成图像和textual prompt之间的CLIP图文相似度，评估editability
* User Study

**P+**
* CLIP Text 相似度
  * 生成图像和prompt之间的CLIP相似度
* Subject Similarity
  * 生成图像和原始图像在ViT-S/16 DINO embedding的图像相似度
* User Study



### **这些工作的缺点和问题**

* 无论是按照时间步换分子阶段，还是按照Cross-Attention Layers划分不同的层阶段，都是一个经验性的操作，比较繁琐，同时一旦划分不得当，效果就会很差。
* 对于单张图像的inversion时间还是比较长，目前来看，最快的是P+，在A100的加持下，能够达到15min搞定一张图。我们的方法目前来看，只需要3min左右。
* 这些论文定义的shape和我们定义的shape是不一致的。我们是用mask衡量的。这些工作都还是大致的shape或者structure。







