---
id: lqhjl119ygemlqpxsxyrnzz
title: Introduction
desc: ''
updated: 1704369047811
created: 1704292440737
---


倒推：

* our pipeline的contributions是什么：
  * 我们提供了一个新的，简单的框架，可以实现shape和appearance子属性的学习和定制，仅仅给定一张参考图的情况下。
  * 我们发现图像的子属性和Unet的层级设计有关系。encoder负责shape，decoder负责appearance。
  * 我们提出的方法能够实现来自多个类别的图像的子属性的学习和定制，泛化性很好，定量定性结果行业很好。

* 我们contributions的好处是什么，解决了什么technical challenge
  * 我们的方法只需要一张参考图，就可以实现子属性的定制和学习，以往P+，Inspiration这些方法都需要多张参考图才能实现。
  * 我们的方法非常简单，相比于Prospect，我们不需要人工划分时间步子阶段这样繁杂的操作。我们只需要输入单张参考图，然后分别微调Unet的encoder或者decoder即可。

* 怎么通过写之前的方法引出我们解决了的technical challenge？
  * Inspiration
  * P+
  * Prospect



第一段：
* Text2Image最近取得了很大的进展。
* 定制化生成是Text2Image的热门研究topic，有着广泛的应用。
* 然而，大多数的定制化生成的工作关注的都是整个图像concept的学习和定制，而人们往往只对图像的某种属性感兴趣，例如blue and white porcelain的外观属性或者一栋建筑的形状，这些方法就无法实现图像属性的定制

第二段：
* 我们这篇论文是关注属性-level的图像定制化生成任务。
* 解释：从用户提供的单张参考图中学习感兴趣的图像属性包括shape和appearance，引用teaser图。
* 然而，这个问题是有挑战的。大多数的定制化方法需要多张图像才能学习到图像的concept，而基于单张图像的定制化方法无法实现细粒度的属性定制，此外不依赖于任何监督信息的前提下，实现属性（shape和appearance）的定制也并不容易。

第三段：
* 现有关于属性-level的图像定制化研究相对较少。要么是人为划分子时间步阶段，要么就是考虑不同的cross-attention层。

第四段：
* example-based 图像manipulation方法。

第五段：
* 我们的做法

第六段：
* 为了评估我们的方法，我们收集了Subconcept inversion benchmark。

最后：
* 总结贡献

---


第一段：

最近，文本引导的图像生成取得了巨大的进展。定制化图像生成是其中热门的研究topic，在虚拟现实，艺术创作，广告营销等领域有着广泛的应用。定制化的目的是从一组图像中学习一个concept，然后利用文本生成包含这些概念的新场景或者新风格图像。
然后，当前大多数的定制化图像生成工作关注的是整个图像concept的学习和定制，这可能无法满足人们的某些兴趣---人们往往只对图像的某种属性感兴趣，例如例如blue and white porcelain的外观属性或者一栋建筑的形状属性。




Recently, there have been significant advancements in text-guided image generation. Within this field, Customized image generation has emerged as a hot research topic, finding wide applications in fields such as virtual reality, art creation, and advertising. The aim of customization is to learn a concept from a set of images and then use text prompt to generate new scenes or stylized images that incorporate these concepts. However, most current work on customized image generation focuses on learning and customizing the entire image concept, which may not fully satisfy people's specific interests. People often have interest in only certain attributes of an image, such as the appearance of blue and white porcelain or the shape of a building.


第二段：

在这篇论文中，我们关注的是在仅仅给定单张参考图像的条件下，属性级别的图像定制化问题，如图1所示。其目标是从单张参考图像中学习用户感兴趣的视觉属性包括appearance和shape，并实现特定属性可控的文本到图像生成。这个设置不仅降低了参考图数量的要求，还实现了细粒度的视觉属性驱动的可控生成。然而，这个问题是极具挑战的。首先，单张参考图像所提供的信息相对有限，这给视觉概念的学习带来了困难。其次，当没有任何监督信息可用时，学习和定制特定的细粒度视觉属性进一步增加了困难。

In this paper, we focus on the problem of attribute-level image customization given only a single reference image, as shown in Figure 1. 
Our objective is to learn the specific visual attributes that users are interested in, such as appearance and shape, from a single reference image, and enable controllable text-to-image generation based on these attributes.



第三段：

传统的方法大多数是通过在一组参考图像上微调Diffusion Unet 模型或者优化罕见词的文本embedding来表示给定的图像concept，例如DreamBooth，Textual Inversion和Custom-Diffusion。然而，这样的方法往往需要多张参考图像，进一步限制了该方法的易用性。为了降低参考图像数量的限制，基于Encoder的定制化方法被提出来。然而这类方法仍然需要在大量图文数据上联合训练Encoder和Diffusion Unet，这引起的训练代价十分昂贵。此外，无论是基于微调的方法还是基于encoder的方法均无法实现细粒度的视觉属性级别的图像定制化。


Traditional methods often involve fine-tuning Diffusion Unet models or optimizing textual embeddings on a set of reference images  for representing specific image concepts like DreamBooth, Textual Inversion, and Custom-Diffusion. However, these approaches typically rely on multiple reference images, limiting their practicality. Encoder-based customization methods have emerged, requiring only a single reference image for efficient customization, contrasting with traditional approaches that rely on multiple images. While these methods excel in requiring only a single reference image for customization, they still demand extensive joint training of Encoder and Diffusion Unet on large-scale image-text datasets, incurring considerable training costs. Furthermore, both fine-tuning and encoder-based methods fall short in achieving fine-grained image customization at the level of specific visual attributes including shape and appearance.

第四段：

最近的方法开始关注属性级别的图像定制化生成任务，代表性的工作包括：P+和Prospect。
P+ 将单个文本prompt扩展到了多个prompts，并注入到Unet的不同cross-attention layer中来解耦视觉属性like style, color and structure. 然而P+需要用户提供多张参考图像才能实现属性的定制化， 收集特定subject的多张参考图像对用户来说是一件费力的事。相比于P+，Prospect提供了一个不同的观点，即不同的采样阶段对应于不同的视觉属性。例如初始采样阶段对应总体布局生成，中间阶段对应结构化的appearance，最终采样阶段对应详细的纹理。然而，Prospect需要人工划分10个子采样阶段，这样的操作可能会导致属性定制的不充分由于某些属性可能横跨多个子采样阶段。




P+ consists of multiple textual conditions derived from per-layer prompts, with each condition corresponding to a layer of the diffusion model's U-net.

The paper shows that P+ provides greater control over image synthesis by disentangling attributes like style, color and structure across layers. Finer layers predominantly influence appearance while coarser layers primarily affect structure.


第五段：

这篇论文提出了一种创新且简洁的框架，用于在仅有单张参考图的条件下，实现属性级别的定制生成，涵盖了shape和appearance。我们的基本理念如图2所示。我们的核心见解在于：图像的视觉属性，包括shape和appearance，是由Diffusion Unet的Encoder和Decoder学习得到的。首先，我们利用预训练的视觉encoder提取参考图像的视觉特征。接着，我们设计了两个Filter Module，分别是shape filter module和appearance filter module，用于通过过滤冗余特征提取与特定属性相关的信息。随后，我们将经过滤的属性特征与文本prompt的embedding融合，生成多模态融合特征，从而增强文本embedding的细节表达能力。最后，我们将多模态融合特征注入至属性Stable Diffusion模型作为条件，然后采用属性-aware的微调策略，精确学习和定制shape和appearance视觉属性。