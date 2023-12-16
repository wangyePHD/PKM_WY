---
id: tn8a1agtj0jjzwbvtufa5uu
title: 20231215个人会议
desc: ''
updated: 1702648858740
created: 1702560795659
marp: true
---


## **汇报大纲**
* 当前的解决方案
* 当前的初步结果
* 与相关工作的比较
* 下一步的优化方向

---


## **当前的解决方案**

### Insight
* Stable Diffusion中的UNet能够储存一张图像的所有信息，包括shape和appearance，但是这些信息分布在UNet的不同区域。**只要针对特定区域进行微调，即使仅给定一张图像，也可以学习到appearance和shape信息。**
* UNet中的**Down block**负责学习**shape和结构信息**
* UNet中的**Up block**负责学习**appearance和外观信息**

    ![图 0](assets/images/499cc7ddca4f38080e9493a65fac937dc2241f392cfd21e5d9c58979674dcc1c.png)  

---

## **当前的解决方案**

### **实验验证**
* 输入一张reference图像，分别微调Down、Up blocks，然后输入测试文本a cat in the appearance of *a. 观察实验现象：

![图 3](assets/images/69d47cafa3163433333718c2b553eda7058ceba6ae866f9a92614a1524ebe5cd.png)  

![图 4](assets/images/2c9305d620c2b1956259d1983ec0afeaec3e6863a8d05ffdfec5e8a2b45e9fd7.png)  

![图 5](assets/images/73bbe135248911ab892cba2caed7057c8651b2d89bd9b6b863b75fcb5f389104.png)  


* 可以发现，**Down block**负责学习给定参考图像的**shape和结构信息**。
* **Up Block**负责学习给定参考图像的**appearance信息**。

### **方法架构**

![图 6](assets/images/520aed8f5a7ced8e7dbee382aa1ac77d0509b9e52c7a69d7b7a610fb5eb1780a.png)  

---
## **当前的实验结果**



### **Appearance Inversion**

![图 9](assets/images/a6b4aaf5d009bb659cfd6ba6c12d2a760db8a920252d3845acb6187ecee7e6c3.png)  

![图 10](assets/images/e1a25a37e10387d29c2d9a274658931294b88ecfc62bad6d97fa527fa31e75b6.png)  

![图 11](assets/images/490ec6f159aef83b12e6d9d5379de17631cc3ea5153260045baaccc0b91a04a8.png)  


### **Shape Inversion**

* 待定


---

## **与相关工作的比较**

对于关注subconcept inversion或者学习的工作，主要是以下三篇工作：
* P+
* Prospect
* MATTE

详细的对比情况如下：

![图 7](assets/images/263adf2af1805ded8c8c6e4435abdb4e8312b1244c2d148f1f2441fb7f7adb6d.png)  

我们是第一个能够实现：

**在仅给定一张参考图像的情况下，实现appearance和shape子概念学习**


---

## **下一步的优化方案**

* **属性驱动的噪音初始化**
  * 有一些文章认为标准的高斯噪音，并不一定适合学习。**因此，设计特定属性分布的Noise可能更合适**
  * ![图 8](assets/images/9fccf275725d089870c296b411f5a17fb772b815f2aa64debe0a2cc501ceacf4.png)  

* **进一步减小过拟合的影响**
  * 

---

## 和马老师讨论记录
* Unet中的Encoder--》CNN Low level feature
* Unet中得Decoder--》恢复图像，细节信息
* 微调的是特定的网络模块或者layers
* 确定到shape和appearance
* 跨类别要大：
  * 如果给定奶牛，如果能够做到跨物种，跨类别的话，比如直接应用到椅子上。
  * 如果给定任意的mask，能否得到满足mask shape要求的生成图像 猫 狗

* 两个事情
  * 华为周三交流，为深入交流做准备，展示更多的结果 PPT，21号下周四下午2.15-4.00 , 扩展到5-6页，bkg，related work，limitation，method，results。
  * 我的文章，张轶博的文章，郑王的文章，1月份老师时间充裕，新加坡那个博后参与进来。和王浩的相关性比较大。

准备ECCV。需要帮手尽早引入。