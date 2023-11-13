---
id: we51fxz8cwu2t3aa6o0vsb4
title: experiment_scheme
desc: ''
updated: 1699856122577
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
- [ ] **想法6:** Dianel搞了Cross-Image Attention，那  我是不是可以搞一个Cross-Feature Attention
  - [ ] **今天重点做，优先做**
- [ ] **想法7：** MasaCtrl这些文章，提到self-attention的K，V存储着该图像的appearance信息，这个信息如何利用
  - [ ] They show that keeping the keys and values of these self-attention layers fixed aids in preserving the visual characteristics of objects when applying non-rigid manipulations over a given image
- [ ] **想法8:** 我现在实现的功能都是text驱动的图像editing或者生成，我在想怎么做才能实现Image-guided的，比如给定一张图，提取shape，用到另外一张图上。或者一张图提取shape，一张图提取appearance，然后组合到另外一张图上。 
- [ ] **想法9：**我现在的结果在appearance inversion的时候，颜色也有一些不align，是否可以利用AdaIN来搞一下。

---

**2023年11月12日20:05:14 一些总结和思考**

我们目前是可以完成shape inversion，在实验的过程中，我们发现mask embed引导的token mse loss下降的很快。最终的效果也很好，那也就是说，这个损失可以作为shape inversion的很好的正则项，能够帮助从Domain class embedding中找到shape相关的信息和特征。

但是在Appearance inversion的时候，我们采用的是DINO对于图像提取的CLS特征，作为target，然后去约束Domain class embedding，目标是得到appearance有关的信息和特征。
但是在训练的过程中，我们发现，appearance regular loss几乎不下降，也就是没学到东西。我们分析，这个原因如下：
1. 首先，domain-class embedding是从Unet+CLIP-Image encoder得到的，而CLS特征是预训练的DINO，冻结固定训练得到的。这两个特征在分布和domain上存在着较大的GAP，强行的学习并不适合。
2. 所以说，直接应用DINO-CLS 特征作为图像的Appearance representation，并不能带来最好的性能。这一点是可以确定的。



