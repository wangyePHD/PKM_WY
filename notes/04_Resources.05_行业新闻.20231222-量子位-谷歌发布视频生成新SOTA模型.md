---
id: 990rrao99ekrkbv2wu1dqr7
title: 20231222-量子位-谷歌发布视频生成新SOTA模型
desc: ''
updated: 1703222020964
created: 1703221446823
---


你敢信？大熊猫都会打牌了！

![图片](https://mmbiz.qpic.cn/mmbiz_gif/YicUhk5aAGtAnt8JIsuMHT34Le1NhjNLFWfUcUp1pHGia7EA3f8aowtJnc8FcgVZuHJJ0fcLHNic13AqzKkLzIJ4w/640?wx_fmt=gif&from=appmsg&wxfrom=5&wx_lazy=1)

看这毛茸茸的脑袋、抓牌的动作……

而这其实都是AI生成的，还是**零样本**那种。

这就是谷歌最新大语言模型**VideoPoet**。

它不仅没有用视频领域常用的扩散模型，还零样本实现了SOTA。相较于此前一些模型，画面更加稳定、动作更加逼真，清晰度也直线up。

![图片](https://mmbiz.qpic.cn/mmbiz_gif/YicUhk5aAGtAnt8JIsuMHT34Le1NhjNLFvvU0Fxs5zOjiaOibnAQhSN3pDic3LSJaO9BF7LVXlpaybGTpD9kIXJyMQ/640?wx_fmt=gif&from=appmsg&wxfrom=5&wx_lazy=1)

和Bard再合作一下，轻松搞定1分钟长的视频小片，从脚本到画面全部不用人类插手。

![图片](https://mmbiz.qpic.cn/mmbiz_gif/YicUhk5aAGtAnt8JIsuMHT34Le1NhjNLF6nic4txxeunIbMRGhojtW5icFDcets0U6diadn3FkhjNxlkth8yqZhPZQ/640?wx_fmt=gif&from=appmsg&wxfrom=5&wx_lazy=1)

这效果，让网友们直呼：视频生成进化速度也太快了吧。

![图片](https://mmbiz.qpic.cn/mmbiz_png/YicUhk5aAGtAnt8JIsuMHT34Le1NhjNLFxJ6AVN3QQqwAmxzm51RHrC8viafeia5ODeiaiaVz4ibd5tkqO4szafwHZgg/640?wx_fmt=png&from=appmsg&wxfrom=5&wx_lazy=1&wx_co=1)

不少人都表示想玩！

![图片](https://mmbiz.qpic.cn/mmbiz_png/YicUhk5aAGtAnt8JIsuMHT34Le1NhjNLFmUiaNOK3eZia03HRCKRZA0sSAXSJJaUYppahcRPPut3dulB0UKribNzvg/640?wx_fmt=png&from=appmsg&wxfrom=5&wx_lazy=1&wx_co=1)

有人还说，VideoPoet效果这么好，看来Runway和Pika要加速了！

![图片](https://mmbiz.qpic.cn/mmbiz_png/YicUhk5aAGtAnt8JIsuMHT34Le1NhjNLFY8gVzyWibicLU9j7icMLjr8MjUo3ib1bFGZicMupuOXyy7zV6JgP89EoiaibA/640?wx_fmt=png&from=appmsg&wxfrom=5&wx_lazy=1&wx_co=1)

## 画面逼真动作稳定

具体来看VideoPoet的能力非常全面。包括：

- 文本-视频
    
- 图像-视频
    
- 视频编辑
    
- 风格化处理
    
- 画面补充
    

**文本到视频任务**，视频输出长度可调整，而且可以基于文本内容应用一系列动作和风格。

![图片](https://mmbiz.qpic.cn/mmbiz_gif/YicUhk5aAGtAnt8JIsuMHT34Le1NhjNLFGNoVj5bJQRYaoxCboTYB1sZ0wuVObUBy8tJcQWE0foAlAI1Zd1hwoQ/640?wx_fmt=gif&from=appmsg&wxfrom=5&wx_lazy=1)

**图像到视频任务**，则能让静态图片动起来。比如一些世界名画和照片，都可生成视频。

![图片](https://mmbiz.qpic.cn/mmbiz_gif/YicUhk5aAGtAnt8JIsuMHT34Le1NhjNLFqHoZ5KNAhonjXH0YN0UXOXr0NnITyGdqGn2ia4vfVhmVcSVhJW6cs3w/640?wx_fmt=gif&from=appmsg&wxfrom=5&wx_lazy=1)

同时也能**调整视频风格**，需要额外输入一些文本，然后模型会预测视频的光照和深度信息。

比如输入“铁狮子在熔炉的火光中咆哮”，原本无厘头的太阳花狮子就变得凶猛威严起来。

![图片](data:image/svg+xml,%3C%3Fxml version='1.0' encoding='UTF-8'%3F%3E%3Csvg width='1px' height='1px' viewBox='0 0 1 1' version='1.1' xmlns='http://www.w3.org/2000/svg' xmlns:xlink='http://www.w3.org/1999/xlink'%3E%3Ctitle%3E%3C/title%3E%3Cg stroke='none' stroke-width='1' fill='none' fill-rule='evenodd' fill-opacity='0'%3E%3Cg transform='translate(-249.000000, -126.000000)' fill='%23FFFFFF'%3E%3Crect x='249' y='126' width='1' height='1'%3E%3C/rect%3E%3C/g%3E%3C/g%3E%3C/svg%3E)

当然也能进行**视频编辑**，比如让视频中的机器人随意运动、背景中加上烟雾等，都是输入文字指令即可实现。

![图片](https://mmbiz.qpic.cn/mmbiz_gif/YicUhk5aAGtAnt8JIsuMHT34Le1NhjNLFqibQzynSLiaj3tooDukln7icXGVjt0hBz1pxgYEjpMD8rHcDpuPP4s9qg/640?wx_fmt=gif&from=appmsg&wxfrom=5&wx_lazy=1)

或者是输入图像，然后修改它的动作。让蒙娜丽莎转动身体、打哈欠。

![图片](https://mmbiz.qpic.cn/mmbiz_gif/YicUhk5aAGtAnt8JIsuMHT34Le1NhjNLFBgiaJ2g8TiaQobibTYhHJqB5HJtNovmFialUzL3V6ibfBvv9TkvoicfGjkaQ/640?wx_fmt=gif&from=appmsg&wxfrom=5&wx_lazy=1)

以及可调整镜头动作。基本的缩放、弧线、航拍镜头都可搞定。

![图片](https://mmbiz.qpic.cn/mmbiz_gif/YicUhk5aAGtAnt8JIsuMHT34Le1NhjNLFsj6HpAnE4dSNEMXYD1Fazx4sAiavf47TlD3kYRwwufayprd7iaIRuP1g/640?wx_fmt=gif&from=appmsg&wxfrom=5&wx_lazy=1)

如果想让扩充视频画面、增加视频元素，VideoPoet也能实现。

![图片](https://mmbiz.qpic.cn/mmbiz_gif/YicUhk5aAGtAnt8JIsuMHT34Le1NhjNLFd5vDCibgoNqSHBMKMRAjkEY6oo45ewdohibRmyW7tNlry5cSjmGWctZA/640?wx_fmt=gif&from=appmsg&wxfrom=5&wx_lazy=1)

值得一提的是，VideoPoet还可以**根据视频配乐**。

这也是让不少网友感到惊讶的地方。

![图片](https://mmbiz.qpic.cn/mmbiz_png/YicUhk5aAGtAnt8JIsuMHT34Le1NhjNLFFW3nluHJA37XqcB7icW20a2awe17GrNtckS66G8iaGfvndeicib5hQpRicA/640?wx_fmt=png&from=appmsg&wxfrom=5&wx_lazy=1&wx_co=1)

比如先让VideoPoet生成一段小熊打架子鼓的视频，然后不给它任何文本提示，VideoPoet根据画面内容自己生成了音频。

如果想要生成更长的视频，可以通过输入视频的最后一秒画面让VideoPoet预测下一段视频，反复多次即可实现。


## 用LLM零样本生成视频

不仅是生成效果好，VideoPoet还有一个优势在于，以LLM为基础，它能更方便利用现有大模型进行改进。

比如VideoPoet就使用了T5的编码器。

![图片](https://mmbiz.qpic.cn/mmbiz_png/YicUhk5aAGtAnt8JIsuMHT34Le1NhjNLFyGaxicbq3fD4mMCkCoD9URC8bXqjlQGjOvKySqFEgbJlicGMFIBibey1g/640?wx_fmt=png&from=appmsg&wxfrom=5&wx_lazy=1&wx_co=1)

不过由于大语言模型使用离散token，使得它生成视频具有一定挑战性。

与自然语言不同，人类对视觉世界尚未演化出最佳的词汇表达。

通过**视频/音频tokenizer**可以来克服这一问题。

它们能将视频和音频编码为离散token，也可将其转换为原始表示。

VideoPoet正是基于这一原理实现。

它利用MAGVIT V2来搞定视频图像表示，SoundStream搞定音频表示。

前者是谷歌CMU团队在今年10月提出的方法，该方法实现了语言模型首次在ImageNet基准上击败扩散模型。

后者是一个端到端神经音频解码器。

具体来看VideoPoet的框架。它支持文本、视觉、音频输入，分别可利用t5、MAGVIT V2、SoundStream的编码器。

然后再自回归生成输出。

![图片](https://mmbiz.qpic.cn/mmbiz_png/YicUhk5aAGtAnt8JIsuMHT34Le1NhjNLFliav496wHiaYx0hHCyrWx6PYyAejFHooQt7GDVwAM0ZrHn0RlJfQJUEA/640?wx_fmt=png&from=appmsg&wxfrom=5&wx_lazy=1&wx_co=1)

实验结果方面，在提示词与生成结果的吻合度方面，VideoPoet超过多个扩散模型。

![图片](https://mmbiz.qpic.cn/mmbiz_png/YicUhk5aAGtAnt8JIsuMHT34Le1NhjNLFiavfAljCau9Jp3mGjJQpuL3LJOQxr8vr9iaCldmGZoUEdiapOxkWOibyHw/640?wx_fmt=png&from=appmsg&wxfrom=5&wx_lazy=1&wx_co=1)

生成动作方面的优势更加明显。

![图片](https://mmbiz.qpic.cn/mmbiz_png/YicUhk5aAGtAnt8JIsuMHT34Le1NhjNLFu51lQ7w2LYYiaTdw3b29rpQ3lu3eL11XgTkLxOKic5OaO2SON3o9RSyg/640?wx_fmt=png&from=appmsg&wxfrom=5&wx_lazy=1&wx_co=1)



* 参考论文：
  * https://arxiv.org/abs/2312.14125