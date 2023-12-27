---
id: p1753zhbl5utlbol8kz3wnq
title: Mike老师NUS-视频Diffusion学习笔记 03
desc: ''
updated: 1703525781839
created: 1703522392765
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


今天，继续学习Mike老师关于Video Diffusion Tutorial的内容。

![图 0](assets/images/75d60fc5c61298b400417fdde1de7601b5c6b787fa75653f33691b0b5db4b2b2.png)  


首先介绍AnimateDiff，他的初衷是如何高效的利用社区的大量定制化模型，来生成视频。而不是重新训练，降低代价。

![图 1](assets/images/7d94c17133ed3dd0a8e46c1f56c2dfda51e4e1645de6007c820029ebfb83ab69.png)  

整体的思路比较简单和直观，通过插入一组Temporal layer list，原文中论述为motion module，然后固定SD，在视频数据上利用Noise MSE Loss仅训练这个module的参数。训练好之后，motion module就具备了从视频中提取motion信息的功能。

![图 2](assets/images/b5bf8d1788fec2332911585839f0dc15c6cd6133464e0321e3de3c0ed940ceb9.png)  

这是直观的模型架构，还是比较简单的。

![图 3](assets/images/673af9029d71e550717028210aee16f8fef37c81656f80c9ccca7433359f6fe0.png)  

（不过这个AnimateDiff实际上是个Image Animation模型）

--- 

接下来这篇工作是Text2Video-Zero，其动机是如果不微调的话，能否直接利用Stable Diffusion来实现视频的生成？如下图所示，实际上可以通过两个方面进行探索：
* 让每一帧的初始化噪音在pattern上都比较类似
* 让不同帧之间的中间特征尽可能的相似

上述两个做法的核心和本质就是保持视频帧的时序一致性。

![图 4](assets/images/e863827fb7115e75cc2b341bde4ff3a6891c12c93f10a1aa9d1333787b60535a.png)  


接下来逐个点解释：

第一个点，如何才能让不同帧之间的噪音pattern尽可能相似呢？
具体做法就是定义一个motion，在给定第一帧噪音的基础上，根据motion逐帧修改noise，得到其他帧的噪音初始化。比如下图中得马，第一帧的噪音初始化后，如果定义的motion是逐渐向左下走，那就逐渐的将噪音向左下移动。

![图 5](assets/images/ad3df4a1ffbdcca86b21197932668c6a57b15d2ab9dd95c488af9ac1d2590cc7.png)  


第二个点，如何才能让不同帧之间的特征更相似呢？
具体做法就是让所有帧对应的self-attention中的k，v，全都替换为第一帧的K，V。

![图 6](assets/images/9fec3f8a1d40bd94c582217eb94ae73edb8c410d752286714903b1e668c5745c.png)  


第三个点，做背景的smooth。
![图 7](assets/images/c03dae4d5be2ea1db4a0d16eb2c134f3da81d6d59f1a91e3914d58e9c3005c5b.png)  


其他training-efficient的工作：

![图 8](assets/images/2916cb01d7a50a3cbc1bd7f4207277bfc29b25ae647042fb8a859c6cba7dbb6f.png)  

---

接下来介绍电影脚本相关的视频生成：

![图 9](assets/images/cea8f8e1331525dd329192fb3a88fa6d21ff75e87ddabab0c939ecaf4aef1a91.png)  

![图 10](assets/images/1e0661733a3283d374e503ccc4b825b22d3374a086e92c6b95bc56bb5a4aa90c.png)  

![图 11](assets/images/9c0fc4a06d4fe3d06b7c41aacef4a2563a264d23e442249972e4bfd11e2a628f.png)  

![图 12](assets/images/c15d32a8662d993d69aa935d1cb78e289c16c5f008c1f67b8c0f9d364bbcd4ed.png)  

![图 13](assets/images/33d1a65da03b4dc913e5fc2ad457e6f8c1ba40646a376ccdbed97c89bc0a1dc4.png)  

如何才能生成电影脚本呢？或者电影脚本对于模型来说如何建模呢？

答：通过定义prompt，利用GPT生成脚本，并且在脚本中可以生成物体的bbox。有了这些脚本之后，可以得到很多的condition，之后就可以利用ControlNet的机制利用这些条件。

![图 14](assets/images/4c4d0d13f45e0ae585a1e880d4dd9f9046996e860239e743a825710716de3fd8.png)  

![图 15](assets/images/2110fffd159838a27f462e1576d8dd5e7d2e11b689ea9df93190daa27e827276.png)  

![图 16](assets/images/205137afdf7f650136517caf735b2ee0dcb9351796b541f995806fd117e86d1f.png)  


除了上述工作外，现在也有很多工作利用LLM来实现StoryBoard Video的生成。

![图 17](assets/images/90938281ece2e28804278cb34dd5c6db6bfad96ded36ab461eb9532f7b1c2f10.png)  

![图 18](assets/images/731a3296c518936c879cd04e8abbe9ebc39a13399ae72d13dc745c592b01b75a.png)  

![图 19](assets/images/63df9411ae836722dec5538bbaf84a270b8a47c9f07db98d289f98054ad414ca.png)  

GPT本身并不能很好的理解Visual Prior，有的时候生成的结果并不合理。因此，也有一些工作去利用GPT先去训练一下，使其更好的适配long-form video prior。

作者收集并标注了StoryBoard20K的数据集，用来训练GPT或者LLM，能够生成更加合理的video layout。

![图 20](assets/images/cd815ef265da9cda8c05995fe90f88d812ce1dfa19df52937966d5b8b7e4f63c.png)  


其他更多的工作：

![图 21](assets/images/9e8cab8aaed07d29aa5cae8b70e694c3db186b6a1014e1bea870f26948a1ac91.png)  


---

接下来介绍了长视频生成的代表性工作。

![图 22](assets/images/c44fb4deade2ce379c37333a9c3eb81863d888264ccf81d292e2c5d191526d48.png)  

![图 23](assets/images/d157296a78d9de0e36f41e1de087e56ce62db57cf848882c352371ade72f6b63.png)  


NUWA-XL这个工作是一个代表性的工作，他的核心思想就是**迭代的进行插帧，实现长视频的生成**，提出了diffusion over diffusion的架构，利用两个Diffusion实现。

![图 24](assets/images/e88ba835e448a9c47ee8e616570da8074008e8024d4e54e30873dc213ca14963.png)  


详细来说，先准备好一些notes，就是文本提示，然后基于这些文本提示，你可以得到每个文本对应生成的关键帧。这就是第一个Diffusion要做的事情。基于这些关键帧，第二个Diffusion就可以不断插帧，得到最后的视频。

![图 25](assets/images/c85e3d821816466033d01ebb2199325f5bfed2e5576ae1b0de27edaeaf4a541f.png)  


这张图就更加详细了。
* 自顶向下，Global Diffusion得到3个关键帧。
* 选择第一帧和最后一帧，利用Local Diffusion生成中间的帧
* 递归如此


![图 26](assets/images/e84fed67dd2d6091d8a3b40ccfcfab2553c192d7045c4c44dae4ac651e4c843c.png)  

可以看到，当Global DIffusion作用的时候，输入的就是纯噪音，所以Mask ALl Frames。
但是当Local DIffusion作用的时候，需要保留首尾帧，然后Mask掉中间帧。

![图 27](assets/images/d2603d527b9aab0707e2510ac26d18e0ace3e808bddc232ea6dc5d66f166fa93.png)  


更多长视频生成的工作：

![图 28](assets/images/4fe8180ff1e7094c9024fb9eb32a1e5ba72e60100bbcbcd20f8122f1a55e868c.png)  
