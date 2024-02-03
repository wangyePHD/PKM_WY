---
id: vvte49j8p4ai19tbr7xv1x6
title: >-
  Mix-of-Show: Decentralized Low-Rank Adaptation for Multi-Concept Customization
  of Diffusion Models
desc: ''
updated: 1706941926254
created: 1706939844514
---

## In a word

![图 3](images/fc62bbcc8a141ba46903b4f08c8d3f85773da3ed52bc7968b998af59741c9c36.png)  

本文是发表在NIPS 2023的一篇关于**多概念定制化**的工作。主要团队来自于腾讯和新国大。核心思想是提出了高效融合多个LoRA tuned的single concpet model，来实现多个概念的组合定制化生成。


## Motivation

现阶段多概念定制化生成的主要问题有以下两个：
* **概念矛盾**：指的是多个概念的学习会出现互相矛盾的情况。
* **身份丢失**：当多个概念进行融合的时候，往往会丢失某些concept。

本文分别从上述两个问题出发，提出了一种新的多概念定制化方法——Mix-of-Show。


## Method

首先作者团队分析了，text token embedding和LoRA weights在概念学习上的不同倾向。如下图所示：

![图 4](images/f178334b04ed3de779f1c4908f1c148370e57a4139019604205edb644e060f7c.png)  

相关结论如下：
* 根据a，b列，可以发现Textual Inversion和P+的token embeding倾向于学习in-domain的concept，而对于没见过的concepts，则无能为力。
* 根据c，d列，可以发现token embedding仅能补货域内的concept，当配合使用LoRA weights时，可以补充学习out-of-domain的concept。这说明，LoRA本质上还是学到了concept identity。
* 根据e列，当多个concept的LoRA进行融合的时候，往往会出现concept identity的丢失。

根据上述观察，作者提出了几个改进的措施：

![图 5](images/5b65cfb2549c44c5bb2316c57ebf55f035f6adeadf3def4c8f8530f00fba89d7.png)  

![图 6](images/408c7372c0e3fa5f7a5aba78dadc8f23584f2807a853606f7ac6164c1a109e21.png)  


* **embedding decomposed LoRA (ED-LoRA)**：其实这个点核心就是利用了P+的思路，使用多个embedding注入，增强embedding的表达能力。
* **Gradient Fusion**：相比如传统的加权融合，梯度融合可以更好地保留不同concept的特征。
* **regionally controllable sampling**：这个trick的目的是避免属性绑定错误或者是丢失一些物体。核心就是利用物体的mask，重构cross-attention map。


## Results


![图 0](images/dae666345948e3eeb14e73d07b7a5743145e8c680735ee8d3ea14b289d12336e.png)  

![图 1](images/0fbe745dfba649451b46e9a97a8f45af3e24069a8c423329d4fe59c33b9610f0.png)  

![图 2](images/2cfe92592a097f720b727bf44a63cdd2e776aa13336692a49eeed7fdb4260bed.png)  


## Related Work

* CONES V2
* Custom-Diffusion
* SVDiff


## Tags

#paper_idea
#定制化
#多概念