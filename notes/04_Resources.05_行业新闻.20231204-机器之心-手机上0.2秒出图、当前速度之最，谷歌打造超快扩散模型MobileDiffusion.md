---
id: hq8l7lhehrz0usrttes74dm
title: 20231204-机器之心-手机上0.2秒出图、当前速度之最，谷歌打造超快扩散模型MobileDiffusion
desc: ''
updated: 1701709029100
created: 1701680247998
---


### 概述与总结

这篇文章介绍了谷歌团队最新研发的「MobileDiffusion」模型，该模型在**移动设备上实现了超快的文本到图像生成速度，仅需0.2秒即可完成一张图像的生成**。MobileDiffusion通过优化大型扩散模型的核心组件UNet和采用新颖的技术路径，解决了当前大模型在移动端运行的计算速度慢、资源需求大的问题。该模型在 iPhone 15 Pro 上进行测试，呈现出极为出色的性能。

### 详细记录

#### MobileDiffusion模型的优化路径：
1. **问题背景与优化需求：**
   - 扩散模型在图像生成领域表现出色，但其大量参数导致计算速度慢，尤其在资源有限的移动端；
   - 多步采样导致推理速度缓慢，限制了移动端应用场景。

2. **MobileDiffusion的优化策略：**
   - 核心组件UNet的优化：精简Convolution和提高Attention效率，将Transformer放在低分辨率特征图上，极大提升运算效率。
   - 微观设计：Decouple Self-Attention and Cross-Attention、Finetune softmax into relu、Separable Convolution等新颖设计，有效减少模型参数、提升运算效率。
   - 采样优化：验证Progressive Distillation和UFOGen的适用性，模型在经过优化后，采样步数8步和1步均有显著性能提升。

3. **MobileDiffusion的实验与应用：**
   - 移动端基准测试：在iPhone 15 Pro上实现了0.2秒一张图像的超快生成速度，为当前移动设备上最快。
   - 下游任务测试：在ControlNet/Plugin和LoRA Finetune等下游任务中保持了优秀的微调性能。

4. **结论与展望：**
   - MobileDiffusion探索了多种模型和采样优化方法，实现了亚秒级的移动端图像生成能力；
   - 未来该优化方法可能对高效的扩散模型设计产生重要影响，并为移动端应用提供了新的可能性。

这篇文章详细介绍了MobileDiffusion模型的优化路径和在移动设备上的出色表现，为后续在移动端运行大型AI模型提供了新思路与可能性。

#Diffusion_加速