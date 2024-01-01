---
id: wzk58ceytvl1uy6ngplmc9j
title: Diffusion升级打怪
desc: ''
updated: 1704000910203
created: 1702643783495
---

> 从今天开始正式从头开始学习Diffusion，包括数学原理，关键论文，底层代码，当前的小领域进展，论文总结等。
>

## **进展情况**
* 基于李宏毅老师的视频，DDPM、VAE的底层数学原理已经弄懂了


## **参考资料**：

* **知乎**
  * https://zhuanlan.zhihu.com/p/605973097
    ![图 0](assets/images/66a8218c0717a7c0d5dbe41f1a949ce4ad4334ffee6e4eccd520c57949df29e2.png)  
  * https://zhuanlan.zhihu.com/p/670174195
    ![图 1](assets/images/3362fb9f5a46269869cde9e4d555ffa8c8b86dfc78f8a21b24292ff4e60c3bc4.png)  

* **Blog**
  * Lilian Weng的博客: https://lilianweng.github.io/posts/2021-07-11-diffusion-models/

* **Tutorial**
  * https://flowus.cn/wangye123/d9fa948f-e692-4963-9ea0-c6ad365d4af3 (Valse 2023, Diffusion教程)
    * ![图 3](assets/images/0f31b71daafc3de9aa97f4510fa4d030b13536b15f8a5ff028f1ab8e7b1e3e2b.png)  

  * https://neurips2023-ldm-tutorial.github.io/ （NIPS2023 tutorial）
    * ![图 2](assets/images/2c002cda3e456cb8a4db4ce0f0ad21d3283175493899f0026452228e08cf5f9f.png)  

* **Slides**
  * [UNC课程](https://www.cs.unc.edu/~ronisen/teaching/fall_2022/pdf_lectures/lecture8_diffusion_model.pdf)
  * [CS231n](http://cs231n.stanford.edu/slides/2023/lecture_15.pdf)
  * [李宏毅](https://speech.ee.ntu.edu.tw/~hylee/ml/ml2023-course-data/DDPM%20(v7).pdf)
  * [Mike视频Diffusion](https://www.dropbox.com/scl/fi/u7jgodz3tz01bzd5uftog/Video-Diffusion-Tutorial-Prof-Mike-Shou-NUS-2023-Dec-15.pdf?rlkey=de6axl9dnjhz1ub0wmpwmpq4f&dl=0)

* **Code实践**
  * https://github.com/huggingface/diffusion-models-class（Huggingface课程）


* **Awesome**
  * https://github.com/showlab/Awesome-Video-Diffusion
---

## **学习路线** 
1. [x] 📚🧠📖先学习李宏毅的视频课程，学习Diffusion Model的数学原理 📚🧠📖
   1. 笔记在readpaper 
2. [x] 学习Conditional diffusion models的基础知识，技术
   1. Classifier guidance
   2. Classifier-free guidance
   3. https://sander.ai/2022/05/26/guidance.html
3. accelerate sampling process
   1. DDIM
   2. LCM
4. 领域分类，代表工作
   1. T2I
   2. I2I
   3. Image Editing
   4. Video




## **学习笔记**
* [[05_Archives.Diffusion.Diffusion升级打怪.李宏毅-Diffusion的数学原理]]