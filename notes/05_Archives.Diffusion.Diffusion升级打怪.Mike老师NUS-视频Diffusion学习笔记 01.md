---
id: ifo493mxkj0k25wriq0c5n8
title: Mike老师NUS-视频Diffusion教程
desc: ''
updated: 1703141065719
created: 1703132643996
---



## **教程介绍**

![图 0](assets/images/cba65fa80c9c8c40d3cc610f3c5a7c086a1263da71f8027ea048ba176540132c.png)  

来自新加坡国立大学的Mike老师制作的关于Video DIffusion Models的Tutorial教程。目前在youtube和bilibili上都有上线。

**Mike老师的个人资料：**
* [个人主页](https://www.comp.nus.edu.sg/cs/people/mikeshou/)
* [bilibili账号](https://space.bilibili.com/1409032486)
* [youtube账号](https://www.youtube.com/@mikeshou1749)
  
**课程资源：**
* 视频链接如下：
  * [youtube](https://www.youtube.com/watch?v=0K56LA821ys) 
  * [bilibili](https://www.bilibili.com/video/BV1jN4y1879z/?spm_id_from=333.1007.0.0&vd_source=45b600ad98b8c54b21b9561915c1ba61)
* Slides：
  * [PPT](https://www.dropbox.com/scl/fi/u7jgodz3tz01bzd5uftog/Video-Diffusion-Tutorial-Prof-Mike-Shou-NUS-2023-Dec-15.pdf?rlkey=de6axl9dnjhz1ub0wmpwmpq4f&dl=0)
* 课程主页：
  * [主页](https://sites.google.com/view/showlab/tutorial)

---


**本笔记用于记录自己学习该课程的学习心得。有过对你有帮助，请帮忙点赞、收藏！本笔记将持续更新，预计一周时间完成本教程的学习。**


下面是学习目录：

![图 1](assets/images/da0fa56f1a2c242700afd3125d32986b309388411b8756a65a49cd853f5a287a.png)  


![图 3](assets/images/d710996ed929018d07f046640a91df66d7eab776777bfe7cccfa3df1dc2ebffe.png)  


首先Mike老师介绍了DDPM和DDIM的原理机制，同时也介绍了DDIM Inversion的含义和概念。但是具体细节并没有详细论述。如果对此处细节不了解，可以学习李宏毅老师的课程：
* [Diffusion Model的数学原理介绍](https://www.youtube.com/watch?v=ifCDXFdeaaM)

![图 2](assets/images/b7218ed0b685029478c718d50bc0c918cb3368711e7f2a161954bf3b820d2d74.png)  


<!-- # TODO DDPM为什么在denoise的时候还要加个噪音呢？
<!-- # TODO DDIM 和 DDPM的区别到底是什么？ -->
<!-- # TODO DDIM Inversion的细节是什么？ --> 


接下来介绍一些基本的技术模型：
* CLIP
* Latent Diffusion
* Stable Diffusion
* LoRA
* Dreambooth
* ControlNet


上述这些经典工作，不做详细的介绍。可以看具体的论文了解其细节。

---

![图 4](assets/images/2976c9e8991e336478347fc76ee316c3a73dbb278feec2f253b67ba73e9fbc56.png)  

目前视频生成发展的非常迅速，各大公司都发布了自己的视频生成架构产品。如下图所示：

![图 5](assets/images/06e558dcbcdf4f1729337b49516da36770da6fb0101fdf38010f5c7e0cb25578.png)  

同时，Mike老师对当前的视频生成工作进行了分类，如下图所示：

![图 6](assets/images/afccd8a8ee05dcea54cbc677941eaccff7b5654a12272d2aaf16e9f66a7bbf75.png)  

接下来逐个类别进行讲解：

![图 7](assets/images/7492161e84c5054fca9036354ea1de7216b191ac16783c0ae0f3880893c71be5.png)  

![图 8](assets/images/81ec35f280790b3fdbb5bba5e8e49f3bd4fe44d31b96ab18a45c59c4e1f68e41.png)  


与文生图相比，文本驱动生成视频有什么不同：

![图 9](assets/images/66b3d651db75ecd05a1f382261a91987511eb1de1886a50e106ede2e08dfa331.png)  

首先是在输出形式的不同，图像是二维的模态，而视频则是多帧组成的3维模态。

![图 10](assets/images/2e4b932d471312a8c392ea1910f886027bf69d22eb292d3687276199a624bb59.png)  

接下来回顾一下过去在视频处理的时候的一些技巧和技术：
* 第一个就是3D卷积

![图 11](assets/images/5b0798f5ba7c23fe9e090566da8ff38ad1e51e6a2c10a03c28991f8602f723d1.png)  

* 第二个是将3D卷积优化为（2+1）卷积，也就是分别在spatial和时序上做卷积

![图 12](assets/images/3a92233b859dd6b019815a48893d48965e8a3a8a78e02094c787d51f37e42125.png)  


接下来介绍Google的最初视频生成开创性的工作：Video Diffusion Model （NIPS22）

![图 13](assets/images/93d9231ff235481e652ce91a7ef67e4b5bf519c3f90f484e6707d5d6ce3b4bbe.png)  

这个工作可以生成16帧的烟火图像。

![图 14](assets/images/6fb19730b9bf723f204a0c4b31b24c50573d7136649b9bdb64b41828b009e0e0.png)  

对于该工作来说，其架构和原理如上图所示，总结来看有以下主要几点：
* 核心思想还是扩展2D Diffusion至3D模态
* 因此作者设计了一个3D Unet，能够关注空间和时间维度
* 插入时序注意力层，主要是学习不同时间帧之间的关系。


接下来介绍另外一个工作：**Make-A-Video**

![图 0](assets/images/389d5fb6685c0b6e7ce5b67ba77836bee1d3b23644e05b75bdf084309c6edac3.png)  

Make-A-Video采用了级联生成的方式，如上图可以看到，
* 输入文本，模型会先生成初始的几帧视频，此时视频的帧数较少，质量较低，这一步对应到上图中的SpatialTemporal Decoder。
* 初始帧经过Frame Interpolation这一module，会进步增加视频帧的数量
* 之后经过Spatiotemporal Super-Resolution，将会提高视频帧的分辨率
* 最后，经过最后一个Spatial Super Resolution进一步提高生成视频的质量。

接下来是Make-A-Video的模型细节：

![图 1](assets/images/b0a304833c58ef3a0b144e494d4e4911aade3c935e4d2321aaadf8ec449cac91.png)  

![图 2](assets/images/bcec33822c20a4b119d630e9de702e42330c5d25ff5b0a05f42a83aed6ee9ca4.png)  

值得注意的是，即使在视频生成过程中，2D上所有的操作基本都是从预训练的T2I模型中初始化的。而时序的处理则是单独设计的。


![图 3](assets/images/46eccc6642d8f82280b9eb5d2948462cfc5c51ea344dc63e9148d379a09079fb.png)  

最后总结一下，如上图所示。

接下来介绍视频生成领域的**主要数据集**和**评价指标**：

![图 4](assets/images/6d0990376555f7ac8af5047b93f9a4ec8b54cdf78ebb5e7c3d8aca36f990cc42.png)  

![图 5](assets/images/fe6c9088025c9e2fc6f539b525ac3e4a17cf2b382984e51777241c8d153b27ec.png)  

![图 6](assets/images/6aa1908fb62169d84d94fa6db708be446f542a0b05193f9590e2fe0c79b67f91.png)  

总览完这些指标后，我们将详细的解释这些指标的含义：

![图 7](assets/images/18548f9e7eb62d01855adbb6f1a4b19e34257ac866bdae4daafc6a1d68041a57.png)  

FID是衡量图像之间语义的相似度。具体就是利用生成图像和参考图像分别过Inception V3网络，得到各自的embedding，然后计算FID即可。FID越小表示语义越相似，生成的图像越像真实图像。

**但是FID关于关注high-level的语义信息，忽略了Pixel-level的细节信息。**

![图 8](assets/images/fab252c2c8ee8b64897e4364ec290af15dc690cad071849907b58393478cf278.png)  

![图 9](assets/images/b863487607a4c30c682ee21cc1314c4ffa6ec22702d7bec8db6f3f73efaab835.png)  

PSNR和SSIM都是关注Pixel-level相似度的指标。

![图 10](assets/images/7d729c21c088cf49337ecaabd0f58b4190b1cb68a372ac0d6935259533dd2a4d.png)  

CLIP的图文相似度。


上述是Image的评价指标，现在我们看一下video的评价指标。

![图 11](assets/images/1a3da2b22ec15bb3313ecf2a9319b25d7f5b4317b1794220a22aa237a9dcb4bb.png)  

![图 12](assets/images/3ee36aa036d10189c1b3daa6ee010d597df8bf02146dff11ef404a8a8addc741.png)  

![图 13](assets/images/2702b18fe830ff99a42712e5892bc8c39c689421540b6e993be368e85ececae9.png)  

![图 14](assets/images/475215d97fdf878a6f7fa5059275c4fb9f5f2bf1cb10ef77067c01a6315c1d21.png)  


上述都是基于机器的自动评价，接下来我们看一下人工打分的指标：

![图 15](assets/images/8aa19ec588a5a80b61a3dc674275306d8391dbb6cdb982c2861090787c32fed5.png)  

比如在Make-A-Video中，人类需要对生成视频的质量和对文本的忠实度进行打分。


![图 16](assets/images/cfe0a7be8f756354b5554a5c689fd4ac725975ab8693de2a6e3cd9196f22bc5a.png) 


接下来是Prior Work中的最后两个工作：

Imagen Video:

![图 17](assets/images/f523ba8e4eb8c46e938cd226769e8938cd604db3e1120d3536923483aa9032da.png)  


Align your Latents

![图 18](assets/images/472b9e471e9d328b059e6d17c401b8d0e98607627e9cff4fb53785e5583965b1.png)  

![图 19](assets/images/ae6ab934debced84d61bb454cc82bc2c867310826e7f3ae6c7e0a9ee6c1f58c1.png)  

值得注意的是，Align your Latents是基于LDM的工作。

---

**未完待续...**