---
id: h2ha8dncqm40dcyrowgvjnc
title: λ-ECLIPSE
desc: ''
updated: 1710164717547
created: 1710164168746
---

## In a word

![图 0](images/26f64d54cc2bf065e67358ce885161dde60358555cca03888824d5446d289e40.png)  

本篇论文是定制化生成领域中，一篇比较不一样的工作。他不是用tuning-based或者encoder-based的方法。而是采用了类似于DALLE和Kandinsky中的text embedding 到图像embedding的映射，然后使用映射得到的img embedding去生成图像即可。

## Motivation


之前的定制化方法无论是基于Tuning的还是基于Encoder的，都会涉及到一个Diffusion Unet参与计算，这样的话，速度就很相对慢一些。
这篇工作呢，直接去学习文本到图像 embedding间的映射，这个映射学到后，就可以对任何文本得到img embedding，然后用img embedding去生成图像。这样的话，速度就会快很多。



## Method

![图 1](images/e9c003a0560ce038d66fecbb21ca726b9a95440f54fa5e50708f8d90284ccd0d.png)  

这个方法也是比较简单，只有一个地方需要训练。

* 首先作者构造了很多图文数据对，用来训练mapping function。
* 然后作者训练了一个mapping function，目标是将文本embedding映射到图像embedding。这里所用的损失函数，一个是MSE，一个是图文对比学习loss。
  * ![图 2](images/5a4d49f2d03ce809cb145fd9e3f098420adc78d92511cd0b536d4ffa5feaa683.png)  
* 一旦这个mapping function训练好了，那么给定任何一个文本，都可以得到其对应的图像embedding，然后我们可以用这个embedding输入至Kandinsky的decoder中，直接生成目标图像。




## Results


![图 3](images/3612e8e7669aa2124cc6a3080c1fe0e25af812db06a88cd1061b7f542d51d14f.png)  

![图 4](images/fb345af3cc5a981c700f0f99f7a974c50b7cf0fc39d23f5e149d8833c89de1f4.png)  


## Tags
#多概念定制化
