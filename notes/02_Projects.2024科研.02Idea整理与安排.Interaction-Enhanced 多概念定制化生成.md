---
id: gn9ys5fwuha673at3hncifx
title: Interaction-Enhanced 多概念定制化生成
desc: ''
updated: 1707113099870
created: 1706964526652
---

## 简介

这个想法来自于对多概念定制化论文的观察，我发现这些论文生成的结果中，多个概念之间的交互非常有限，更多的是摆放在特定的位置。因此，我们想提出一种Interaction-enhanced的多概念定制化生成方法，希望在生成的结果中允许概念之间存在简单甚至是复杂的interactions。



## Sub-idea 1: Object-Object之间的Interaction

### 代表工作

* Custom-Diffusion（已读）
* CONES，ICML 2023.03.09，ICML 2023（未看）
* CONES V2，2023.05.30（已读）开源
* Mix-of-Show，2023.05.29 V1，2023.11.10，NIPS 2023（已读）开源

### Limitations

* 我发现CONES V2 和 Mix-of-Show这两个最新的SOTA方法，在多概念的定制化生成的时候，人为的指定了Layout或者Pose或者Canny图作为引导。这样的做法，很大程度上限制了概念之间的Interactions。
* 另外，CONES V2 和 Mix-of-Show这两个方法，都没有考虑到人物之间的Interactions。更多的都是物体或者动物。





## Sub-idea 2: Person-Object之间的Interaction

### 代表工作
* 目前没有发现相关工作






## Sub-idea 3: Person-Person之间的Interaction

### 代表工作
* Fastcomposer（已读），开源
* PortraitBooth（未读），未开源
* Face-diffuser（未读），未开源
* Mix-of-Show，2023.05.29 V1，2023.11.10，NIPS 2023（已读）开源
* Cross Initialization for Personalized Text-to-Image Generation，2023.12.26（未读）未开源
* Orthogonal Adaptation for Modular Customization of Diffusion Models，2023.12.05（未读）未开源
* PhotoMaker: Customizing Realistic Human Photos via Stacked ID Embedding，2023.12.07 （已读） 测试开源，训练未开源
* PhotoVerse: Tuning-Free Image Customization with Text-to-Image Diffusion Models，2023.09.11，未开源
* Taming Encoder for Zero Fine-tuning Image Customization with Text-to-Image Diffusion Models，2023.04.05，未开源
* Subject-Diffusion:Open Domain Personalized Text-to-Image Generation without Test-time Fine-tuning，2023.07.21，训练代码开源
* InstantBooth: Personalized Text-to-Image Generation without Test-Time Finetuning，2023.04.06，未开源

### Limitations

---

## 技术路线


### Baseline 1

最简单的方法，就是利用CONES V2的代码架构，添加一个Interaction Layout生成模块（可以用大语言模型），这样不仅有了物体的bbox，还可以为动词设计一个bbox。然后修改Cross-attention Map。直接生成，观察是否能够实现Interaction的准确生成。 

* 不需要训练，直接作为插件，可以和任意一个多物体定制化模型配合。
* 但是效果可能不会太好


## Baseline 2

直接训练。收集HOI数据，基于FastComposer或者Mix-of-Show、或者CONES V2的架构，设计一个模型，同时进行物体和交互的定制。

目前能想到的点：
* 身份的保持，可以参考PhotoMaker或者InstantID的做法
* Interaction的准确定制该如何做？
  * 参考Revision或者Action定制



