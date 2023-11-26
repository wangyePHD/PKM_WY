---
id: 7cedeiiixb0q5uzg2l3eu1p
title: In_context_learning
desc: ''
updated: 1698643849056
created: 1698643849056
---

# Visual In-context Learning Paper 

## milestone-work
 - _**Visual Prompting via Image Inpainting (NIPS2022)**_， 
  _**第一篇**_构建In-context learning的工作，直接构造了Grid-Image（4宫格），
  利用inpainting的方式，去复原第四张图，这样的话网络学习的只是在给定前三张图像
  的上下文的基础上，学习如何输出第四张图。不再受限于具体任务。
  具体的方法就是（MAE+VQGAN）
    - 后续的改进工作
      - _（**处理更多的任务**_）_**Painter**_ : Images Speak in Images: A Generalist Painter for In-Context Visual Learning
      , 这个工作还是建立在MAE的基础上来做的，只不过Painter可以支持的任务相较于
      Visual Prompting via Image Inpainting来说要更多一些。
      - _**引入Diffusion Model**_ 
        - In-Context Learning Unlocked for Diffusion Models（NIPS2023）这篇工作首次引入了Diffusion model来执行In-context learning。
        因为基于Inpainting的方法，需要将四个小图组成一个大图，这对于Transformer等模型来说消耗巨大。
        因此，本工作是利用controlnet，并在上下文学习中引入了Text prompt作为guidance。
        - ImageBrush（NIPS2023）：这个工作其实可以认为就是将Visual Prompting via Image Inpainting
        工作拓展到了Diffusion Model上仅此。
      - _**引入Inversion**_：Visual Instruction Inversion: Image Editing via Visual Prompting（NIPS 2023），
      这篇工作的核心是利用Inversion学习一张图编辑前后的变化情况，也可以认为是编辑方向。一旦学到了这样的编辑方向，便可以利用其配合IP2P完成query图像的编辑。


