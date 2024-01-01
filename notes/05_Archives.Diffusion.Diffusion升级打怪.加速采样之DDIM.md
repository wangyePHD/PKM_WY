---
id: kif779ncs4m3pibj8vcat82
title: 加速采样之DDIM
desc: ''
updated: 1704043867559
created: 1704002807918
---

> **注：本文是作为自我学习和理解使用，有些观点不一定正确。请慎重参考**


## DDPM的基本原理和弊端

对于DDPM，我们推导其采样目标的路线为：

$$
p\left(\boldsymbol{x}_t \mid \boldsymbol{x}_{t-1}\right) \stackrel{\text { 推导 }}{\longrightarrow} p\left(\boldsymbol{x}_t \mid \boldsymbol{x}_0\right) \stackrel{\text { 推导 }}{\longrightarrow} p\left(\boldsymbol{x}_{t-1} \mid \boldsymbol{x}_t, \boldsymbol{x}_0\right) \stackrel{\text { 近似 }}{\longrightarrow} p\left(\boldsymbol{x}_{t-1} \mid \boldsymbol{x}_t\right)
$$

同时，我们是利用贝叶斯定理：

$$
p\left(\boldsymbol{x}_{t-1} \mid \boldsymbol{x}_t, \boldsymbol{x}_0\right)=\frac{p\left(\boldsymbol{x}_t \mid \boldsymbol{x}_{t-1}\right) p\left(\boldsymbol{x}_{t-1} \mid \boldsymbol{x}_0\right)}{p\left(\boldsymbol{x}_t \mid \boldsymbol{x}_0\right)}
$$

实现，$x_t$到$x_{t-1}$的去噪推理。

由于DDPM依赖于马尔科夫链进行加噪，那么在去噪的过程中也需要计算 $p\left(\boldsymbol{x}_t \mid \boldsymbol{x}_{t-1}\right)$，同理其去噪的过程同样收到马尔科夫链的影响，需要逐步降噪。如果总时间步是1000的话，那就需要迭代1000次才能实现，这样的采样速度是非常慢而不能接受的。




## DDIM的原理和数学推导（直观）

DDIM的核心原理就是摆脱了马尔科夫链的限制，使得其在采样的时候，不必一步一步地去噪，而是可以跳步去噪，这样就加快了采样速度。

下面我们看一下DDIM的数学推导，在这里我们主要是以直观为主：

从贝叶斯公式出发，为了令DDIM不依赖于马尔科夫过程，我们在求解$p\left(\boldsymbol{x}_{t-1} \mid \boldsymbol{x}_t, \boldsymbol{x}_0\right)$的时候，可以不计算$p\left(\boldsymbol{x}_t \mid \boldsymbol{x}_{t-1}\right)$，那么这样，我们就不需要逐步的去降噪了。

OK，那我们直接将假设：

$$
\begin{aligned}
& P\left(x_{t-1} \mid x_t, x_0\right) \sim N\left(k x_0+m x_t, \sigma^2\right) \\
& x_{t-1}=k x_0+m x_t+\sigma \epsilon \epsilon \sim N(0,1)
\end{aligned}
$$

这样的话，我们就可以直接将$x_{t-1}$表示成一个正态分布，而不是依赖于贝叶斯定理，中间借助马尔科夫链来求解。

又因为加噪公式为：

$$
x_t=\sqrt{\overline{\alpha_t}} x_0+\sqrt{1-\overline{\alpha_t}} \epsilon, \epsilon \sim N(0,1)
$$

因此，可将$x_t$代入上式并进行化简：

$$
\begin{gathered}
x_{t-1}=k x_0+m\left[\sqrt{\bar{\alpha}_t} x_0+\sqrt{1-\overline{\alpha_t}} \epsilon\right]+\sigma \epsilon \\
x_{t-1}=\left(k+m \sqrt{\overline{\alpha_t}}\right) x_0+\epsilon^{\prime}, \epsilon^{\prime} \sim N\left(0, m^2\left(1-\overline{\alpha_t}\right)+\sigma^2\right)
\end{gathered}
$$


那由前向加噪公式，我们可以得到$x_{t-1}$的表示：

