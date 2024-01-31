---
id: g1sxlzyurev38simrpwsxon
title: Expressive Text-to-Image Generation with Rich Text
desc: ''
updated: 1706687627328
created: 1706680251266
---


![图 0](../images/7347af42e6f5984944d5c15a3e2f3c4feb756132ccfdeb1b4861b8764fbf0e42.png)  

## In a word

这篇论文第一次提出了使用富文本来作为提示，驱动图像生成。最大的创新点就是提出了新的任务，衍生出很多的novel应用。这个任务是Rich-text-to-image generation，即从富文本中生成图像。富文本相较于传统的文本，可以更加丰富、更加丰富的表达信息。本文最关注的还是以下几点：

* 富文本可以自由设置**字体颜色**
* 富文本可以调整文本的**字体样式**
* 富文本可以**加粗文本**，来re-weight文本权重
* 富文本可以**写脚注**，从而提供更多的描述信息



## Motivation

大多数的图像生成方法使用的是朴素文本驱动图像生成，但是传统文本存在很多限制，例如描述不清晰等。因此，本文提出了使用富文本作为输入条件，驱动图像生成。


## Method

![图 1](../images/5b8e5571686e64f16658a575cacc5b21cdbe7a88b8c6f6c7abebcd0ab956770f.png)  

本文在技术上的创新并不大，总体方法的流程图如上所示。

* 首先用户可以输入富文本
  * 富文本会首先转成plain text。
  * 富文本还会转为json形式，主要用于保存attribute信息等。
* plain text将输入至Vanilla Diffusion模型中，主要的目的是得到初始图像对应的attention map，这里包括self-attention和cross-attention。然后利用谱聚类直接对self-attention map进行聚类，得到K个segments。这些segments将和文本tokens进行相似度匹配，得到每个text_span对应的attention mask。也就是spatial layout信息。
* 之后的问题就比较简单了，可以把整个文本，分解为单独区域的优化问题。
  * 因为每个区域目前都有文本对应，比如对于church，我们输入了RGB颜色，对话与garden，有footnote信息。
  * 对于每个区域，我们可以利用对应的文本信息，来优化该区域图像生成，这部分的优化技术其实就是利用Classifier-free guidance来指导更新Xt，也就是test-time optimization。
  * 唯一一点需要注意的是，颜色的学习，作者利用的是生成图像的RGB信息和给定的RGB之间的MSE loss来进行学习。

总体来说，本文提出了富文本引导的图像生成任务，但是整体的解决方法还是基于传统文本+辅助信息+test-time optimization，进行实现。但是富文本这个点，确实优化了人们的输入逻辑，同时也赋予了人们更多的灵活性和自由度。


## Results

![图 2](../images/63cbd27e60948706eb7583da7fec2f554e15e8f342865789928938efbe6faeb5.png)  
![图 3](../images/63ce74a1115c2994b52dafa4f9976fddca7ec77ae18242d7a4b80476c23395fa.png)  
![图 4](../images/df86c17d4846ec2dccabcf3db3faa2c62c7086ba0267e2e241613924097a03ad.png)  
![图 5](../images/6427a6f2e85565fec9be5cb62049ce8dca0c66a732b5592e72f86f1a2d7ef3a1.png)  
![图 6](../images/69767262883922faaeb829c228472d673b07ab46054b793abc5c51219b981ae0.png)  


## Tags
#text2img


