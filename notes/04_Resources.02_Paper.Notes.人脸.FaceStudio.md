---
id: avjr9s4qkoebgholpy4dx08
title: FaceStudio
desc: ''
updated: 1710143999835
created: 1710143413002
---

## In a word

FaceStudio这篇论文其实本质上，还是在利用多模态强化的embedding来实现人脸身份的定制化生成。


## Method

![图 0](images/7dbf6251ac1466db4e7a1ca2350057c62370f1532daa4420b4346589b43d872a.png)  
（注意上图为推理示意图）

方法也比较简单，主要分为以下几个步骤：
* 作者首先利用mask，提取非人脸区域，作为style content的内容输入，提取的人脸图像作为identity content的内容输入。
* 然后分别提取embedding 
  * 文本由CLIP encoder提取
  * 人脸图像由Arcface提取
  * style embedding由CLIP提取
    * 上述三个特征会融合一下，然后过linear, 最后融合加权。注入到Unet中。

其实就没了，然后就是大规模的图像数据进行训练了。



## Insight

* 提升identity，多模态的embedding融合很重要
* 不过这篇论文的style内容居然用非人脸区域的图像，感觉不是很严谨啊。



## Results

![图 1](images/60d00252e531d45982db2d4193aae8a82d642e9dba6050ea1bf0105933c21a5e.png)  


## Tags

#人脸 #定制化