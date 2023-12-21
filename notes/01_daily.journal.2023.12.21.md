---
id: a4clb5dr1qht7hxmm2djqim
title: '2023-12-21'
desc: ''
updated: 1703176010114
created: 1703174238520
traitIds:
  - journalNote
---
<!--
Based on the journaling method created by Intelligent Change:
- [Intelligent Change: Our Story](https://www.intelligentchange.com/pages/our-story)
- [The Five Minute Journal](https://www.intelligentchange.com/products/the-five-minute-journal)
-->



## **工作笔记**


\section{Method}

## overview

Our goal is to develop a method that efficiently customizes sub-attributes, such as shape and appearance, within a single user-provided image, enabling precise control at the attribute level for text-to-image generation.  To achieve our goal, we propose ESCDiffusion, a new method shown in Figure \ref{fig:pipeline}. We use a pre-trained encoder to capture visual features from the reference image. These features are processed separately by the shape and appearance filter modules to extract shape and appearance details. We then combine these features with word embeddings and separately inject them into the shape diffusion model and the appearance diffusion model. Fine-tuning these models helps to learn and customize specific attributes like shape and appearance.


In the following sections, we start by exploring the background of the text-to-image diffusion model and image customization in section \ref{subsec:Preliminary}. 
Following that, we introduce our method's architecture in Section \ref{subsec:Architecture}, and finally, demonstrate the technical details in Section \ref{subsec:Implementation}.


\subsection{Preliminary}
\label{subsec:Preliminary}
% 先介绍Diffusion Model
% 之后介绍Stable Diffusion Model，这里需要强调SD和Diffusion的区别。

\textbf{Stable Diffusion.} The diffusion model, a subclass of generative models, operates by progressively denoising a Gaussian prior $x_T$ to reconstruct the original data $x_0$, such as natural images. The training objective $L_{DM}(\theta)$ is defined as:

\begin{equation}
    L_{DM}(\theta) := \mathbb{E}_{t,x_0,\epsilon} \left[ \lVert \epsilon - \epsilon_\theta(x_t, t) \rVert^2 \right] \label{eq:DM}
\end{equation}
where $x_t$ denotes the noisy image formed by introducing noise $\epsilon \sim N(0, I)$ to $x_0$. The network $\theta(\cdot)$ predicts and removes this added noise. The training process of the diffusion model consists of two stages: forward diffusion and backward denoising. The forward diffusion gradually introduces noise until the image becomes pure Gaussian noise. The backward denoising reverses this process by iteratively removing noise to reconstruct the original image. During inference, the diffusion model employs neural networks, typically adopting architectures like U-Net, to estimate and eliminate noise at each step, progressively reconstructing images from random noise.

Latent Diffusion Model (LDM) \cite{rombach2022high}, preceding Stable Diffusion, introduced substantial alterations to the original diffusion model \cite{ho2020denoising}. Notably, LDM departed from directly modeling the distribution of natural images by focusing on images' projections within an autoencoder's compressed latent space. Moreover, LDM facilitated text-to-image generation by integrating encoded text input into the UNet \cite{ronneberger2015u}, denoted as $\theta(\cdot)$. The loss function for LDM is formulated as:


\begin{equation}
    L_{LDM}(\theta) := \mathbb{E}_{t,x_0,\epsilon} \left[ \lVert \epsilon - \epsilon_\theta(x_t, t, \tau_{\theta}(c)) \rVert^2 \right] \label{eq:LLDM}
\end{equation}
Here, $x$ represents the autoencoder latents for images, and $\tau_{\theta}(\cdot)$ refers to a BERT text encoder \cite{devlin2018bert} used for encoding text descriptions $c$.

Stable Diffusion\cite{rombach2022high} extends LDM by training on the larger LAION dataset \cite{schuhmann2022laion} and replacing the trainable BERT text encoder with the pre-trained CLIP text encoder \cite{}.
Our study is based on the Stable Diffusion\cite{rombach2022high} model. 


\input{articles/fig_pipeline.tex}


\textbf{Image Customization.} Current image customization methods predominantly focus on customizing global image concepts. Given several images containing specific entities, these methods aim to find text embeddings *V related to these entities for pre-trained T2I models. The obtained *V can then be utilized to generate the same entity in various scenes.

In our work, our objective is to learn the sub-attributes or sub-concepts, namely shape and appearance, of the target entity solely from a single reference image. Leveraging these obtained sub-attributes, we achieve attribute-aware controlled text-to-image generation. 



\subsection{Architecture Desgin}
\label{subsec:Architecture}

As shown in Figure \ref{fig:pipeline}, our method is composed of three stages: visual features extraction, multi-modal embeddings fusion and attribute-aware finetuning. In the following sections, we will introduce the details of each stage.

\textbf{Visual Features Extraction.} Previous methods, such as P+ and Textual Inversion, customize image concepts by optimizing a rare word token embedding. However, these approaches required multiple images and suffered from the limitation of token embeddings, constrained to a length of 768, which couldn't fully represent all image information. Therefore, inspired by E4T\cite{gal2023encoder}, we adopted a pre-trained visual encoder to extract features from single reference image. The architecture of this visual encoder is illustrated in Figure \ref{}.
The encoder combines a pre-trained Down block from Stable Diffusion UNet\cite{rombach2022high} and OpenCLIP Vit-32\cite{dosovitskiy2020image}. Using time step $\mathit{t}$ and empty text $\mathit{c'}$ as conditions, we utilize the Unet Down block to extract features from reference images. Then, OpenCLIP Vit-32\cite{dosovitskiy2020image} helps derive the CLS token embedding from the image, merging it seamlessly with the Down block's extracted features. This fusion process yields the final embedding for the current image. 


\begin{equation}
F_{down} = \epsilon_{\theta'}(x_t,t,\tau_{\theta}(c'))
\end{equation}

\begin{equation}
    embeds_{ref} = \textit{clip-v} (x_0,F_{down}) 
\end{equation}

Please refer to the supplementary materials for specific details.



\textbf{Multi-Modal Embeddings Fusion.} Our objective is to learn and customize the subattributes or subconcepts of single reference image, namely shape and appearance. However, the aforementioned visual encoder extracts global features of the image rather than the subattributes or subconcepts. Therefore, we have separately designed shape filter and appearance filter networks to filter and extract the target subattributes. Both the shape filter and appearance filter employ the same network architecture, as illustrated in Figure \ref{}. 

Taking the shape filter branch as an example, the features projected by the filter network will be merged with the embeddings of subattribute word 'shape', resulting in multimodal feature embeddings. These multimodal feature embeddings serve as the initialization for the embedding of *m. 
Unike P+\cite{voynov2023p+}, which utilized domain class-level textual word embeddings like 'dog' and 'cat' for fusion, our method employs subattribute-level words, significantly enhancing the learning and customization of image subattributes or subconcepts.
In the next step, the text prompts containing *m will be encoded using the CLIP Text Encoder and then injected as conditions into Shape Stable Diffusion for attribute-aware model fine-tuning.
The forward process for *a follows the same procedure as that for *m, as exemplified with *m.


\textbf{Attribute-Aware Finetuning.} 

Fine-tuning all parameters or specific parameters of the Unet in Stable Diffusion to achieve customized image concept generation is a common practice, 
as discussed in works such as DreamBooth\cite{ruiz2023dreambooth} and Custom Diffusion\cite{kumari2023multi}. However, these methods fail to achieve customization at the subattribute level, since they overlook the hierarchical subattribute learning capabilities of the Unet.


We observe that the encoder of the Unet predominantly learns shape information, while the decoder focuses on appearance information, as shown in Figure \ref{}. To leverage this observation and address the limitation, we present a straightforward and intuitive attribute-aware Unet fine-tuning method that requires only a single reference image. Our method is designed to be easily followed and implemented.
By utilizing the observed learning tendencies of the Unet, we propose fine-tuning only specific parts of the model for customized attribute learning. For instance, to achieve personalized shape attribute learning, we input the reference image and incorporate the embedding condition of the current text prompt. Then, we fine-tune only the encoder part of the Unet. Similarly, for personalized appearance attribute learning, we solely fine-tune the decoder part of the Unet.
This approach allows us to effectively customize shape and appearance attributes by capitalizing on the inherent learning capabilities of the Unet. Moreover, the simplicity and ease of following our method make it accessible for researchers and practitioners alike.




## **问题记录**


## **今日总结**

