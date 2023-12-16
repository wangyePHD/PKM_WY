---
id: f5ctxjqjklfa8z3w2blz13v
title: 写作素材整理
desc: ''
updated: 1702746947521
created: 1702739835674
---

## Title
* ESCDiff：Learning to extract sub-concept for example-driven text to image generation
* Shape and Appearance Inversion for Example-driven Text to Image Generation 



## Related Work
* CONFORM: Contrast is All You Need For High-Fidelity Text-to-Image Diffusion Models
![图 0](assets/images/5a32e883ea29971656ba80be36263319198e685b0d23c104005bd29f66626126.png)  
* PortraitBooth: A Versatile Portrait Model for Fast Identity-preserved Personalization
  * 关于文本提示的缺点
    ![图 1](assets/images/c3bb9835187343b6699a3425d684b4b9ec65ce61768cc15d1ef4299e4837e3d6.png) 

* Compositional Inversion for Stable Diffusion Models
![图 2](assets/images/ab1ffdcbb827ad7fa991eb11142085d82b3d541fae9df79b569256c934209fb9.png)  


* ELITE: Encoding Visual Concepts into Textual Embeddings for Customized Text-to-Image Generation
![图 3](assets/images/97b9e4718e29542408703ebd1a80ba3cec06e773428ab71e1df7efb8416846b6.png)  

* E4T
  * ![图 4](assets/images/9d6512d6888483a7eb6d4d4cbeeaad5b6ac950abc2cc2703d4350b92113dd394.png)  
  * ![图 5](assets/images/cab9da991a04c2d248dddddd12285558c9cdf65c85a0ab2f80556181bee96784.png)  



* 中文粗写

```txt
文本引导的图像生成的发展取得了巨大的成功，早期的文本到图像的生成模型主要是利用基于生成对抗网络的结构，结合CLIP。然而，GANs的训练不稳定容易引起模型坍塌问题，同时GANs受限于结构化的场景例如人脸编辑，并且difficult to train at scale.

最近，基于Diffusion的生成模型成为了SOTA for Text-to-image generation 由于其前所未有的高质量和可控的生成能力。

即使这些方法在文本到图像合成领域取得了显著进展，但是这些方法仅仅利用文本在图像生成时，仍然缺乏细粒度的控制，同时也无法清晰的表述清楚用户真正的意图。

在本文中，我们的目的是希望模型能够从给定的输入参考图中学习用户感兴趣的图像内容，并利用其合成满足用户意图的新的图像，进而消除文本内在的不确定性和模糊性。



```


---

