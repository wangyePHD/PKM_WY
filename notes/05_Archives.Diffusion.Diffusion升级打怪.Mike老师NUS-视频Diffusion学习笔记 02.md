---
id: 0ogp2qvilp0te851zc85dmk
title: Mike老师NUS-视频Diffusion学习笔记 02
desc: ''
updated: 1703232649029
created: 1703228441671
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


今天我们继续学习Mike老师的Video Diffusion Tutorial的第二部分---Video Generation

![图 0](assets/images/6fdfe6eb5d658b89b338b7916a5877332110c9910514e6f6a6129ffd9aea6fee.png)  


在这一节当中，将主要介绍当前open-source的base model for video generation。

![图 1](assets/images/7310a2d9a2707a3ce25081bbbaf6ad987fc4a38d9e5b37a87d42d76de3098d69.png)  


第一个工作是**ModelScopeT2V**。这个工作的idea，是利用现有的预训练的T2I模型，迁移到视频生成任务上。请看下图

![图 2](assets/images/e036cd2d42a0b8ba7fedf1c316d72c29f89cfd19db0845645910047f59bdac96.png)  

左右对比，可以发现ModelScopeT2V，基本保留了Stable Diffusion的原始架构。

![图 3](assets/images/1ed024e95f41ff0c1fe04df60dee9797271ab12e127c44a3ec570364ca389587.png)  

此外，ModelScopeT2V还针对视频设计了spatio-temporal blocks，具体的结构可以看上图。

![图 4](assets/images/39aa276ac0a8cd85c6e4950159c1544c4d60d3b1531fffeab4d410f5b520ac4d.png)  

一个比较有趣的地方是ModelScopeT2V是可以支持变长的视频生成的，这得益于Temporal Block的数量是可以设置的。当只有一个Temporal Block的时候，模型就会生成图像。

![图 5](assets/images/0a6daf42fa06b9e592c7581181ddf6b5dbb589b3ee0a44285f6447963b5d78d7.png)  

接下来看一下结果：

![图 6](assets/images/9dd630fa8d279c348ebec8c1a68172f2c54a7a74801f044b3afc7169c2429d1d.png)  

---

接下来介绍第二个工作，**Show-1**。

![图 7](assets/images/6992a610d8064ad3e43d3d1fcf3ef1017c411d9b6166abe9d629216f85ff2bc9.png)  

Show-1的动机是发现，之前的一些方法比如ZeroScope和ModelScope生成的视频，和对应的文本之间并不完全相符。比如上图上bule tiger。

![图 8](assets/images/2446dd9d32451b551f203cdb28f4ec1d4f19a14905e269bf21ae75ff77d4578d.png)  

如上图所示，show-1认为pixel-level的Diffusion Model能够带来更好的文本和视觉内容的alighment。这个可能是因为：
* pixel-level的Diffusion Model本质上是像素和文本之间的交互。
* 但是latents-level的Diffusion Model和文本的交互，时间接的，所以就有可能发生无法对齐的现象。

但是如果直接在Pixel-level进行视频生成工作的话，显存的消耗是巨大的。这个该如何解决呢？
作者团队采用了级联的模型架构，也就是在生成初期采用Pixel-level，这个时候像素分辨率较低，显存压力不大，同时在init的时候提供了很好的alignment。然后在后续的超分阶段，虽然分辨率较大，但是可以在latents-level进行，进一步降低显存消耗。

![图 9](assets/images/298b294a0187e196f5dd21ad1cc8a43bf4b7d00297e4f51b61844405a1f1551d.png)  

![图 10](assets/images/b1810deb3f11a7ea0c71bb904932a63ef6b1001fe267921e585a9f9e91acab1e.png)  

这样的话，Show-1就能获得更好的alignment，同时计算也是高效的。

![图 11](assets/images/3865de3d092d751ec5c95f2a7696ed08cd89680029a27c26c093382dc8884755.png)  

---

接下来，简单介绍了两个开源工作VideoCrafte，LaVie。

![图 12](assets/images/f60acf0ea49d191acf6cc0df2c28333b9867e5b5831cb7833d8f9e03fc78bbc3.png)  

![图 13](assets/images/d4d05b3963548bab8c91c1a0f25458a2a952791dcbb0555d4946ad39a0b05f06.png)  

这里，Mike老师介绍也比较快速。大家感兴趣可以去看一下原论文。


之后，介绍了Stable Video Diffusion。

![图 14](assets/images/1eebbc2803a3fa105c8d876a2b9dd8f08a867eab49fd7b65ad5bc27cc323b618.png)  

第一步就是使用SD2.1的权重进行初始化。

![图 15](assets/images/1cbdf37f12141b75a302462c533bc7050c2d06e06bd9db1d88049ae557385266.png)  

第二步是开始收集并制作高质量的视频-文本数据。

![图 17](assets/images/1bb9f61e5811adf12ff137511cc9faa53dbe5c523b07d08f12d890b4c2186de5.png)  

![图 16](assets/images/62ab7918aacb67ec84847a5115c017c9409eaeb128a223e307bb4805de5600ba.png)  

这是最终的数据情况。

![图 18](assets/images/11b5eb3cd3a86885133e3232a7b6e07703793acda3fd68f4f5038c07a2670c91.png)  

第三步就是Finetuning。SVD可以支持：
* Text2Video
* Image2Video
* Frame Interpolation
* Multi-View Generation


---

未完待续...