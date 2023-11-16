---
id: 9y1i9ix785u9rr4k5m3f4u4
title: Plug-and-Play Diffusion Features for Text-Driven Image-to-Image Translation，CVPR2023 poster
desc: ''
updated: 1699862255511
created: 1699859871989
---

## In a word

本文深入地分析了Stable Diffusion内部representation的作用，提供了关于**如何通过利用内部spatial feature和self-attention机制来控制图像结构不变的insight**。从而实现了不需要训练，便可实现Text-guided Image Translation。

![图 0](assets/images/b01f2ee786eb51371e149ef2c7fca74a3eccf4f0f2424cbbc65e8b836c2a2c31.png)  



## Motivation

作者希望在做Translation的时候，使用原图保持structure，然后文本提供appearance的修改。实现text-guided image2image translation。



## Method

![图 1](assets/images/1bca39e683b51336c4311301dc3461da98ff47a4deb2c7b26aed9711ff610e55.png)  

实际上方法，真的很简单。简单一句话总结，就是构建双路branch，一路用来做原图的DDIM inversion，并从inversion noise的sampling阶段提取spatial feature和self-attention信息，然后注入到下面的分支中。用来保持下面分支的结构。下面的分支接收文本prompt，来修改图像外观信息。



## Insight

![图 2](assets/images/cd15fca06ee8dda171e3771d7355aa2d0b2ea28f29f7db9f6a1a65c74e21f17d.png)  


（1）**spatial features extracted from intermediate decoder layers encode localized semantic information and are less affected by appearance information（Unet的decoder的中间层其实就是ResNetBlock的输出包含了丰富的语义信息，且不容易受到appearance的影响）**


![](assets/images/905b155d9bd4e28cde5f94000dc2865efcf61deff519388400eda177715d1b0f.png) 

（2）**self-attention representing the affinities between the spatial features, allows to retain fine layout and shape details (self-attention描述了空间特征之间的相似程度，因此，可以表示layout和shape信息).**



## Results
![图 4](assets/images/f70823199152b6f8b241f6bf1df7339754e888c146d837c4d8f28cb57a1ceb87.png)  


## More

**简单记录一下我的启发：**

> 实际上这篇论文的创新大吗？解法新吗？ 我不认为解法很新，也不认为创新很大。但是为什么这篇论文能中呢？我认为主要有三点：
* 第一，效果好。
* 第二，论文排版，作图清晰，读起来一气呵成
* 第三，提供了有用的insights。我觉得这个才是最重要的。
* 那我以这个标准来要求自己，只要我的工作能提供这个领域没有的insight，我的效果好，我写的好。ok，我自己就满意了。  


