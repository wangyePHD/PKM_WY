---
id: vj85x2gnpmgia331702upms
title: e4t架构下baseline实验
desc: ''
updated: 1698396559813
created: 1698394044081
---
- [**实验概述**](#实验概述)
- [**Wandb实验信息**：](#wandb实验信息)
- [**实验代码备份：**](#实验代码备份)
- [**Bug排除及注意事项：**](#bug排除及注意事项)
- [**测试的结果如下：**](#测试的结果如下)




## **实验概述**
使用E4T架构进行实验，对其代码进行适配操作。训练所用的数据集为chair图像数据，共100张图像用于训练。本次实验的实验信息及参数配置可访问如下链接。（此wandb project有两个实验，origin和shape，分别是使用不同的template进行训练的。前者是标准的*s chair形式，后者是chair in the shape of *s形式）

## **Wandb实验信息**：

[https://wandb.ai/wangye889905/e4t?workspace=user-wangye889905](https://wandb.ai/wangye889905/e4t?workspace=user-wangye889905)

## **实验代码备份：**

[https://wandb.ai/wangye889905/e4t?workspace=user-wangye889905](https://wandb.ai/wangye889905/e4t?workspace=user-wangye889905)

在上述链接中，可访问每个run下面的code页面，云端代码已存储

其次，也可以访问github上的release（推荐）:

[https://github.com/wangyePHD/ShapeInversion/releases/tag/baseline](https://github.com/wangyePHD/ShapeInversion/releases/tag/baseline)

## **Bug排除及注意事项：**
这次最大的bug就是E4T架构在pretraining之后，domain-tuning的时候对batchsize的要求极为苛刻，在4*A40的情况下，**batchsize越大效果越好（bsz=2 per-device是最大设置，也能实现最优效果）这个bug排查了3天，TMD！**

## **测试的结果如下：**
![](/assets/images/2023-10-27-16-09-07.png)



