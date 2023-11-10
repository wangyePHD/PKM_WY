---
id: 7sfxffrzl46dj8bch0s72vd
title: Image_Translation
desc: ''
updated: 1699618657963
created: 1699361142764
---

## **Image Translation领域的发展历程**
早期的图像Translation主要关注single domain，后续有了multi-domain translation。但是这些方法对于每一个domain，都需要大量的数据进行训练。因此就出现了这种single-image pairs引导的image translation的工作出现，直到最近CVPR2022上出现Splicing vit features for semantic appearance transfer.后续很多工作都是基于这个方法来做的。
上述是参考[[Research.Paper.Notes.Image_Translation.Diffusion-based Image Translation using Disentangled Style and Content Representation]]




## **Appearance Transfer领域的发展历程**
早期就是用GAN来解，需要收集配对或者非配对的数据进行训练。里程碑式的工作就是Swapping Autoencoder。但是这些方法都需要收集特定领域的数据来训练一个结构复杂的生成器。

后来为了降低上述的难度和要求，就出现了这种使用single exemplar来学习mapping的工作。比如[[Splicing ViT|Research.Paper.Notes.Image_Translation.Splicing ViT Features for Semantic Appearance Transfer]]这篇。 但是这一类的工作主要依赖于DINO-ViT来提取Structure和Appearance的信息，同时在Appearance Transfer的时候，也受限于相对相似的shape。

再后来呢，大家就开始引入Diffusion Model来解。他们的主要做法就是引入一些loss，来帮助Diffusion model朝着保持structure和Transfer Appearance的方向优化。但是这样的方法并没有考虑到图片之间semantic correspondence。

最新的工作就是Daniel组在2023.11.06发表的文章 [[cross-image attention|Research.Paper.Notes.Image_Translation.Cross-Image Attention for Zero-Shot Appearance Transfer]]。

> 注：上述笔记参考论文Cross-Image Attention for Zero-Shot Appearance Transfer 相关工作部分完成。

