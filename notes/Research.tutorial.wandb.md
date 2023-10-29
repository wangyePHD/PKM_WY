---
id: 1itmvrsd419mgpb3vxg41rb
title: 如何利用wandb高效管理Deep Learning实验？
desc: ''
updated: 1698568339911
created: 1698562365814
---
- [**Wandb简介**](#wandb简介)
- [**Wandb都能做什么呢？**](#wandb都能做什么呢)
  - [**可视化**](#可视化)
  - [**多实验对比**](#多实验对比)
  - [**云端存储**](#云端存储)
  - [**实验报告**](#实验报告)
- [**如何使用Wandb呢？**](#如何使用wandb呢)
  - [**注册账户**](#注册账户)
  - [**安装Wandb**](#安装wandb)
  - [**开始使用**](#开始使用)
- [**Pytorch+Wandb实现高效实验管理**](#pytorchwandb实现高效实验管理)

---

## **Wandb简介**

[Wandb](https://wandb.ai/site)是一个高效的、功能丰富的人工智能实验管理平台，是帮助我们训练深度学习、机器学习模型的科研利器。基于Wandb，你可以高效的管理你的实验，对比多个实验，可视化实验结果，总之，有了Wandb之后，我们进行和管理实验的效率将会提高10倍以上。

![Wandb概览](assets/images/a20d3b92248174af4092e0fdbb56323d0d5c6a33692e8834f9783e56e2b7232e.png)  

---

## **Wandb都能做什么呢？**

### **可视化**
* Wandb可以可视化你想可视化的一切事物，比如基础的Loss曲线，Acc曲线，学习率变化曲线等，同时还可以进阶监视参数梯度的信息，掌控模型训练。(下图：左图为loss曲线，右图为模型参数的梯度直方图)

![图 1](assets/images/7a582b07e919524425fb062d90e557eacf1e729859ab99942a3186623cc3647f.png)| ![图 2](assets/images/3307d44ffc19e8c8e2ced978ad49987f911e37509ceffa6a1047ec5ad6a38dd4.png)  
---|---


### **多实验对比**
* 多实验对比的应用场景例如：**当你使用不同的参数训练一个模型，需要比较各自参数设置下的模型的性能**，这个时候，Wandb就非常有用了。如下图所示。
![图 3](assets/images/081687eafa3051683e0dd81ca6fb10f57faa1eff0db2b48dfcb8ef7bf11516de.png)  

* 除了对比训练曲线外，你还可以对比多次实验的参数配置。想象一种情况，你跑了很多参数的实验，每个实验的参数都是在本地存储，很容易混乱。但是，有了Wandb之后，一切都变得清晰可见。
![图 4](assets/images/ab4b25a57165c696f1e7829639559b302cbb5766f0478bf9d23523940e8c4170.png)  

### **云端存储**
* 这个功能是Wandb最实用的功能之一。想象一下，你跑了N组实验，每次实验的代码都是不同的，参数也是不同，很容易混乱掉，而无法复现出最好的实验结果。Wandb可以完全避免掉这样的问题，因为Wandb可以将你每次实验的参数、日志、代码、甚至硬件信息全部储存到云端，这样你无需刻意管理代码及参数的备份，只要你想复现出上次实验的结果，你就可以找到wandb上对应的实验，然后下载代码，100%复现你的实验。** (放心，每人云端的空间是100GB，够用)**

![图 5](assets/images/50dc14ae2525f2f0024d921a472026a82a3982c0ae7fd88eabea412138695c6c.png)|![图 6](assets/images/edb1b03632e04b8b67da6305b7fb33af569bd3dee05a1fdc9bbe72c84d7f5079.png)|![图 8](assets/images/4957ce98146bba26ee5d443b8da149b651c0c6334c462be912d3d3fc166ebfdf.png) 
---|---|---

### **实验报告**
* 这个功能的核心，就是能够让你在Wandb的网站上，为每个实验都创建一个report markdown文档，你可以在云端编写，非常酷炫。不过我个人还是习惯在本地写实验总结和分析。

---

## **如何使用Wandb呢？**

> 以下教程参考了wandb官网文档，可[点击访问](https://docs.wandb.ai/quickstart)

为了使用Wandb，你需要做以下几步：
1. 注册账户
2. 安装Wandb
3. 开始使用

### **注册账户**
请访问[链接](https://wandb.ai/site)，进行注册。
![图 9](assets/images/e5910ccb487aa8765dec82f0345243b3997c2dd3769076bce5df6b7d5d5912a9.png)  

 
### **安装Wandb**
傻瓜式安装：
```bash
conda activate your env
pip install wandb
```

### **开始使用**
```python
# train.py
import wandb
import random 

wandb.login()

epochs=10
lr=0.01

run = wandb.init(
    # 此处设置你的项目名
    project="my-awesome-project",
    # 此处配置需要Wandb帮你记录和track的参数
    config={
        "learning_rate": lr,
        "epochs": epochs,
    })

offset = random.random() / 5
print(f"lr: {lr}")

# 模拟训练的过程
for epoch in range(2, epochs):
    acc = 1 - 2 ** -epoch - random.random() / epoch - offset
    loss = 2 ** -epoch + random.random() / epoch + offset
    print(f"epoch={epoch}, accuracy={acc}, loss={loss}")
    wandb.log({"accuracy": acc, "loss": loss})
```
请在命令行运行此脚本：
```bash
python train.py
```
首先，Wandb会提示你login，你需要根据提示中得链接，copy到你的apikey，然后复制粘到此即可。
![图 10](assets/images/296341dd96e32466ca63cbf001fec254154daa0614f61cadcac9b91c8f3f4ef9.png)  
成功后，如下图。
![图 11](assets/images/7b142ac7e1dc92634f2e0b317e523ecd1d07d8105c5fb26f5209147a2d925055.png)  

OK，现在可以打开链接看一下我们的实验是怎么被记录的。
![图 12](assets/images/8f1ea406a3da8b9be4ba8f785a0595ad53357a2cb137a2b96cec638faf2dff8b.png)  

接下来，我们跑多次实验，看一下可视化的结果如何，我们重复运行三次上述脚本。
![图 13](assets/images/f065bd2a5289134758dcc34401511f961080875aab0a24fdf4dd6764b17d45e3.png)  


<font color="red">**请注意，project和run是有区别的，project是一个总体的概念，比如你要验证学习率对模型的影响，这个时候你可以建立一个project，比如lr_project。为了验证lr的影响，你需要设置不同的lr，来跑实验，这里每个lr对应的实验，在Wandb中被称为是一次run。**</font>



## **Pytorch+Wandb实现高效实验管理**
ToDo