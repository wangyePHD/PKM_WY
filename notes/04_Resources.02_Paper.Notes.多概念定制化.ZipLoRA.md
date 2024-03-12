#! https://zhuanlan.zhihu.com/p/686535112
---
id: 2nyhs456n7l91di9da9jpmq
title: ZipLoRA
desc: ''
updated: 1710212124273
created: 1710211349493
---

## In a word

![图 0](images/200b96ca67ab1c8512c53018c4d4a6679f7037fddf5f03f40ab68d1ae282815b.png)  

这篇论文通过分析两个LoRA在Merging的时候，出现的问题，通过设计一种以降低两个LoRA权重相似度的方式，来实现给定任意图像subject在任意图像style下的定制化生成。



## Motivation

如何实现Any Subject in Any Style的定制化生成？以前的方法可以分别训练一个Subject LoRA和一个Style LoRA，然后将两个LoRA合并，得到定制化的图像。但是，这种方法存在两个问题：

1. 两个LoRA的权重相似度高，合并的时候会出现矛盾，但是style和content的学习打折扣。
2. 合并两个LoRA的过程需要耗费大量的时间和资源。

因此，作者提出了一种新的方法，通过设计一种以降低两个LoRA权重相似度的方式，来实现给定任意图像subject在任意图像style下的定制化生成。


## Method


![图 1](images/2aa50c1f92118839cadfcf4fc6e2049b218851d8b3125dd8ceaf99a4598a7f6b.png)  

作者先是分析两个insight，即：

1. 如图左所示，作者发现LoRA中大多数的weight的update都是0，这说明影响LoRA或者使得LoRA work的权重只有少部分。
2. 如图右所示，作者发现Content和Style对应的LoRA weight之间，大多数都是高度align的。如果直接merge的话，高度对齐的weight会使得生成的图像质量不好。但是如果降低权重之间的相似度的话，就可以使得生成的图像质量更好。

因此，作者围绕上述两个insight，提出了一种新的方法：

![图 2](images/e525c6b1ceba3d9ce1fcafc9be724fc7e7c56a688ce52c42f1bac0ad1f3c34d3.png)  

作者为两个lora分别创建一个可学习的权重系数，通过广播机制进行相乘。接下来看方法架构图：

![图 3](images/d8d46647f6de4be3069e6a6f5a95ff99995b282ee1004caab2e656117d9d59e3.png)  

![图 4](images/370e5b7902a0f4b8bdb66c97cae7e08ec0d8a1d8d8b7ef2e3a9b215ee7857a81.png)  



## Insight

![图 5](images/6da9994b9697fda931a97d09fd2fdef3af7592fe6bec78e18a1f2635c38872c9.png)  




## Results

![图 6](images/4ef4e4b60cec2ea9617b253cf947e1678c99e6bd03eb468926a416278e5d4588.png)  


## Tags

#多概念定制化