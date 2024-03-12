---
id: 00f156afmcagb498b6249ac
title: 'MagiCapture: High-Resolution Multi-Concept Portrait Customization'
desc: ''
updated: 1710051911686
created: 1710048499462
---

## In a word

![图 0](images/bf4a724fdc5a128020325bf21cc055eb9b99dedc14a19f9e8eaae13e24d0e439.png)  


文本利用了多阶段的Tuning策略，实现了Subject（人脸）和Style两种概念的组合定制化生成。


## Motivation

* 现有的方法无法实现商业可用级别的高清人脸定制化

这篇论文从这一点出发做了一些尝试。

## Method

![图 1](images/0d9d8c38c8a2a27c4ee3dd726efc74d86efc27b69344310d6f6752596be5f3e6.png)  


本文的方法也比较简单，所使用的Trick都比较常见。方法共分为三个阶段：
* Source-level Tuning
* Reference-level Tuning
* Composed-level Tuning

首先看Source-level Tuning，这个过程很简单，输入多张参考图，然后不断的tuning 去学习[V1]的embedding。这个学习过程中，使用mask来限制噪音compare的loss的约束。

![图 2](images/7281f0725137c0a66599081a902a110c545fd3eda909e534a0d98523ec625519.png)  


接下来是Reference-level Tuning，这个过程主要用来学习style的token表示，也就是[V2]，只不过在这个tuning过程中，作者引入了LoRA。当然也是用mask来约束噪音学习的区域，也就是非人脸区域。

![图 3](images/22e26ecb0318183ec2e87919769763d247895b9b3e030bbcfaa574533d9610b8.png)  


然后就是composed-level Tuning，这个过程就是将两个token表示结合起来，一起学习，因此主要解决的就是二者之间不要耦合。做法比较简单，分别用mask得到人脸区域和style区域，然后分别建立损失即可。


最后就是推理阶段：推理阶段作者也引入了类似于P2P中的cross-attention map操作，也就是用mask来约束map的区域。只不过作者用的思想是：应该令非人脸区域的attention map接近于0，而人脸区域不一定要是1（因为网络传递的过程中，最优的map value不一定是1）这样可以使得推理结果更加准确，减少耦合。


## Insight

如何解决耦合问题？
* 使用Mask来分别限制和区分，训练和推理都用
  
LoRA的作用是什么？
* 不改变模型参数，保留模型的生成能力
* 引入一组小参数，能够学习到更多的细节信息。





## Results

![图 4](images/854d516807bbc8cecfb1c4ebb7a930f981e5cfac4d5667a5cc06b91d64146940.png)  


## Tags
#人脸 #定制化 #多阶段 #耦合 #LoRA