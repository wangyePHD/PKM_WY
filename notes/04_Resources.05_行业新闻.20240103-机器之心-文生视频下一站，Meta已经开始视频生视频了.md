
---
id: 69396b5xvfevtg3lrdyrcmk
title: 20240103-机器之心-文生视频下一站，Meta已经开始视频生视频了
desc: ''
updated: 1704256463517
created: 1704251722422
---


  

![图片](https://mmbiz.qpic.cn/sz_mmbiz_gif/KmXPKA19gWic1NHhSnLibZoQ4IS9QrPKhZQyPo0kAA0WnB37uUxMAfDghPxLiaQkiczeuia3maibFlE98vC2b8qRKZEw/640?wx_fmt=gif&from=appmsg&wxfrom=5&wx_lazy=1&wx_co=1)‍

文本指导的视频到视频（V2V）合成在各个领域具有广泛的应用，例如短视频创作以及更广泛的电影行业。扩散模型已经改变了图像到图像（I2I）的合成方式，但在视频到视频（V2V）合成方面面临维持视频帧间时间一致性的挑战。在视频上应用 I2I 模型通常会在帧之间产生像素闪烁。

  

为了解决这个问题，来自得州大学奥斯汀分校、Meta GenAI 的研究者提出了一种新的 V2V 合成框架 ——FlowVid，联合利用了源视频中的空间条件和时间光流线索（clue）。给定输入视频和文本 prompt，FlowVid 就可以合成时间一致的视频。

  

![图片](https://mmbiz.qpic.cn/sz_mmbiz_png/KmXPKA19gWic1NHhSnLibZoQ4IS9QrPKhZjv1IFnmnianhrYnVsuicYA1snhgeaHbq2ciaaBh0v6wU8ML7fgu7LhoFg/640?wx_fmt=png&from=appmsg&wxfrom=5&wx_lazy=1&wx_co=1)

- 论文地址：https://huggingface.co/papers/2312.17681
    
- 项目地址：https://jeff-liangf.github.io/projects/flowvid/
    

  

总的来说，FlowVid 展示了卓越的灵活性，可与现有的 I2I 模型无缝协作，完成各种修改，包括风格化、对象交换和局部编辑。在合成效率上，生成 30 FPS、512×512 分辨率的 4 秒视频仅需 1.5 分钟，分别比 CoDeF、Rerender 和 TokenFlow 快 3.1 倍、7.2 倍和 10.5 倍，并且保证了合成视频的高质量。

  

先来看下合成效果，例如，将视频中的人物转换成「希腊雕塑」的形态：

  

![图片](https://mmbiz.qpic.cn/sz_mmbiz_gif/KmXPKA19gWic1NHhSnLibZoQ4IS9QrPKhZapIsY7zhicY7W9CtkZIE2cfe0pNHmYmpV5h6n0nhzJTs9I6DqjsuVVQ/640?wx_fmt=gif&from=appmsg&wxfrom=5&wx_lazy=1&wx_co=1)

将吃竹子的大熊猫转换成「国画」的形式，再把大熊猫换成考拉：

  

![图片](https://mmbiz.qpic.cn/sz_mmbiz_gif/KmXPKA19gWic1NHhSnLibZoQ4IS9QrPKhZNcrdHd6epDKwAhqe9cct5c61pxic2EMcuibYLqjLPyuD2euaRvtErzYQ/640?wx_fmt=gif&from=appmsg&wxfrom=5&wx_lazy=1&wx_co=1)

跳跳绳的场景可以丝滑切换，人物也可以换成蝙蝠侠：

  

![图片](https://mmbiz.qpic.cn/sz_mmbiz_gif/KmXPKA19gWic1NHhSnLibZoQ4IS9QrPKhZyLZ4lCvLuTPWqvNtliaoOfa4S2A5whdoyddvdlyyXbR49zOxCg4dGdg/640?wx_fmt=gif&from=appmsg&wxfrom=5&wx_lazy=1&wx_co=1)

**方法简介**

  

一些研究采用流来导出像素对应关系，从而产生两帧之间的像素级映射，这种对应关系随后用于获取遮挡掩码或构建规范图像。然而，如果流估计不准确，这种硬约束可能就会出现问题。

  

FlowVid 首先使用常见的 I2I 模型编辑第一帧，然后传播这些编辑到连续帧，使得模型能够完成视频合成的任务。

  

具体来说，FlowVid 执行从第一帧到后续帧的流变形（flow warp）。这些变形的帧将遵循原始帧的结构，但包含一些遮挡区域（标记为灰色），如图 2 (b) 所示。

  

![图片](https://mmbiz.qpic.cn/sz_mmbiz_png/KmXPKA19gWic1NHhSnLibZoQ4IS9QrPKhZic3n8bH0KmiaeRxlUtLvPR9wuYeEialUEia0BU0opuc1B3f8Kqib67ibibsPQ/640?wx_fmt=png&from=appmsg&wxfrom=5&wx_lazy=1&wx_co=1)

如果使用流作为硬约束，例如修复遮挡区域，则不准确的估计将持续存在。因此，该研究尝试引入额外的空间条件，例如图 2 (c) 中的深度图，以及时间流条件。联合时空条件将纠正不完美的光流，从而得到图 2 (d) 中一致的结果。

  

研究者基于 inflated 空间控制 I2I 模型构建了一个视频扩散模型。他们利用空间条件（如深度图）和时间条件（流变形视频）对模型进行训练，以预测输入视频。

  

![图片](https://mmbiz.qpic.cn/sz_mmbiz_png/KmXPKA19gWic1NHhSnLibZoQ4IS9QrPKhZSkXia6icSp4UdwnD9ja5z9TY1onEugCyXt6amBYOVA7NjaHibJlBw3q1A/640?wx_fmt=png&from=appmsg&wxfrom=5&wx_lazy=1&wx_co=1)

在生成过程中，研究者采用编辑 - 传播程序：(1) 用流行的 I2I 模型编辑第一帧。(2) 使用本文模型在整个视频中传播编辑内容。解耦设计允许他们采用自回归机制：当前批次的最后一帧可以是下一批次的第一帧，从而使其能够生成冗长的视频。

  

**实验及结果**

  

**细节设置**

  

研究者使用 Shutterstock 的 100k 个视频来训练模型。对于每个训练视频，研究者按顺序采样 16 个间隔为 {2,4,8} 的帧，这些帧代表持续时间为 {1,2,4} 秒的视频（视频的 FPS 为 30）。所有图像的分辨率都通过中心裁剪设置为 512×512。模型的训练是在每个 GPU 上以 1 的批量大小进行的，总共使用 8 个 GPU，总批量大小为 8。实验使用了 AdamW 优化器，学习率为 1e-5，迭代次数为 100k。

  

在生成过程中，研究者首先使用训练好的模型生成关键帧，然后使用现成的帧插值模型（如 RIFE ）生成非关键帧。默认情况下，以 4 的间隔生成 16 个关键帧，相当于 8 FPS 下的 2 秒片段。然后，研究者使用 RIFE 将结果插值到 32 FPS。他们采用比例为 7.5 的无分类器引导，并使用 20 个推理采样步骤。此外，研究者还使用了零信噪比（Zero SNR）噪声调度器 。他们还根据 FateZero ，融合了在对输入视频中的相应关键帧进行 DDIM 反转时获得的自注意力特征。

  

研究者从公开的 DAVIS 数据集中选取了 25 个以物体为中心的视频，涵盖人类、动物等。针对这些视频，研究者人工设计了 115 个 prompt，范围包括风格化到物体替换。此外，他们还收集了 50 个 Shutterstock 视频，并为这些视频设计了 200 个 prompt。研究者对以上视频进行了定性和定量的比较。

  

**定性结果**

  

在图 5 中，研究者定性地将本文方法与几种代表性的方法进行了比较。当输入视频中的运动量较大时，CoDeF 产生的输出结果会出现明显的模糊，在男子的手和老虎的脸部等区域可以观察到。Rerender 通常无法捕捉到较大的运动，如左侧示例中的桨叶运动。TokenFlow 偶尔会难以按照提示进行操作，例如在左侧示例中将男子变为海盗。相比之下，本文的方法在编辑能力和视频质量方面更具优势。

  

![图片](https://mmbiz.qpic.cn/sz_mmbiz_png/KmXPKA19gWic1NHhSnLibZoQ4IS9QrPKhZLvO3wCUkVg37nFWnDXnCJ5ZTdGsIJgiaN0OEaNicuSsvCuiaE8D6bibejg/640?wx_fmt=png&from=appmsg&wxfrom=5&wx_lazy=1&wx_co=1)

**定量结果**

  

研究者进行了一项人类评估，以将本文的方法与 CoDeF 、Rerender 和 TokenFlow 进行比较。研究者向参与者展示了四段视频，并要求他们在考虑时间一致性和文本对齐的情况下，找出哪段视频的质量最好。详细结果见表。本文方法取得了 45.7% 的偏好，优于其他三种方法。表 1 中还展示了各方法的管道运行时间，对比了它们的运行效率。本文方法（1.5 分钟）快于 CoDeF（4.6 分钟）、Rerender（10.8 分钟）和 TokenFlow（15.8 分钟），分别快 3.1 倍、7.2 倍和 10.5 倍。

  

![图片](https://mmbiz.qpic.cn/sz_mmbiz_png/KmXPKA19gWic1NHhSnLibZoQ4IS9QrPKhZsSZIWTZxNicEuROPicIhJJS7LoS3zfalUMibt53CVHEeGT8JnSbFLZMYA/640?wx_fmt=png&from=appmsg&wxfrom=5&wx_lazy=1&wx_co=1)

**消融实验**

  

研究者将图 6（a）中的四种条件进行组合研究，分别是 (I) 空间控制：例如深度图 ；(II) 流变形视频：从第一帧使用光流变形的帧；(III) 流遮挡遮罩指示哪些部分被遮挡（标记为白色）；(IV) 第一帧。

  

![图片](https://mmbiz.qpic.cn/sz_mmbiz_png/KmXPKA19gWic1NHhSnLibZoQ4IS9QrPKhZHictiaNluOU56V5DVicOHsxvXkb8rhYLVqMdqR39IBwj9v1iaiaVlfzNx9A/640?wx_fmt=png&from=appmsg&wxfrom=5&wx_lazy=1&wx_co=1)

图 6（b）中评估了这些条件的组合，通过与包含所有四种条件的完整模型的胜率来评估它们的有效性。由于缺乏时间信息，纯空间条件的胜率仅为 9%。加入流变形视频后，胜率大幅提高至 38%，突出了时间引导的重要性。研究者使用灰色像素表示被遮挡的区域，这可能会与图像中的原始灰色相混淆。为了避免可能出现的混淆，他们进一步加入了二进制流遮挡掩码，更好地帮助模型识别哪部分被遮挡。胜率进一步提高到 42%。最后，研究者增加了第一帧条件，以提供更好的纹理引导，这在遮挡掩码较大而原始像素剩余较少时尤为有用。

  

研究者在 FlowVid 中研究了两种类型的空间条件：canny 边缘和深度图。在图 7（a）所示的输入帧中，从熊猫的眼睛和嘴巴可以看出，canny 边缘比深度图保留了更多细节。空间控制的强度反过来会影响视频编辑。在评估过程中，研究者发现，当希望尽可能保持输入视频的结构（如风格化）时，canny 边缘效果更好。如果场景变化较大，如物体交换，需要更大的编辑灵活性时，深度图的效果会更好。

  

如图 8 所示，虽然 ϵ-prediction 通常用于扩散模型的参数化，但研究者发现它可能会出现不自然的跨帧全局色彩偏移。尽管这两种方法都使用了相同的流变形视频，但 ϵ-prediction 带来了不自然的灰暗色彩。这种现象在图像到视频中也有发现。

  

![图片](https://mmbiz.qpic.cn/sz_mmbiz_png/KmXPKA19gWic1NHhSnLibZoQ4IS9QrPKhZjWU237NV44r1QnQKEoeqwKHHKgXM8fytcib6aHbUALb6icV0lVE3QJMA/640?wx_fmt=png&from=appmsg&wxfrom=5&wx_lazy=1&wx_co=1)

**局限**

  

虽然 FlowVid 取得了显著的性能，但也存在一些局限性。首先，FlowVid 严重依赖于第一帧的生成，而第一帧在结构上应与输入帧保持一致。如图 9（a）所示，编辑后的第一帧将大象的后腿识别为前鼻子。错误的鼻子会传播到下一帧，导致最终预测结果不理想。其次，是当摄像机或物体移动得太快，以至于出现大面积遮挡时。在这种情况下，FlowVid 会猜测缺失的区域，甚至产生幻觉。如图 9 (b) 所示，当芭蕾舞演员转动身体和头部时，整个身体部分都被遮挡住了。FlowVid 成功地处理了衣服，但却将后脑勺变成了前脸，如果在视频中显示，这将十分惊悚。

  

![图片](https://mmbiz.qpic.cn/sz_mmbiz_png/KmXPKA19gWic1NHhSnLibZoQ4IS9QrPKhZCxDpcIhILF1zF60ZM2bJtDdzA1Nvv36lmLljDXfn8UxC1BJxZJ8Rnw/640?wx_fmt=png&from=appmsg&wxfrom=5&wx_lazy=1&wx_co=1)