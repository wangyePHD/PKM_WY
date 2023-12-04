---
id: 61cg2sqsm3yisalx3gjo03r
title: Research_Ideas
desc: ''
updated: 1701708785356
created: 1701279654189
---


## **基于文本或者引入更多的控制，生成更加复杂的自动驾驶视频数据**
#自动驾驶
#video_generation
#Video
* 灵感来源：
  * Panacea: Panoramic and Controllable Video Generation for Autonomous Driving
  * ![图 6](assets/images/19d087c22ecb8efb5322cc8bf11431555a67fff6bf48dd7f86b02d0e6983e148.png)  

* 详细描述：
  * 如上图，这个工作只是能够生成简单的左右方向，以及季节、天气等简单的视频数据。但是对于自动驾驶来说，还有一些更复杂的数据需要生成。比如**长尾数据中的少数样本，多车拥堵数据，路口拥堵数据，车祸场景数据，障碍场景数据等等。**


不过我最近也看到了中科院发布的工作，[[Drive-WM|04_Resources.05_行业新闻.20231202-机器之心-驶向未来，首个多视图预测+规划自动驾驶世界模型来了]], 这个工作可以生成高质量的视频，同时还能实现很多控制，比如文本修改天气，方向和速度，稀有场景、行人生成和前景编辑。



## **用户给定参考图像，反转图像内容，替换原视频中的内容**

#Video
#video_generation
#Video_edit

比如原视频是一段狗在走路，用户提供的是一匹马的图像，我是否可以修改视频成马在走路呢？

StyleCrafter: Enhancing Stylized Text-to-Video Generation with Style Adapter
![图 0](assets/images/72c90c853c01b3102244e437e3f01a7003ad41bbcb9c581fb94e687c7c48fbb1.png)  

收到了这篇工作的启发，不过这篇工作是做style的。我们想做identity和content。

可以参考PhotoSwap这篇工作：PHOTOSWAP: Personalized Subject Swapping in Images


