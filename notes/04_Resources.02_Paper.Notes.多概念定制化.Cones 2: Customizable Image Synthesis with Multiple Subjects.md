---
id: w5gd627bg9ru0r4u9qbc0t9
title: 'Cones 2: Customizable Image Synthesis with Multiple Subjects'
desc: ''
updated: 1706945416978
created: 1706944778056
---

## In a word

![图 0](images/65bd648bf835556df98b4671a02bfaeddfbb14f813a1b490d969820c93526fdb.png)  

本文是由DAMO研究院推出的一篇关于**多物体概念定制化生成**的工作。其核心是提出了Concept Text token residual embedding的学习方法，同时利用Layout作为约束，实现多物体的概念定制化生成。


## Motivation

在以往的多物体定制化生成研究中，存在以下的limitations：

* 以Custom Diffusion为代表的先驱工作，需要对每一个concept都训练一个模型，这样的话存储开销较大。
* 不同的concept在组合定制的时候，会出现互相干扰的问题。


针对上述问题，作者分别提出了两个对应的trick，详见method。


## Method

![图 1](images/49e9c0c181379568aceee451ed446b10354191e3242db4f658c43453f2e9eef9.png)  

本文的方法非常简单，共有两个设计：
* **Subject Text Token Embedding Residual Learning**：其目的是为每一个subject concept学习一个残差文本embedding，这样的话对于每个concept，都只需要存储仅仅几kb的token residual embedding。存储非常高效。
* **Layout guidance**：这一步的目的是约束多物体生成的位置，防止互相遮挡或者概念丢失。总体来说，就是利用人为指定的layout作为约束，修正cross-attention map。

具体的推理细节：

![图 2](images/892465f29b9c3818ff70762e2d6d67ebf41b5d4d5a401099e3d244c4be97262b.png)  


## Results

![图 3](images/8a8cf571f32b3ef63e6bdaf46e6b5f4a3c7fe47921001cfc73b9b5dfe8ca4085.png)  
![图 4](images/9f11d788ff06dcaeb73704a6cd628214733d109295af7e1dd84266c9481d4bc8.png)  
![图 5](images/926ae7073ef2edd177584d54ebee971786296e8e68d56c065a3d445629b96e59.png)  




## More
[[04_Resources.02_Paper.Notes.多概念定制化.Mix-of-Show: Decentralized Low-Rank Adaptation for Multi-Concept Customization of Diffusion Models]]


## Tags
#定制化  #多概念
