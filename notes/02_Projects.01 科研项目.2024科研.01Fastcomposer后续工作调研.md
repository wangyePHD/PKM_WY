---
id: iopmvfv4eprz5n6db2xagv5
title: 01Fastcomposer后续工作调研
desc: ''
updated: 1706423871665
created: 1706369756649
---


## DreamVideo: Composing Your Dream Videos with Customized Subject and Motion

这篇论文介绍了一个叫做DreamVideo的系统，它可以帮助人们用电脑制作出自己想要的视频。这个系统特别擅长把特定的角色（比如一只狗或者一个人）和特定的动作（比如弹吉他或者跑步）结合起来，创造出全新的视频。这就像是你可以告诉电脑你想要一个视频，里面有一只狗在弹吉他，然后电脑就能帮你做出来。

## Customizing Motion in Text-to-Video Diffusion Models

这篇论文介绍了一种叫做“Customizing Motion in Text-to-Video Diffusion Models”的方法。这个方法可以帮助电脑学习新的动作，然后用这些动作来制作视频。就像你告诉电脑你想看一个机器人跳舞，电脑就能根据你的描述，创造出一个跳舞的机器人视频。也就是给一个视频motion，学出来一个V*，然后用来定制化生成此motion对应的视频。

## A Video is Worth 256 Bases: Spatial-Temporal Expectation-Maximization Inversion for Zero-Shot Video Editing

在计算机的世界里，有很多技术可以帮助我们生成图片，比如根据文字描述生成图片。但是，视频编辑比图片生成要复杂得多，因为视频是连续的图片序列，需要保持时间上的连贯性。所以，研究者们想要找到一种方法，能够在不训练计算机的情况下，直接编辑视频内容。



## VideoBooth: Diffusion-based Video Generation with Image Prompts

想象一下，你有一张你最喜欢的超级英雄的照片，比如蜘蛛侠。然后，你告诉魔法棒：“我想要一个视频，蜘蛛侠在纽约的高楼大厦间飞来飞去。”这篇论文就是研究如何让魔法棒（计算机）听懂你的话，然后创造出一个视频，里面真的有蜘蛛侠在飞。


## PortraitBooth: A Versatile Portrait Model for Fast Identity-preserved Personalization
#重点

这篇论文介绍了一个叫做PortraitBooth的工具，它可以帮助电脑快速地根据你的照片和文字描述来制作个性化的肖像画。这个工具特别擅长理解你想要表达的情感，比如快乐、惊讶或者酷酷的，然后让电脑画出的肖像画中的人物看起来就像真的在经历这些情感一样。简单来说，PortraitBooth就像是一个魔法画笔，你只需要告诉它你的想法，它就能帮你画出一张既像你又充满个性的肖像画。这样，你就可以得到一张独一无二的图片，展示出你想要的样子和情感。

## Local Conditional Controlling for Text-to-Image Diffusion Models


研究者们想要找到一种方法，让电脑能够理解你的文字描述，并且能够在图片的特定区域添加你想要的东西。这样，你就可以创造出更有趣、更个性化的图片。


## StoryGPT-V: Large Language Models as Consistent Story Visualizers

#重点
#paper_idea

想象一下，你有一本书，书里有很多故事，每个故事都有好几页，每页都有文字描述和对应的图片。现在，我们想要让电脑学会读懂这些故事，并且能够自己画出这些故事的图片。但是，这比单单画一张图片要复杂得多，因为电脑需要理解故事中的角色，比如“他”、“她”、“他们”这些代词指的是谁，还要保证每张图片的角色和背景都是连贯的。



## UDiffText: A Unified Framework for High-quality Text Synthesis in Arbitrary Images via Character-aware Diffusion Models

论文主要研究的是如何让电脑在任意图片上生成高质量的文字。
想象一下，你有一张图片，比如一张风景照片，你想让电脑在图片上加上一些文字，比如“美丽的风景”。但是，电脑有时候可能会把字写错，或者写得不整齐。这篇论文就是教电脑如何更好地在图片上写字，让文字看起来既准确又美观。



## Grounded Text-to-Image Synthesis with Attention Refocusing

