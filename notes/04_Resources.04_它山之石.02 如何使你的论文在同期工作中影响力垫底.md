---
id: gj3bt6d57yf3jhqctxce7io
title: 02 如何使你的论文在同期工作中影响力垫底
desc: ''
updated: 1704211259055
created: 1704211149190
---

## **总结来看，论文需要有个好题目啊！**
> **可以借鉴这篇文章起标题的思路**

---


复盘了一下2023的工作。来分享一下我在论文营销上得到的教训。

今年年初的时候，ChatGPT大火，每个人都在谈论大语言模型。我们也抓住机会，在**5月2日**发布了一个多模态大语言模型的工作**VPGTrans**，提出了一个多模态对话模型**VL-Vicuna**。

然而我们却成功做到了**同期工作里影响力垫底**：

| 模型 | Arxiv 时间 | 数值实验数量 | 引用 | github star |
| --- | --- | --- | --- | --- |
| LLaVA | 4月17日 | 61 | 531 | 11.8k |
| MiniGPT-4 | 4月20日 | 0 | 435 | 24k |
| mPlug-Owl | 4月27日 | ～100 | 187 | 1.7k |
| LLaMA-Adapter v2 | 4月28日 | 15 | 130 | 5.2k |
| VPGTrans (ours) | 5月2日 | 428 | 22 | 0.25k |
| Otter | 5月5日 | 0 | 148 | 3.3k |
| MM-GPT | 5月8日 | 0 | 86 | 1.3k |
| InstructBLIP | 5月11日 | 179 | 531 | 7.7k |
| PandaGPT | 5月25日 | 0 | 63 | 682 |

其中，数值实验数量是我大概数了一下每篇论文第一版arxiv中图+表中的实验结果数量。这当然不是一个严谨统计量，也说明不了什么，我们仅仅示意一下。

在那个你**随便起个名字**、**实验报告里没有任何数字**就能获得**1k以上star**和**巨量引用**的时代，我们却在**做了top-3级别的实验量**之后，做到了**引用量**+**github star数量垫底**。

更离谱的是，虽然我们影响力被MiniGPT-4暴打，**但我们的思路其实和MiniGPT-4是撞车的**。。。都是用迁移学习将已有的视觉感知模块迁移到新LLM上。

论文在这里：[https://arxiv.org/abs/2305.01278](https://link.zhihu.com/?target=https%3A//arxiv.org/abs/2305.01278)

也许有小伙伴会问，是不是你们没用力宣传。其实也不是，我们当时也联系了公众号投稿+做直播，也找人帮忙转发过。但我们依然完成了影响力被大部分同期工作甩开3倍以上的壮举。

## 所以到底为什么？

这应该主要得益于我们在**起名字**和**宣传定位**方面的失败。

对于一个论文来说，最重要也是最具有性价比的宣传就是**起个好题目**。

而我们的题目叫什么呢？

> Transfer Visual Prompt Generator across LLMs

我们下面来逐点分析一下题目的问题。

  

**第一个经验：记得写简称！**

首先，我们其实是论文名字是有简称的 (VPGTrans)，但我却忘了把简称写在题目前面。稍好一点的做法应该是改成 VPGTrans: Transfer Visual Prompt Generator across LLMs。

原因非常简单：**在论文量爆炸的时代里，我们根本记不住完整的题目。**

举个最简单的例子，MiniGPT-4、mPlug-Owl、Otter这些文章题目里简称后面的内容，我一个都背不下来。离谱一点，即使是ResNet，我也记不住他的完整题目 Deep Residual Learning for Image Recognition。

  

**第二个经验：尽量快的亮明你的主题！**

一定要让人看完题目就知道你做了什么内容。甚至运气好的情况下，一些题目可以在第一个单词就亮明身份，比如MiniGPT-4是一个GPT-4开源方案，InstructBLIP是BLIP+指令微调。

我们的VPGTrans就很好的踩中了这个雷点。首先，Visual Prompt Generator这个学术用语，其实是我自己这篇论文里提出的。很多朋友可能根本不知道什么叫VPG。可能只有比较熟悉prompt tuning的朋友才能大概猜到Visual Prompt Generator是个什么东西。

这时候不如把题目改成 XXX: building new MLLMs with transfer learning。明明是一个意思，但阅读门槛却降低了很多。

  

**第三个经验：选最亮眼的部分做题目！**

一个论文往往有很多个侧面，比如研究问题有特色、模型结构简单、理论证明严谨充分、模型效果好、炫酷的展示效果等等。

以我的论文为例子，我主要有以下3个侧面：

1. **分析型论文：**巨量实验分析了如何做迁移可以既高效又不掉点。
2. **方法极其高效：**模拟BLIP-2直接开训，用10%开销完成BLIP-2训练。
3. **炫酷的应用场景：**VL-LLaMA和VL-Vicuna效果展示。

![](https://pic3.zhimg.com/v2-61a0004afcc8df4d5b748ca4249be1d2_b.jpg)

![](https://pic3.zhimg.com/80/v2-61a0004afcc8df4d5b748ca4249be1d2_1440w.webp)

非常明显，最亮眼的点其实是3和2。**但我偏偏只从1出发起了我的论文题目。**

从2出发，我可以起一个 "XXX: Building New MLLMs with less than $250"之类的题目。

从3出发，我可以起一个"VL-Vicuna: XXX"之类的题目。

从3,2,1出发，我应该起一个"**VL-Vicuna：transfer learning enables MLLMs construction with less than $250**"或者 "**VL-Vicuna：$250 is all you need for MLLM construction using transfer learning**" 之类的题目。

  

**第四个经验：叠点额外的buff**

常见于各类公众号和社交媒体，比如MIT出品，CMU华人小哥xxx，清华特奖，Best Paper之类的。这个大部分地球人也用不了，所以不推荐了。。。