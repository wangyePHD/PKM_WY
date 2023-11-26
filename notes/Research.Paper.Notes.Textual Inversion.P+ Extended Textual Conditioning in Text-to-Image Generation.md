---
id: 1xya958rg7k11bfuf11xvhk
title: P+ Extended Textual Conditioning in Text-to-Image Generation
desc: ''
updated: 1700974767021
created: 1700966931897
---

![图 0](assets/images/c2ee737fc00b3977149bcca5b9b267684edd77ad13f32c0f9904b7df3c084899.png)  

## In a word
之前的Textual Inversion技术，比如经典的[[Research.Paper.Notes.Textual Inversion.An Image is Worth One Word Personalizing Text-to-Image Generation using Textual Inversion]]中使用的方式，给定一个字符，利用重建降噪损失不断优化该字符的embedding表示，最终实现利用该字符表示当前图像中的Concept。

与上述技术截然不同的是，P+利用了多个embedding，分别注入UNet的不同层中，实现了多属性的Textual Inversion。

![图 1](assets/images/168004955434f9f709f17593dd2827f7b0da5e574cbb0a1444af2c4082cb7031.png)  



## Motivation

之前的方法，比如Textual Inversion或者Dreambooth，都只能做global concept的inversion，没有办法实现某种子属性或者子概念的inversion。
如何才能实现sub-concept的inversion呢？


## Method

作者的一个最直观的想法就是说：SD中UNet的每一cross-attention layer层在生成过程中扮演的角色是不一样的。 于是作者做了一个简单的实验来验证这一观点：

![图 2](assets/images/4ef6abedaff26605aac938e4a432174ea96d4bcfac8603f74be9038ebc6b55bf.png)  

可以发现，类似于red或者green这样的颜色信息是在fine outer layers生成的，也就是resolution较高的层。而诸如content或者形状都是在coarse inner layers产生的。也就是mid-block的区域。

这一直观的发现，促使作者设计了P+ Space:

![图 3](assets/images/e8ae5808142b6caeca96dc057b1ad283edb7714c86feea2750c9a6e5973e6eef.png)  

那么后续的优化目标和Textual Inversion是一致的，都是在给定Textual 条件下，实现noise的估计。只不过在P+中，需要多个token同时被优化。一旦优化成功，不同的p就学习到了不同的sub-concept。

![图 4](assets/images/4f055d7c01450766d1738783fe2c65dc3b150415fb018d4a76775ef79c1ccf69.png)  


## Insight

![图 5](assets/images/59fd69ced57b658a957ef1a8d1d15db96812ad81c15ec914a74d3e3f104fa064.png)  

其实P+的结论可以从另外一篇文章 [[Research.Paper.Notes.Textual Inversion.An Image is Worth Multiple Words: Multi-attribute Inversion for Constrained Text-to-Image Synthesis]] 中，进一步的体会：

![图 6](assets/images/6f27448f3ca9b7ff44ba4702767a532ed56b2602a3f6edfe72b2a471b6ab703d.png)  

这张图其实不仅从cross-attention layer的角度，还从timestep的角度，协同论述了一下不同的属性是在哪个阶段哪个layer产生关系的。

**object: coarse层**

**pose或者latout：coarse层**

**color 或者 style：moderate层**

（省略timestep阶段）

## Results

和其他方法的对比：

![图 7](assets/images/33304a718efe8bde764ef9b8322af13f35b9679c5618f336e80458911a0fdf13.png)  

子属性的混合：

![图 8](assets/images/7cedc9d432fce934469b025dd9ad2fa75498c2155ad4a489c3d2cd6c40f4a821.png)  


![图 9](assets/images/abeeb8f7009f7d14a26e60fcbe9ae0af4f1ab3fe47ca16bcb56c998b3f960955.png)  



## More

在这里链接一下其他相关的文章：

* [[Research.Paper.Notes.Textual Inversion.An Image is Worth Multiple Words: Multi-attribute Inversion for Constrained Text-to-Image Synthesis]]
* [[Research.Paper.Notes.Textual Inversion.ProSpect: Expanded Conditioning for the Personalization of Attribute-aware Image Generation]]