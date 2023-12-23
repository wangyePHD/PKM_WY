---
id: 1nm5bk34jdnb4pfhq3oluqr
title: 科研经验积累
desc: ''
updated: 1703312228142
created: 1701405582493
---

# **科研心态篇**

## **刻苦不等于高效科研**

原链接：https://www.zhihu.com/question/621912340/answer/3308865761

![图 0](assets/images/8ace816332abeb3b430d6017cfac8a76606bff2fef7061872fd71fb5e636442e.png)  



---


# **方法论**


## 如何从浩如烟海的文献中走的进来，带的出去？

* **走进来**：
  * 使用Arxiv阅读每日更新的论文，时刻跟进前沿进展
  * 使用markdown文件，维护一个感兴趣领域、或者热门领域的paper list，根据每天的新论文，填充进去
  * 使用readpaper在线收藏重点文章，进行分类
  * 设置一个**“我想读”**的文件夹，专门用来保存，自己想读的文章，提醒自己后续进行泛读
  * 定期清理**"我想读"**文件夹里的内容，时常翻看和阅读

* **带出去**：
  * 使用AI阅读文章整体情况，有一个具体的把控。
  * 根据上述整体的了解，快速看teaser，pipeline图，理解其做的事情
  * 快速阅读abstract和introduction部分，了解故事梗概
  * 如果还是很感兴趣，读method细节。
  * 最后简单看一下实验效果


* **案例**
  * 论文走进来带出去-倒金字塔模型
  * 

## 科研思路
* **旧问题：从代码出发，测试当前某类方法的共性问题，设计解法去解决问题：**
  * 我发现很多文章，比如Compositional Inversion for Stable Diffusion Models这篇工作，大概率是从当前算法的测试结果来看，有哪些问题这些方法做不了，然后去解决这些问题。光看论文的话，就会让人感觉很多问题都被做了。所以还是要从代码出发，大量测试，找到这些方法的共性问题。然后解决。
    * 这些文章还包括，从ControlNet出发，发现其问题，然后改进的工作：
      * FineControlNet: Fine-level Text Control for Image Generation with Spatially Aligned Text Control Injection
      * Local Conditional Controlling for Text-to-Image Diffusion Models
    * 其实这就说明，我们一定要从代码实践出发，发现问题，然后总结规律，解决问题，形成论文。
* **新问题：提出新问题，找到可解得方案，迅速完成文章：**
  * 待补充






