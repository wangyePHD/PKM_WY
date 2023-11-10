---
id: qikzz351b5vz9ga4wp2rgdo
title: Splicing ViT Features for Semantic Appearance Transfer-CVPR 2022 Oral
desc: ''
updated: 1699533619516
created: 1699425694264
---

## In a word
本文解决的是如何将target图的appearance迁移到source图上，同时保持source图的结构不变。也就是所谓的Appearance Transfer。
![图 0](assets/images/0a2c59ac7e4858d4fcc92d7a58d6ba5a1fb92a2e72728e75f4913fe5e3a14b16.png)  



## Motivation

在之前，基于GAN的方式去做Domain-Transfer或者Image-to-Image Translation, 都需要去收集pair-domain的数据来训练GAN，这样的方法受限于特定的domain。

后续出现了image-to-image translation methods trained on a single example，这种方法利用了low-level的visual information。

Neural Style Transfer（NST）这种方法实际上是利用预训练的网络例如VGG，来编码global-style。

semantic style transfer是将appearance信息，在语义相关的区域上进行transfer。

作者希望解决上述问题，提出了一个pair-example的Appearance Transfer方法。

## Insight

本文最终要的Insight是关于DINO-ViT的：
* DINO-ViT的CLS token representation实际上是对visual appearance的强大表示。不仅包含了纹理信息
* DINO-ViT的deepest layer的输出特征能够提供强大而丰富的semantic information

## Method

![图 1](assets/images/2abc529aedef31d0306078e5459d8dd025947b7a01d5a2d34863ad131779fe18.png)  


本文的方法比较直观。input是[target image，source image]，target image用来提供appearance，source image来提供structure。利用一个生成器，输出一个output图像，包含了原图的structure和target的appearance。

1. 目标图输入DINO-ViT，提取deepest layer的CLS特征，作为Appearance的表达。
2. 原图输入至生成器，生成一张图，也输入至DINO-ViT，同样得到CLS特征，
3. 基于上述特征，直接做Loss，用来监督appearance的一致性。

**Loss appearance如下：**

![图 2](assets/images/3a99ba91d1ce44afb3503ae3c510698c590a4bc061cd923a4bd004703d9cb7b7.png)  


接下来就是structure如何保持的问题了。什么样的representation能表示structure呢？
1. 首先要对局部的texture非常鲁棒
2. 同时能够保存一些布局的信息、形状信息、能够感知物体及其周围的语义信息

作者这边给出的结论是：“直接利用DINO-ViT的Deepest layer spatial feature，其实就是最深一层的输出特征，来计算一个self-similarity矩阵作为structure的表达”。

具体就是取deepest layer的K Matrix，假如图像有20个patch，加上一个CLS，就是21。最终可计算一个21*21的self-similarity 矩阵。用这个矩阵来描述自身的structure信息。

![图 3](assets/images/77d5ed908ea510dce7ea4a40fd07946c9bb482d44b1f2fba7e268b051e0f52d2.png)  

然后，就可以利用上述来约束两张图之间的structure。

![图 4](assets/images/8ec398f6773f5d652a9076e8fdcbffc1b3a3850985ead3594dfbd01f6bb42b31.png)  


## Experiment

作者首先利用实验分析了一下CLS和self-similarity的特点：

![图 5](assets/images/6c30d288283dbb5a1f8208aba9b3d26a748f316184fb696a7a4ffbfa54a504a1.png)  

首先是上图，通过Feature Inversion技术可视化了多层的CLS的特征的可视化结果，可以看到CLS确实关注到了appearance信息。

![图 6](assets/images/ebb23f766a293f65f6347eb01dc45f4247cf1fe1f4ec7f2466a0666ff2634310.png)  

这是利用PCA对self-similarity key matrix进行可视化的结果。可以看到，确实关注到了structure的信息。



接下来看一下消融实验：

![图 7](assets/images/ec90764fa6a21e3e52447831efb298a9b4a739639a7467fdfa5108a71db03006.png)  





## Results

![图 8](assets/images/029212f6028a330de4fe628ad2a5afe36ea813c62685e9ec6c2801d406a4df09.png)  

![图 9](assets/images/bf18c77f81b02ee8ea823bf0822c30510a5ffc6196b3ca30ea38e4a0bdc55467.png)  




## Cons

其实这样的方法是依赖于DINO的，如果DINO在某些数据上的性能不好，那该方法就不work了。




## More

* **Neural Style Transfer**: represents content and an artistic style in the space of deep features encoded by a pre-trained classification CNN model (e.g., VGG). While NST methods have shown a remarkable ability to globally transfer artistic styles, their content/style representations are not suitable for region-based, semantic appearance transfer across objects in two natural images
* **Feature Inversion**: visualization techniques previously used in the context of CNN features


the global token (a.k.a [CLS] token) provides a powerful representation of visual appearance, which captures not only texture information but more global information such as object parts, and 

(ii) the original image can be reconstructed from the deepest features, yet they provide powerful semantic information at high spatial granularity.



