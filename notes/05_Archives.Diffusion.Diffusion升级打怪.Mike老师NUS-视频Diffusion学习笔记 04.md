---
id: avw7v3bnded8swnqq2fa1tm
title: Mike老师NUS-视频Diffusion学习笔记 04
desc: ''
updated: 1704176722662
created: 1703609998119
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

今天我们继续学习NUS Mike老师的Video Diffusion课程。今天的主要内容包括：

* Multimoda-guided generation
* Video Editing 
  * Tuning-based One-shot
  * Tuning-based Multiple-shot
  * Training-free


首先，我们先对视频生成领域的最后一个板块---Multimodal-guided generation进行介绍。如下图所示：

![图 0](assets/images/d94287905372493a1e51eebe0aeaa840aa8be3650cef10dca0b98a7026554862.png)  

![图 1](assets/images/6111c9abf599aef64b6d6c3770d419163acb1f067541b3524b971ffc5fa775df.png)  

![图 2](assets/images/186be0f63b283d8922ac095d9e41e9e57c5461ec36f88cfdb2cb42ce0f6c740b.png)  

![图 3](assets/images/2c66bd368c81c336c20d6e67397d83e27af0ddec800e76bb473a3ca5315d54cb.png)  


![图 4](assets/images/4de2c5011b8f2004cb10091c5796b8241a48cc65d8e3594d7959456b9d37e09c.png)  


![图 5](assets/images/69cebbd20103d2bcf705039a07eeae2924168a2e898158ef4095fcb192a68b4f.png)  


![图 6](assets/images/147d0c88022f0dce05c6111414941805e0dfb4b1b1b956fc63b6c6383cdb30b0.png)  


![图 7](assets/images/b5d49ba559b2471f58c5b7d198d9fce89c6303becf1abda0f89b95756c6fd2a9.png)  


![图 8](assets/images/1ee9e194857d0ad04971d58419673a8b83ead801158a3027fed37a79e8a038f9.png)  



---


接下来，我们主要介绍视频Editing的工作。因为对于视频数据的训练，计算资源将消耗巨大。因此，基于Tuning-based的方法对于高校科研来说可能更加合适。

![图 9](assets/images/961d34beb28fd21784973f148a1da973081846a224b6a5d03de0a7c716ba9b12.png)  

而One-shot Tuned的方式，就是只给定一个视频数据，然后在给定的这个视频上训练微调，实现对视频的editing。而这样的训练成本是相对较低的。

![图 10](assets/images/e6987b18393bd98df0d6b228462e822cbf8a0c83edda4697c02c72550f721efd.png)  

接下来，我们介绍one-shot tuned的代表性工作 **Tune-A-Video**：

![图 11](assets/images/daef69ce504b0ace1373966feb8de8426d5c17f358105eb7f769c35d27d78156.png)  

这个工作要做的事情是：给定一个目标视频，我能否在保持目标视频的motion的前提下，editing目标视频中内容的appearance。

为了实现这个目标，这篇论文从下述动机出发：可以利用预训练好的T2I模型来生成很好的appearance信息，然后从给定的reference video中学习motion的信息。

![图 12](assets/images/16ad2a862e1d940b46e74861486f44d92968d718069801c2b2943ba8cdbf3163.png)  

![图 13](assets/images/ee7c6502dc4b669df718fd6381c467b796973b5f49c9fdf75f82eeb85381deee.png)  

作者采用的核心做法就是在给定的one-shot视频和文本描述下，inflate预训练的T2I模型，并高效微调。

![图 14](assets/images/825d76b09bb1051d057ecb92a0404556f88ec2eb7a1ae83ee0c6396d1e05e856.png)  

![图 15](assets/images/a69a32447f97c808c4152eb3ee3a01e28a7e2a575f46ad991ee9c8a6d66956d8.png)  


如上图所示，左侧是训练图例，而右侧是推理图例。在训练的流程图中，因为给定的Reference Video只有一个，因为全部finetuning整个T2I是不切实际的。于是作者采用的做法是在T2I中插入Spatial-Temporal Attn和Temporal-Attn，然后只训练这些相关层，其他均固定。此外，作者还设计了一个高效的注意力计算方法，那就是在计算帧与帧之间注意力关系的时候，只需要计算当前帧和第一帧，以及当前帧和前一帧之间的关系。

以下是一些效果展示：

![图 16](assets/images/09816e9d323deda92302e86b1039ed47e2aa19e70570f8634ffc3253950a120c.png)  

![图 17](assets/images/bead04270dd34b9c48fea72d5fad57a8afd40f11ca9e50819b803feb4c0d41e2.png)  

![图 18](assets/images/1d7db3ffff7ad09b9ff33d875f4d25bc0afded7be333fdab31ee2432a43e9dc4.png)  