$$
x_{t-1}=\sqrt{\overline{\alpha_{t-1}}} x_0+\sqrt{1-\overline{\alpha_{t-1}}} \epsilon
$$


OK，我们只需要满足对应系数相等：

$$
\begin{gathered}
k+m \sqrt{\bar{\alpha}_t}=\sqrt{\alpha_{t-1}^{-}} \\
m^2\left(1-\overline{\alpha_t}\right)+\sigma^2=1-\alpha_{t-1}^{-}
\end{gathered}
$$

求得：

$$
\begin{gathered}
m=\frac{\sqrt{1-\alpha_{t-1}^{-}-\sigma^2}}{\sqrt{1-\overline{\alpha_t}}} \\
k=\sqrt{\alpha_{t-1}^{-}}-\frac{\sqrt{1-\alpha_{t-1}^{-}-\sigma^2}}{\sqrt{1-\overline{\alpha_t}}} \sqrt{\overline{\alpha_t}}
\end{gathered}
$$

因此：

$$
\begin{aligned}
& P\left(x_{t-1} \mid x_t, x_0\right) \sim N\left(\left(\sqrt{\alpha_{t-1}^{-}}-\frac{\sqrt{1-\alpha_{t-1}^{-}-\sigma^2}}{\sqrt{1-\overline{\alpha_t}}} \sqrt{\overline{\alpha_t}}\right) x_0+\left(\frac{\sqrt{1-\alpha_{t-1}^{-}-\sigma^2}}{\sqrt{1-\overline{\alpha_t}}}\right) x_t, \sigma^2\right) \\
& \sim N\left(\sqrt{\alpha_{t-1}^{-}} x_0+\sqrt{1-\alpha_{t-1}^{-}-\sigma^2} \frac{x_t-\sqrt{\bar{\alpha}_t} x_0}{\sqrt{1-\overline{\alpha_t}}}, \sigma^2\right)
\end{aligned}
$$

接下来，我们把$x_0$ 替换成$x_t$表示：

$$
\begin{array}{r}
x_0=\frac{x_t-\sqrt{1-\overline{\alpha_t}} \epsilon_t}{\sqrt{\overline{\alpha_t}}}
\end{array}
$$

$$
\begin{array}{r}
\epsilon_t=\frac{x_t-\sqrt{\overline{\alpha_t}} x_0}{\sqrt{1-\overline{\alpha_t}}}
\end{array}
$$


最后，得到采样的最终形式：

$$
x_{t-1}=\sqrt{\alpha_{t-1}^{-}}\left(\frac{x_t-\sqrt{1-\overline{\alpha_t}} \epsilon_t}{\sqrt{\overline{\alpha_t}}}\right)+\sqrt{1-\alpha_{t-1}^{-}-\sigma^2} \epsilon_t+\sigma^2 \epsilon
$$

需要注意的是，我们整个推导的过程中，并没有使用和依赖马尔可夫过程。那也就是说此时$x_{t-1}$，并不是严格的从$x_t$到$x_{t-1}$，而是通用的代表着以前的任一时刻：$x_{prev}$。因此，一般化的公式如下：

$$
x_{\text {prev }}=\sqrt{\alpha_{\text {prev }}}\left(\frac{x_t-\sqrt{1-\overline{\alpha_t}} \epsilon_t}{\sqrt{\overline{\alpha_t}}}\right)+\sqrt{1-\alpha_{\text {prev }}^{-}-\sigma^2} \epsilon_t+\sigma^2 \epsilon
$$




## DDIM加速采样





## DDIM 和 DDPM 对比




## DDIM Inversion技术










## **参考资料**

* [DDPM与DDIM简洁版总结](https://www.bilibili.com/video/BV1Bh4y1E7vZ/?spm_id_from=333.337.search-card.all.click&vd_source=45b600ad98b8c54b21b9561915c1ba61)
* [生成扩散模型漫谈（四）：DDIM = 高观点DDPM](https://kexue.fm/archives/9181)
* [一文带你看懂DDPM和DDIM（含原理简易推导，pytorch代码）](https://zhuanlan.zhihu.com/p/666552214)
* [扩散模型之DDIM](https://zhuanlan.zhihu.com/p/565698027)


