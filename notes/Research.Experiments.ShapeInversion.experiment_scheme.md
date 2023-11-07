---
id: we51fxz8cwu2t3aa6o0vsb4
title: experiment_scheme
desc: ''
updated: 1699370323150
created: 1699369889624
---

## **下一阶段实验方案**
**下一阶段的实验重点还是回归到如何Inversion Appearance 属性**。而不是将shape Inversion和style inversion合并到一起做，这是因为，根据之前的文章，多个token一起inversion也会有很多坑。

### **一些想法**

* **想法1**：从slicing Vision Transformer及后续工作DIFFUSION-BASED IMAGE TRANSLATION USING DISENTANGLED STYLE AND CONTENT REPRESENTATION（ICLR2023）, 我发现这些论文都是利用DINO-ViT的CLS特征来表示Appearance。我们也打算这么尝试一下。
* **想法2**：从Cross-Image Attention论文及Masactrl，TokenFlow，InFusion这些工作中，都是利用了Self-Attention冻结K，V，使得Appearance得以保持。我在想能否在这上面下一些功夫。这样的话，shape就是cross-attention，Appearance就是靠self-attention。从解法上来看，非常对称。






 