有时候电脑生成的图片并不完全符合文字描述，比如可能会画错颜色或者位置。为了解决这个问题，他们发明了一个叫做“注意力重聚焦”（Attention Refocusing）的方法。这个方法就像是给画家一副特殊的眼镜，帮助他更准确地看到描述中的关键部分，比如小丑的衣服颜色和他在草地上的位置。



## FaceStudio: Put Your Face Everywhere in Seconds

想象一下，电脑里有一个神奇的画师，它叫做FaceStudio。这个画师非常聪明，它可以听懂你的话，比如你说“我想要变成卡通风格”，或者“我想要穿上超人的衣服”，然后它就能在你的脸上画上相应的风格，但你的五官还是你的五官，你的朋友一看就知道那是你。

这个画师是怎么做到的呢？它用了一种叫做“混合引导”的方法。就像你画画时，先用铅笔画出大概的形状，然后再用彩色笔上色。FaceStudio也是这样，它先用一种叫做“风格图像”的东西来决定你想要变成的样子，然后用你的照片来确保画出来的还是你。这个过程就像是把一张你的照片和一张卡通风格的图片混合在一起，但保持你的特征不变。

而且，这个画师还能处理更复杂的情况，比如你想要和你的好朋友一起变成卡通人物，或者你想要在古代的背景里。它通过一种叫做“多身份交叉注意力机制”的方法，能够分辨出图片中的每个人，然后分别给他们加上不同的风格，但每个人还是保持自己的样子。



## Make-A-Storyboard: A General Framework for Storyboard with Disentangled and Merged Control

#重点
#paper_idea

你给电脑画师讲了一个关于一只小猫在花园里玩耍的故事。电脑画师首先会画出小猫在花园里走来走去，然后是小猫在花丛中玩耍，接着是小猫站在树下，最后是小猫在池塘边看着水里的鱼。每一页都是一个场景，而且这些场景都是连贯的，就像你在看电影一样。

这个电脑画师非常厉害，它不仅能够画出小猫的样子，还能保持花园的样子不变，这样你就能清楚地看到故事是怎么发展的。而且，如果你想要故事里的小猫换成小狗，或者花园变成海边，电脑画师也能帮你做到，而且画面看起来还是那么自然和协调。

这篇论文就是介绍了这个电脑画师是怎么工作的。它用了一种叫做“解耦控制”的方法，先把故事里的角色和场景分开来画，然后再巧妙地把它们合并在一起。这样，不管故事有多复杂，电脑画师都能画出既符合你的故事，又看起来和谐一致的图片。


## CogCartoon: Towards Practical Story Visualization

#重点
#paper_idea

比如，你有一个关于一个小女孩、一个小男孩和一只小狗的故事。你告诉CogCartoon：“在一个阳光明媚的下午，小女孩在公园里遇到了小男孩，他们一起玩耍，然后遇到了一只可爱的小狗。”CogCartoon就会根据你的故事，画出小女孩在公园里玩耍的场景，然后是他们遇到小狗的场景。而且，这些画面都是连贯的，就像你在看一本真正的图画书一样。

CogCartoon的魔法之处在于，它不需要很多的训练材料，也就是说，你不需要给它看很多类似的故事和图片，它就能学会如何画出你的故事。这就像是你只需要给一个小朋友看几本图画书，他就能学会怎么画里面的人物和场景了。

此外，CogCartoon还有一个特别的功能，那就是你可以在故事中随时添加新的角色，或者改变角色的位置。这就像是你可以在画板上随意移动小人偶，让他们出现在你想要的地方。


## High-fidelity Person-centric Subject-to-Image Synthesis

#重点
#paper_idea

这个画笔非常特别，它有两个好朋友，一个叫做Text-driven Diffusion Model（TDM），另一个叫做Subject-augmented Diffusion Model（SDM）。TDM擅长画背景，比如森林、海洋或者城市；SDM则擅长画人物，比如你和你的朋友们。

当你想要画一个故事时，首先TDM会帮你画出背景，比如一个美丽的海滩。然后，SDM会根据你提供的图片，帮你把人物画进这个背景里。这个过程就像是TDM先搭好舞台，SDM再让人物上台表演。

