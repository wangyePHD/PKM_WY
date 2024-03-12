---
id: 7t6xl89ub56ao7h4rdj6zqw
title: 定量结果记录
desc: ''
updated: 1705544293935
created: 1705544259525
---
## Appearance 结果


|      Method      | clip I-T score | DINO score | Average Score |
| :----------------: | :--------------: | :----------: | :-------------: |
| Stable Diffusion |     0.2854     |   0.2596   |    0.2729    |
|    Dreambooth    |     0.2681     |   0.2671   |    0.2676    |
| Custom Diffusion |     0.2710     |   0.2977   |    0.2837    |
|     Prospect     |     0.2800     |   0.3849   |    0.3242    |
|                 |               |           |               |
|       Ours       |     0.2822     |   0.4149   |    0.3359    |

## Shape 结果


|      Method      | CLIP I-T Score | Mask IoU Score | Average Score |
| :----------------: | :--------------: | :--------------: | :-------------: |
| Stable Diffusion |     0.2380     |     0.3418     |    0.2806    |
|    Dreambooth    |     0.2791     |     0.3524     |    0.3115    |
| Custom Diffusion |     0.2844     |     0.3691     |    0.3213    |
|                 |               |               |               |
|     Prospect     |     0.2795     |     0.4656     |    0.3493    |
|       Ours       |     0.2798     |     0.4938     |    0.3572    |

---

## 消融实验



|     Method     | DINO Score | Mask IoU Score |
| :---------------: | :----------: | :--------------: |
|      ours      |   0.4149   |     0.4938     |
| No Hypernetwork |   0.2596   |     0.3418     |
| 没有多模态融合 |           |               |
| 没有视觉Encoder |           |               |
