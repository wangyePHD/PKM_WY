---
id: qju6jh5omwgiw3d3ewjiomw
title: >-
  An Image is Worth Multiple Words Multi-attribute Inversion for Constrained 
  Text-to-Image Synthesis
desc: ''
updated: 1701064784773
created: 1701061037573
---
![图 0](assets/images/2b769499bd5d6f1a0bded51885a41236606f4088507496b6f4ea0a571c65e55c.png)  


## In a word
本文提出了一种反转给定图像的多种sub-concept或者attribution的方法。能够实现四类token的反转，分别是：**color, style, object, layout**

>**注: 在本文中，把Standing、Sitting成为layout**

## Motivation

* 对于诸如Dreambooth、CustomDiffusion等古老的方法来说，他们都只能将给定的reference图反转成一个token，无法反转感兴趣的子属性或者子概念。
* 后续出现的P+，Prospect这两篇工作，分别从Unet的不同层，Inference期间的不同的时间阶段出发，实现子属性的inversion。作者认为这两篇工作都不是很全面，应该结合时间步阶段和Unet的网络层，更全面的inversion子属性或者子概念。


## Method

![图 1](assets/images/92ec6bfc3679a614f78105dc3364d21b19819dd1d05f06aa09674456d2973d71.png)  

方法其实比较简单，只需要在不同层，不同的降噪阶段，分别注入token。接下来就是优化。
优化的损失有三种，第一个就是重建损失，也就是降噪损失：

![图 2](assets/images/73c8d7f6c8c4f4fd90254f705a8055db6f4fc75fe324388e239b6ba0303dcd39.png)  

第二个是color和style的解耦损失：

![图 3](assets/images/9a2bf9e20fdf8073537b677244cc816038ff6af941191eb2b8d48b4651e836af.png)  

我们的直觉是通过确保学习到的表示 < c > 尽可能接近 c_gt 的表示来推进这个过程，同时也确保两者与 s 的距离相等。这个过程自然地使得 < c > 的表示靠近颜色的CLIP特征空间（因此与 < s > 的表示不同）。


第三个是layout和object的解耦损失：

![图 4](assets/images/bc5cbe9a69040e1954822e0606eb4f78c2482499e46c769c7af768ba39042670.png)  


## Insight

![图 5](assets/images/accdab5f49c3530cde89d2c88db763381158b1a65197bb05b0b3c575596229ce.png)  

  
This passage summarizes observations from an image generation experiment involving different conditional settings—color, style, object, and layout. The key findings are:

- **Color & Style**: Specific color or style adjustments at various layers or stages didn't impact the generated image significantly. Color and style seemed mainly captured during initial denoising stages and across moderate layers.
- **Object Semantics**: Despite specifying different objects (e.g., cat, cow) in initial and later stages, the resulting image consistently showed a cat. Object semantics were primarily captured across middle denoising stages and coarse layers.
- **Layout Features**: Altering layout aspects after the first denoising stage had minimal impact on the posture of the generated cat, indicating layout was predominantly captured in the initial denoising stage and specific resolution layers.

In summary, variations in conditions appeared to influence different image features differently. Color and style were predominantly captured during initial denoising stages and moderate layers, object semantics across middle and coarse layers, while layout features were primarily captured in the initial stages and specific resolution layers.





## Results

![图 6](assets/images/a2f06d49e4a1475029abddb8bdcd4596bca9ba522134bbdf2ea432701db6f6a3.png)  

![图 7](assets/images/b3736068ad0a2080c20310b31b0fa1302563e1986b5da49cf8126718861409a3.png)  



## More
其他相关的文章

* [[04_Resources.02_Paper.Notes.Textual Inversion.P+ Extended Textual Conditioning in Text-to-Image Generation]]
* [[04_Resources.02_Paper.Notes.Textual Inversion.ProSpect Expanded Conditioning for the Personalization of Attribute-aware Image Generation]]

## Tags
#subconcept-inversion