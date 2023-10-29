---
id: hl8g90ehq1yp1uklwkyuavv
title: mask_loss_idea_0_outline
desc: ''
updated: 1698597799185
created: 1698393830393
---
## ShapeInversion实验概要


|               标题               |             分类             |          时间          |        是否完成        |                             详情页                             | 实验结论                                                                                                 |
| :---------------------------------: | :-----------------------------: | :----------------------: | :-----------------------: | :---------------------------------------------------------------: | ---------------------------------------------------------------------------------------------------------- |
|      标题，例如Baseline实验      | 请为此实验打tag，例如baseline |     搜狗拼音打时间     | 👍（完成）👎 （未完成） |                       请插入详细站内链接                       | 一句话总结                                                                                               |
|         E4T-Baseline实验         |           baseline           | 2023年10月25日13:06:14 |           👍           |    [[Research.Experiments.ShapeInversion.e4t_baseline_exp]]    | E4Tbaseline效果不错                                                                                      |
|         测试是否需要Mask         |          mask的影响          | 2023年10月25日13:37:14 |           👍           |      [[Research.Experiments.ShapeInversion.mask_is_need]]      | mask影响不大，但是使用mask去掉背景效果会差一些。因此，保留背景训练。                                     |
|       Mask Loss Weight实验       |             idea             | 2023年10月26日00:12:49 |           👍           |     [[Research.Experiments.ShapeInversion.mask_loss_idea]]     | 基于Cross-attention Map的Mask Loss Idea能够极大的改进shape的学习，一致性很好。但是编辑能力下降的很严重。 |
|        Mask Loss 实验分析        |             分析             | 2023年10月28日21:47:27 |           👍           | [[Research.Experiments.ShapeInversion.mask_loss_idea_analysis]] | 分析当下实验，未得出相关结论                                                                             |
| 基于Self-attention的Mask Loss实验 |             idea             | 2023年10月29日20:22:17 |           👍           |                             [[Research.Experiments.ShapeInversion.self_attn_mask_loss]]                                    | self-attention based Mask Loss效果不好，无法学习shape信息                                                |
|   Domain-tuning和Mask Loss idea   |             idea             | 2023年10月29日21:49:18 |           👍           |                                                                 |                                                                                                          |
