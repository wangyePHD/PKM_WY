---
id: ccs7d7umlj5adk5iiz5i16k
title: CVPR2023-Tutorial-Alignment in Text-to-Image Generation
desc: ''
updated: 1700894981800
created: 1700887914946
---

这里的align指的是如何更好的**align with human intention**

![图 0](assets/images/16e4668b939494b21d8bc6672372e4649bdd2704bd429eb481fdec81e4a36474.png)  


本talk主要涉及了四个方面。分别是如下：
* 可控的生成：通过各种条件进行控制，比如ControlNet
* 图像编辑：改变或调整图像内容
* Better following prompts: 注入SD等文生图模型，有的时候生成的内容和文本输入并不一致。
* 概念定制化：Textual Inversion

![图 0](assets/images/2969be4621538bc840615c1d48a421a52f656db2c5ebe564f6a73e1d06df6250.png)  

接下来，作者介绍了四种比较主流的生成模型，分别是：
* GAN
* Auto-regressive model
  * 将图像离散化为token，然后训练，模型逐个预测token，最后由decoder解码成图像
* Non-AR Transformer
  * 与AR的不同是并不一定循规蹈矩的逐个预测，可以多个token一起预测出来
* Diffusion 

![图 1](assets/images/5ab744ffb234a19ac321ca3b7e5b638dbea690ae992f7c8ea75b025f182f1ef9.png)  


接下来作者主要就是详细的讲了一下Stable Diffusion的原理和细节。尤其是Cross-Attention的细节，以及SD在infernece stage是如何进行的。

![图 4](assets/images/9419a68ee2d8b8b16847a098af717136dc0dd62c40ff4a59cf383ba71c3de062.png)  

![图 3](assets/images/3c7effa4308fa9aefdb2f22ff9245f745ff1ca32ff6287d9f8af1e85b259a620.png)  

![图 2](assets/images/6b39859fe9e70218c4fbc517728da11d83212c255a3fb193978a4e6722f56394.png)  


接下来进入本次talk的核心四个板块的第一个：**可控图像生成**：

![图 5](assets/images/10ffc12f28445cc3c78a61ba43a3637b84d7bf1d8d6b5a1eeaf3cb4140618b2b.png)  

**基于Layout的可控图像生成：**

**ReCo**这个工作的核心是，将每一个object都进行描述，同时每个描述中都包含了position信息，接下来finetuning SD来理解这些position信息即可。

![图 6](assets/images/a34c6b00e9a603e6ee31fce63142d8c705b4204688361b81b674e0ce253ba533.png)  

与ReCo不同，GLIGEN实际上是从模型设计的角度出发，来理解layout信息的。在这个工作中，作者引入了Grounding tokens，其实就是object text name embeds + bbox embedding。此外，为了理解这样的grounding tokens信息，作者还设计了Gated Self-Attention机制，用来理解grounding tokens。这个 Gated Self-Attention只需要插入到原来的self-attention和cross-attention之间即可。并且也只需要训练这个Gated self-attention。

![图 7](assets/images/544df1c5c050376b6eb9fd911cfae40432eccd4f4dedba836fd7b1eb88f4edb7.png)  


接下来就是ControlNet的一些列工作了。

![图 8](assets/images/4bef66a735e0592da1dac29b75273f0da5713bf05e25e41fa68032eaf0430526.png)  

![图 9](assets/images/faec8f0b46dafa6c55b41618d14e55aec081da7fd74288e0cc2133dfd1491c83.png)  

**Inference-time guidance:**

这个也是一个很有趣的topic，我们除了在Training或者Finetuning SD做东西，还可以在Inference-Stage进行额外的指导。大家知道原始的inference阶段，SD用了Classifier-free guidance。除此之外，还可以使用任意一种能够计算loss并提供梯度的term来指导推理生成。比如Pix2Pix-zero中使用cross-attention和mask之间的loss来约束一样。

![图 10](assets/images/993df80d13b5a658ca0272abbf0f6c84df16f6d322ec41cb94173bb5b2920e18.png)  

可控图像生成部分完结
---
---

**图像编辑**是第二个较大的板块，这里作者分别给出了四个小topic。
![图 11](assets/images/7b64a5753bf97ec46f8f7950aa74b5deb4b0a5fdf2d798eb8e5fbd5453e8b77b.png)  


** Latent Spatial Blend **

这个东西其实是Inpainting。之所以称为Latent Spatial Blend，指的是前景的latent和背景的latent之间是可以blend的。

![图 12](assets/images/28ca6c6f343836046aaa24fdb26f2a1bd4fb526db5ea9ccc42f66fc6bd4a2778.png)  


**Image-Text attention edit**

Google的P2P。

![图 13](assets/images/5385ba9106a71dbaaf8982ebfa187a101f4e32b31156573a1d72dd2f055527d8.png)  


这个Imagic很有意思，也比较有启发。本质就是说SD其实是实现了文本到图像之间的生成式的映射。那我们是否可以基于文本的插值，来实现图像的编辑。

![图 14](assets/images/9ecdb8cf4b27b448a5e46a2c1995e46dd7b6d418f94ba609fc60f91474665238.png)  
这个是中文的解释：https://zhuanlan.zhihu.com/p/576710237

这个也比较经典，指令理解的编辑。
![图 15](assets/images/526d8b413c38ea695a11e67458a2057b48eeacd1995d75ae5274379f47bdf6b6.png)  

构建图像编辑系统
![图 16](assets/images/125f186c00ffd4d4b39fb5cfe82fdb3988fdaa3945eb42274f548e5f94a05235.png)  


图像编辑部分完结
---
---

接下来是Better Following Prompts

这个topic的动机是，SD没有办法完美的理解文本，并生成和文本内容一致的图像内容。

![图 17](assets/images/b53c8b6083d73e8d730592ffc52818c37201e4e4e92147ae59d3b7139eda39c7.png)  

这一部分的详细内容没有记录。

Better Following Prompts
---

接下来是最后一部分的内容，图像概念的定制化。

![图 18](assets/images/1653a82b8441c640cfc6e4e7e083c40f9f8c0d07dbe49787db41d6cda47bdc27.png)  



