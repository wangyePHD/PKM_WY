---
id: ovec1dsuisobnyb143kx9bz
title: 主谓宾定制化生成
desc: ''
updated: 1708500639252
created: 1706964542875
---



* **主谓宾定制化生成**
  * 主语：给定一张胡歌图像
  * 宾语：给定一张水桶图像
  * 谓语：给定一张梅西举起大力神杯的图像
  * 生成：胡歌举起水桶的图像

上述两个Idea均属于多物体、多概念定制化生成领域赛道，这个赛道目前还不卷，关于多概念定制化的文章：通用物体的包括了Custom-Diffusion、CONES、CONES V2、Mix-of-Show。person-centric包括Fastcomposer、PortraitBooth、Face-diffuser等。


这个想法和其他工作之间的差异是：
* 现阶段的多概念定制化方法生成的多个概念之间没有任何的联系，基本是要依赖文本或者layout来指定他们之间的interaction。
  * 文本不准确，layout太麻烦，并且对于有些交互，layout并不适合用于表达。
* 我们的想法是不仅要有多个concept，多个concept之间的交互也要有，同时这个交互信息不是通过文本或者layout指定的，我们也给他提供了一个interaction图，从图中学习interaction，然后生成复合特定interaction的多概念结果。


这个想法可能需要分阶段来实现，因为如果多个concept和interaction一起来学习的话，难度有些大。可以：
* 第一个阶段，先做多概念的定制化学习，主要目标就是identity的高度保持，高保真度。
* 第二个阶段，设计一个interaction提取模块，提取interaction。
* 第三个阶段，微调上两个阶段。

