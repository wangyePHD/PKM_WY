---
id: we51fxz8cwu2t3aa6o0vsb4
title: experiment_scheme
desc: ''
updated: 1699584976780
created: 1699369889624
---

## **下一阶段实验方案**
**下一阶段的实验重点还是回归到如何Inversion Appearance 属性**。而不是将shape Inversion和style inversion合并到一起做，这是因为，根据之前的文章，多个token一起inversion也会有很多坑。

### **一些想法**

- [x] **想法1**：从slicing Vision Transformer及后续工作DIFFUSION-BASED IMAGE TRANSLATION USING DISENTANGLED STYLE AND CONTENT REPRESENTATION（ICLR2023）, 我发现这些论文都是利用DINO-ViT的CLS特征来表示Appearance。我们也打算这么尝试一下。
  - [x] 已验证，效果不错。
- [ ] **想法2**：从Cross-Image Attention论文及Masactrl，TokenFlow，InFusion这些工作中，都是利用了Self-Attention冻结K，V，使得Appearance得以保持。我在想能否在这上面下一些功夫。这样的话，shape就是cross-attention，Appearance就是靠self-attention。从解法上来看，非常对称。
- [ ] **想法3：** 如果shape和appearance放到一起学，会出现问题。那为什么不先学shape，然后在学好shape的基础上固定shape，去学appearance呢？那这样的话，可以为shape搞一个weight offset，然后为style搞一个weight offset？
- [ ] **想法4：**是否可以利用CLS的特征进行cross-attention的query 
- [ ] **想法5：**splicing ViT文章中用了Key self-similarity matrix来保持结构，这一点是否可以扩展使用一下
- [ ] **想法6:** Dianel搞了Cross-Image Attention，那我是不是可以搞一个Cross-Feature Attention
  - [ ] **今天重点做，优先做**
- [ ] **想法7：** MasaCtrl这些文章，提到self-attention的K，V存储着该图像的appearance信息，这个信息如何利用
  - [ ] They show that keeping the keys and values of these self-attention layers fixed aids in preserving the visual characteristics of objects when applying non-rigid manipulations over a given image

 

s