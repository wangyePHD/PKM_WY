---
id: 23us7y92oosxf6a6tnnw779
title: '20231227'
desc: ''
updated: 1703653961695
created: 1703653449705
---




## UniHuman: A Unified Model For Editing Human Images in the Wild
#有点东西
#human

![图 2](assets/images/4b29c251c70d8ac053e2cd116dabf6bcb9aee286e63c819a39bb4d4025cfe2fb.png)  

![图 3](assets/images/ceb27dfddd6352f9d1b103549654af49ea00361f2829d19275fc5683b23844ce.png)  


这个工作是把Human Image Editing中的三种任务**重塑姿势、虚拟试穿和文本引导编辑**统一起来联合训练。


## Emage: Non-Autoregressive Text-to-Image Generation
#有点东西
#text2img

![图 4](assets/images/9deb73b941679230822b12a5292db8d3e58e9b87f926aa71509dfea147d3e390.png)  

这个架构很简单，但是文章还没完全完成。展示的图片效果也一般，而且数量也很少。



## FineMoGen: Fine-Grained Spatio-Temporal Motion Generation and Editing
#有点东西
#motion
#video_editing
#Video
#video_generation


![图 5](assets/images/47e499760f7b16c6593d053f76fbec0ac561eb00894eedacdb141ac45892a67f.png)  


这个工作做了一个本文引导的人体动作序列生成和编辑的工作，支持细粒度的操作。主要贡献就是一个Spatio-Temporal Mixture Attention (SAMI)模块。
此外，我看还收集了一个数据集，**HuMMan-MoGen dataset, which consists of 2,968 videos and 102,336 fine-grained spatio-temporal descriptions。**


## A Two-stage Personalized Virtual Try-on Framework with Shape Control and Texture Guidance
#有点东西
#human

![图 6](assets/images/ef5b20e53b335215160f8f62e459651eb39694f63f9315790e4920c0286c1059.png)  

做的事情挺有意思，就是给定原图，再给一张参考图像的衣服，然后你可以解耦这个衣服的shape或者是texture，给应用到原图上，就OK了。

但是架构图画的好复杂，不想读了。

![图 7](assets/images/02fe85d5f19a0e268574e0980dc7046c4bc10eb69fe38f0948f4660d627dbe3d.png)  



## High-Fidelity Diffusion-based Image Editing
#有点东西
#image_editing

![图 8](assets/images/e95700e173e0796841b3ca03865a8d7684eb5d46e1d39c0308f94005fa369d5e.png)  

这个工作的初衷是说Diffusion Model在Denoising的时候，会由于马尔科夫链的存在，导致错误的累加。因此，editing的效果都缺乏保真度。

作者的做法也比较简单，就是直接用一个Encoder去编码原图图像信息，然后在合适的Diffusion层注入。不过注入的方式有些不一样，他是选择利用这个Encoder来预测Diffusion Model中卷积核权重的offset。这个就有点和E4T类似了。


## A Recipe for Scaling up Text-to-Video Generation with Text-free Videos
#有点东西
#Video
#video_editing
#video_generation
#Text-free

![图 9](assets/images/136db73fa115aadd02105b1190f7899d802139dd219cbc273133b7a06166b300.png)  

这个工作有点意思，就是说如何利用大量的没有文本标注的Video数据，来实现视频的合成和生成。
作者就是将这个过程建模成两个分支，一个分支就是学Appearance，这个就完全可以利用图文来学。另外一个分支学motion或者temporal dynamic的信息，这个可以利用Text-free Video数据来学。


## Semantic Guidance Tuning for Text-To-Image Diffusion Models
#有点东西
#text2img


![图 10](assets/images/90c239e4cf5693fafd877466accab2a1f9642e184a8c69edda7490e1e431c605.png)  

这个图有点意思，之前text2image生成中存在alignment很差的问题。这篇论文把prompt解析成不同的concept，然后利用多个concept之间的score，对目标prompt进行约束。

## LangSplat: 3D Language Gaussian Splatting
#一般
#Gaussian_Splatting

![图 11](assets/images/57aa41a4383be460a383848a9159d74fd0b4ee01553a9e7e5698f67784cd97c8.png)  

基于Gaussian Splatting，做Text到3Dspace的query。