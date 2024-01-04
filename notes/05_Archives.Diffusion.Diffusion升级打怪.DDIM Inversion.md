---
id: 3l1bdhk5xnqamzj8ie2mj1k
title: DDIM Inversion
desc: ''
updated: 1704090438452
created: 1704085824363
---

> **自我学习整理使用，请谨慎参考**

## **Inversion 概述**

Inversion的目的是，在表示空间中，找到一个latent embedding $z$，使其能够经过生成器$G$得到目标图像。或者是说，为真实图像$X$找到一个对应的空间表示。

$$

G(z) = X 

$$

$$

G^{-1}(X) = z  

$$

## **Diffusion中的Inversion应该是什么样的？**

我们说Inversion是为了找到一个latent embedding，使其能够经过生成器得到目标图像。而对于Diffusion来说，Inversion就是找到一个噪音，使得以该噪音为起点，经过采样得到目标图像。



## **DDPM为什么不能做Inversion？**

大家耳熟能详的就是DDIM Inversion，那为什么DDPM不能做Inversion呢？首先，对于Inversion，其潜在的有两个要求：
* 反转的速度要快
* 反转的过程是确定的，不能一张图反转到了多个空间embedding

而对于DDPM来说，首先DDPM的sampling的步骤是高达1000步，其推理采样的速度是很慢的。此外，DDPM在采样的过程中，会引入噪音。这个过程无法保证inversion是确定的。




## **DDIM Inversion**

DDIM完美的解决了DDPM的两个问题，DDIM的采样速度很快，同时DDIM的采样过程是确定的，**因为$\sigma$可以设置成0**，这样在采样的过程中就不会引入任何的噪音了。

$$
x_{t-1}=\sqrt{\alpha_{t-1}^{-}}\left(\frac{x_t-\sqrt{1-\overline{\alpha_t}} \epsilon_t}{\sqrt{\overline{\alpha_t}}}\right)+\sqrt{1-\alpha_{t-1}^{-}-\sigma^2} \epsilon_t+\sigma^2 \epsilon
$$


OK，既然Inversion是为了得到图像对应的初始噪音，那么这个过程应该是怎么样的呢？其直观的数学原理是什么？代码是怎么实现的？

既然DDIM Inversion是为了得到图像的初始噪音，也就是$x_T$，那这个过程可以建模为**如何从$x_0$得到$x_T$**，而我们知道DDIM采样是规定了**如何从$x_T$得到$x_0$**，那我们只需将上面的公式折腾一番，求解出$x_t$的表达即可。因此：



$$

x_t = \frac{\sqrt{\overline{\alpha_t}}}{\sqrt{\overline{\alpha_t}-1}} (x_{t-1} - \sqrt{1-\alpha_{t-1}^{-}} \epsilon_t) + \sqrt{1-\overline{\alpha_t}} \epsilon_t

$$

有了上述的公式之后，我们只需要从给定图像$x_0$，$t=0$开始，使用预训练的模型预测噪音，不断更新$x_t$即可。


下面是代码实现：

```python

## Inversion
@torch.no_grad()
def invert(start_latents, prompt, guidance_scale=3.5, num_inference_steps=80,
           num_images_per_prompt=1, do_classifier_free_guidance=True,
           negative_prompt='', device=device):
  
    # Encode prompt
    text_embeddings = pipe._encode_prompt(
            prompt, device, num_images_per_prompt, do_classifier_free_guidance, negative_prompt
    )

    # latents are now the specified start latents
    latents = start_latents.clone()

    # We'll keep a list of the inverted latents as the process goes on
    intermediate_latents = []

    # Set num inference steps
    pipe.scheduler.set_timesteps(num_inference_steps, device=device)

    # Reversed timesteps <<<<<<<<<<<<<<<<<<<<
    timesteps = reversed(pipe.scheduler.timesteps)

    for i in tqdm(range(1, num_inference_steps), total=num_inference_steps-1):

        # We'll skip the final iteration
        if i >= num_inference_steps - 1: continue

        t = timesteps[i]

        # expand the latents if we are doing classifier free guidance
        latent_model_input = torch.cat([latents] * 2) if do_classifier_free_guidance else latents
        latent_model_input = pipe.scheduler.scale_model_input(latent_model_input, t)

        # predict the noise residual
        noise_pred = pipe.unet(latent_model_input, t, encoder_hidden_states=text_embeddings).sample

        # perform guidance
        if do_classifier_free_guidance:
            noise_pred_uncond, noise_pred_text = noise_pred.chunk(2)
            noise_pred = noise_pred_uncond + guidance_scale * (noise_pred_text - noise_pred_uncond)

        current_t = max(0, t.item() - (1000//num_inference_steps))#t
        next_t = t # min(999, t.item() + (1000//num_inference_steps)) # t+1
        alpha_t = pipe.scheduler.alphas_cumprod[current_t]
        alpha_t_next = pipe.scheduler.alphas_cumprod[next_t]

        # Inverted update step (re-arranging the update step to get x(t) (new latents) as a function of x(t-1) (current latents)
        latents = (latents - (1-alpha_t).sqrt()*noise_pred)*(alpha_t_next.sqrt()/alpha_t.sqrt()) + (1-alpha_t_next).sqrt()*noise_pred


        # Store
        intermediate_latents.append(latents)
            
    return torch.cat(intermediate_latents)

```



## **当前的SOTA DDIM Inversion方法**
* [Null-text Inversion for Editing Real Images using Guided Diffusion Models](https://arxiv.org/pdf/2211.09794.pdf)





## **参考资料**

* [扩散模型4：DDIM反转和音频扩散](https://zhuanlan.zhihu.com/p/666015077)
* [DDIM Inversion and Latent Space Manipulation](https://ucladeepvision.github.io/CS188-Projects-2023Winter/2022/03/27/team27-ddim-inversion.html)
* [扩散模型实战（十二）：使用调度器DDIM反转来优化图像编辑](https://zhuanlan.zhihu.com/p/668868277)