![图 19](assets/images/12c0b1eb1d8d448ce657bb97c13d321775f5dc54259da1a9d749f822ccfc9c22.png)  

后续One-shot tuning的工作，还有一篇是来自于google的**Dreamix**：

![图 20](assets/images/6dceb05d2c78ab17e34fd284fa128f9c9d2520c056e305821915f217cc42d29a.png)  

![图 21](assets/images/44c47c7d6004bcc5d2a5f6bbcc4947a5bbeb9219551f9c7ed47571629238e3cc.png)  


他的核心做法是：同时混合训练视频数据，和其乱序的帧图像数据，训练视频数据的时候，temporal attention需要训练。而训练image的时候，时序的layers不需要训练。

更多的工作如下所示：

![图 22](assets/images/da0766c2de8a8ad31be53398a202097f42b81b4984677c4cef7b3b99a2f7d686.png)  


接下来，我们介绍一下**Multiple-Shot Tuned**的方法。

![图 23](assets/images/bfa9b1b6676d65194297e00d2cf0ebc16147a20e2fd043e73c7c4bacf98fda57.png)  

这里要介绍的代表性的工作是：**MotionDirector**。

这个工作的核心是如果给定多个参考视频，可以怎么学习？比如下面这张图，如何让猴子打高尔夫球？


![图 24](assets/images/71e31f290b5609679428f38963a056f7fcf071e978eff1b03475732bbf76f7ad.png)  


如果直接利用T2V模型去生成，你会发现猴子，高尔夫这些概念都是有的，但是打高尔夫的motion是缺失的。

![图 25](assets/images/a6d5f5cadba8a7151f9295a12b66b88823dba1e9fa23344e40e84d387cbd1ffe.png)  


这个工作的做法就是，提供一些motion video subset，然后从这些视频集中学习motion，并应用。

![图 26](assets/images/38162f3cd66849466e4ac69ebed5fd3c983544f70bdc823ab3a346325ddbf94f.png)  

![图 27](assets/images/6a488fce9e0bcca0e23021691bc52f9508203ec5f55bbb48181754d7b246bce9.png)  

作者分别训练了两个分支，对应两个LoRA，一个负责学习Spatial appearance信息，另外一个负责学习Temporal信息。


这个方法不仅能学习物体的motion，还可以学习相机的motion。
![图 28](assets/images/d0625a1bc6481212ca36d8227d4679aa04ca30ab2d6cd42b1cbb55a04630b312.png)  

该方法可以实现motion和appearance的解耦。

![图 29](assets/images/7b029baaf11766288e5c2e1dd445243c25e37c46f42fe387663ad147f5be6928.png)  

---

接下来，我们将介绍Training-free Video Editing的相关内容：

![图 30](assets/images/38f1fff63be171a8bb0934df1f7cd02d367ef395e68d834a83cffecadd95ca84.png)  

第一个代表性的工作是TokenFlow。

这篇工作的动机是，如果采用T2I模型逐帧编辑的模式，会发现时序一致性很差。

![图 31](assets/images/2f52319fd6ff2b3fa00edf5d6323cff6556044968681b072bd62931c8f7ca57a.png)  

因此，可以利用帧与帧之间的token correspondence来学习。

![图 32](assets/images/1bf60c0be78641bf39e97978426db54191f3e99f32d16103fe2a2a859c54e0d4.png)  

![图 33](assets/images/24221bfbd5dfb4232d90b7792320bedc8be2fc08ab6d998eb37b918acff65c6f.png)  

![图 34](assets/images/a2f950e4ef4300a6142962fe794b33304893a6b76e81cea5fa29ad4eafe95a94.png)  

具体的做法就是利用当前帧之前和之后的帧对应的特征，进行加权融合，得到当前帧的表示。

![图 35](assets/images/c79348e8636f22aa0e5e39e118e860863a665d5b5eeb7fe51d255159c49687da.png)  

如上图所示，TokenFlow的一致性还是不错的。


另外一个工作是：**FateZero**

![图 36](assets/images/32b8928e72f99f5bf3012ddf995cd7d1cd38186808b99f0497ab0c541028782a.png)  

![图 37](assets/images/e7d9e557035136a064b116ee0897b3a9bb1c69b1a72ad9681b224e0923986905.png)  

从上述两个图可以看出，FateZero的核心步骤分为两步：

* 第一步就是利用DDIM inversion，得到当前视频的self-attention的特征
* 第二步就是前景使用编辑文本驱动得到的特征，背景使用第一步得到的self-attention的特征。依赖mask进行融合。


看一下结果：

![图 38](assets/images/f5858545c4233a49857a81f4e8d4085360f7d8169360e10afdfadd8374f3a5ae.png)  

更多的工作：

![图 39](assets/images/4a6a794dd8dba7a7eb1ab4ff268016da0a0b1f3295614c4dce22156c357d2913.png)  




未完待续。。。。