为了让人物和背景更自然地融合在一起，Face-diffuser还有一个秘密武器，叫做Saliency-adaptive Noise Fusion（SNF）。这个秘密武器会告诉画笔，哪里应该让TDM来画，哪里应该让SDM来画，这样画出来的人物就能和背景完美地融合在一起。

举个例子，如果你想要画一个穿着蜘蛛侠服装的男孩和一个女孩站在海边，Face-diffuser就能帮你做到。TDM会画出海边的背景，SDM会画出蜘蛛侠男孩和女孩，然后SNF会确保他们看起来就像是真的站在那个海边一样。


## SINGLEINSERT: INSERTING NEW CONCEPTS FROM A SINGLE IMAGE INTO TEXT-TO-IMAGE MODELS FOR FLEXIBLE EDITING

这个魔法相机叫做“SingleInsert”，它有两种模式。第一种模式叫做“inversion stage”，就像是一个魔术师，它能把一张图片变成文字描述，然后再根据这个描述变出新的照片。比如，你给相机一张小狗的照片，它就能学会小狗的样子，然后帮你变出一张新的小狗照片。第二种模式叫做“finetuning stage”，这就像是给相机升级，让它不仅能够变出小狗，还能让小狗穿上不同的衣服，或者改变它的表情。

这个魔法相机很特别，它不会把背景也一起变，比如你只想让小狗穿上超级英雄的服装，但不想改变它身后的草地。SingleInsert就能帮你做到这一点，它只关注你想要变化的部分，让其他部分保持不变。

而且，这个魔法相机还能帮你做一些更复杂的事情，比如同时给小狗和小猫穿上超级英雄的服装，或者让小狗从不同的角度看起来都像超级英雄。这些都不需要你教它很多次，它学一次就能记住。

论文里还提到了一个叫做“Editing Success Rate (ESR)”的新方法，就像是给魔法相机打分，看看它变出的照片有多好。这样，我们就能知道这个魔法相机在变魔术时表现得怎么样。

## Expressive Text-to-Image Generation with Rich Text

#重点
#paper_idea


这篇论文通过引入富文本编辑器的功能，提高了文本到图像生成模型的灵活性和精确性。



## VideoDreamer: Customized Multi-Subject Text-to-Video Generation with Disen-Mix Finetuning
#重点

## 介绍
这篇论文介绍了一个叫做**VideoDreamer**的系统，它能够根据你提供的文字描述，生成包含多个主题的视频。比如，你可以告诉它“画一个小狗和小猫在海边跳舞”，它就能创造出一个视频，里面有小狗和小猫在海边快乐地跳舞。

## 研究背景
在人工智能的世界里，有一个任务叫做**文本到视频生成**，就是让电脑根据文字描述来创造出视频。这个任务很难，因为电脑需要理解文字，还要创造出动态的画面。以前的系统只能处理一个主题，比如只能画小狗，或者只能画小猫，但不能同时画它们两个。

## 研究动机
科学家们想，如果能让电脑同时处理多个主题，并且让它们在视频中自然地互动，那该多好啊！这样，我们就可以创造出更丰富、更有趣的视频内容。

## 研究方法
为了解决这个问题，科学家们发明了一种新的方法，叫做**Disen-Mix Finetuning**。这个方法就像是给电脑装上了一个小精灵，这个小精灵可以帮助电脑记住每个主题的特点，然后在生成视频的时候，让它们各自保持特色，不会混淆。

## 贡献和创新点
- **VideoDreamer**是第一个能够处理多个主题的文本到视频生成系统。
- 它使用了一种叫做**Disen-Mix Finetuning**的技术，可以很好地保持每个主题的特色。
- 还有一个叫做**Human-in-the-Loop Re-finetuning**的功能，让你可以参与到视频创作中，如果不满意，可以告诉电脑调整。

## 相关工作
在VideoDreamer之前，已经有一些系统可以生成视频，但它们只能处理一个主题。VideoDreamer的出现，让电脑能够同时处理多个主题，这是一个很大的进步。

这篇论文就像是在说：“看，我们找到了一个新方法，让电脑可以像人类一样，根据文字描述创造出包含多个角色和动作的视频。”这真的很酷，对吧？



f