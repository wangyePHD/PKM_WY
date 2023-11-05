---
id: q308z7ug9yl38xeo2zrnuq5
title: 诸子钰3D-VisTA通用统一的3D视觉语言预训练模型
desc: ''
updated: 1699192244883
created: 1699188834495
---


![图 0](assets/images/06f4d80acc6a7b8d3aa26d544f4c4ac5134a7cb82d28fa4ad2999ffb37658e10.png)  

之前的3D VL models都是关注特定任务的，无法作为一个general model来处理多种任务。

---

![图 1](assets/images/d1428b6f8cfb2c5e9ad7279c7fa04f97b070b96e4831243ded9246b13f5a73e8.png)  


---

![图 2](assets/images/f6a4ac708e10e0b47679e940ac6ece0441bbe8c420cc82d607a1d21532bc3ca8.png)  

这里的发展脉络还是总结的很清晰的。


![图 3](assets/images/3876c01fb3ad1ff35d05ab47abfb9d445b3120d40d60cbb2c4718216416c1744.png)  

1、没有一个统一的3D VL model

2、没有大规模的数据集

3、3D environment和2D图像存在很大的差异


![图 4](assets/images/949f4ee43173e2bb3199a7e51ba67a69c83034f76d3100e77f2c9733732e344c.png)  

![图 5](assets/images/51ae829d8224f48559a48670f39def62e817ab966e3b8c1c41a96ab38592b602.png)  

他这个工作还是比较简单的、统一的，通用的。

![图 6](assets/images/aee6f558090c9a8786b1cf7693bb422b7937947ce672a95fa715f424458aab40.png)  

![图 7](assets/images/dc67ac0523de85748594a95ff7d949b8e8faccd5f1aa8986f8a03215694c0c79.png)  
![图 9](assets/images/63c76c167f2798da5521377c986066ad315177d1660e0b125f329c2b12db25b4.png)  


他这个自己提出的数据集，体量还挺大。

![图 8](assets/images/a36b8f7ac4e84bda1940ebe8e0165f435dc7ebf88798baff7dfa04de89a8cfa6.png)  

利用第三方的媒介，作为信号，调用LLM得到一些文本，这个想法还是比较通用的。

![图 10](assets/images/adc67331daeb7c3e4f735c1a59146e0f6d2df9a3918fb3b529db15ef137ea459.png)  
虽然这个架构很简单，但是我现在的一个想法就是，只有在大数据加持下，你的模型才有可能搞得简洁。不然就需要用各种loss来辅助学习。
