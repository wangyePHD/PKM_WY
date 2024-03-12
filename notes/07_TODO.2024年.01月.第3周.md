---
id: qmg72zh56q675lx4mr3eukm
title: 第3周
desc: ''
updated: 1705584971552
created: 1705281193499
---


## 2024年1月15日

## TODO


## Doing




## Done
* Teaser图绘制，优秀案例寻找，模仿绘制
* 定型试验画图
* Arxiv论文整理
* prospect shape inversion 定性实验 全部搞定


## Backlog
* neural body 写作风格整理，模板化。
* P+定型试验全部搞定
* P+代码运行，调试
* SD 构建baseline，思考
* 整理自己之前学习过的Diffusion课程内容


---

## 2024年1月16日

## TODO



## Doing


## Done
* 多样性实验画图
* Prospect对比的定性实验结果 画图搞定
* bash _shape_inversion.sh 0 triangle triangle
* bash _shape_inversion.sh 1 bird2 bird
* bash _shape_inversion.sh 2 sitting woman
* bash _shape_inversion.sh 3 walking man
* bash _shape_inversion.sh 2 dotdog dog

## Backlog
* P+定型试验全部搞定, P+代码运行，调试,
* neural body 写作风格整理，模板化。
* 整理自己之前学习过的Diffusion课程内容
* 公众号浏览 记录


---





## 2024年1月17日

## TODO
* 定性实验结果图 绘制
* 消融实验进行
  * 正则损失是否有必要
  * 其他项推进
* 定量实验推进
  * 如何做，参考Prospect的做法



## Doing


* Stable Diffusion Appearance 测试结果整理
  * 训练
  * 测试
  * 整理


* 写测试代码
  * 整图切割脚本
  * DINO 测试Appearance 相似性分数 
    * ours 0.4149
    * prospect 0.3848792767621637
    * stablediffusion 0.25957962386007233
  * CLIP 图文相似度分数
    * Appearance 测试结果
      * ours 0.2925
      * prospect 0.2891



## DONE
* Arxiv 16更新
  * 官网无更新
* 公众号浏览
  * https://mp.weixin.qq.com/s/tlOWaMi0e6By__MUT414xA
  * https://mp.weixin.qq.com/s/LOuWukV0jBs8zEtoP05FkQ
  * https://mp.weixin.qq.com/s/5QaOIprTfaDpitPYMw2s4Q
  * https://mp.weixin.qq.com/s/csqBozijH8jcOSzyWLDk8g
  * https://huggingface.co/spaces/modelscope/ReplaceAnything
  * https://arxiv.org/pdf/2312.04461.pdf
* Stable Diffusion Baseline 实验结果整理
* P+代码研究，是否合适作为Baseline(不适合)
* 挑选自己的测试结果
  * appearance 测试结果 整理完毕
  * shape 测试结果 整理完毕
* 写脚本，训练Prospect，测试其余数据，然后生成对应数量的图像

## Backlog 

* Stable Diffusion appearance 测试图片重命名
* 重命名图片 DINO CLIP 测试
* **_上述测试完毕，appearance inversion定量实验全部搞定_**
* 公众号整理
  * https://mp.weixin.qq.com/s/tlOWaMi0e6By__MUT414xA
  * https://mp.weixin.qq.com/s/LOuWukV0jBs8zEtoP05FkQ
  * https://mp.weixin.qq.com/s/5QaOIprTfaDpitPYMw2s4Q
  * https://mp.weixin.qq.com/s/csqBozijH8jcOSzyWLDk8g
  * https://huggingface.co/spaces/modelscope/ReplaceAnything
  * https://arxiv.org/pdf/2312.04461.pdf

---

## 2024年1月18日

## TODO




## Doing





## Done

* 测试脚本撰写
  * 参考图padding到1：1，然后 文本驱动SAM分割主体
  * 分割不好的个例 手动分割
  * 求解主体质心，移动到512*512的图像中心
  * 分割生成图像，得到主体
  * 求解主体质心，移动到512*512的图像中心
  * 求解IoU Score
  * Mask IoU分数
    * prospect
    * ours
    * 
* Stable Diffusion appearance 测试图片重命名
* DINO CLIP 测试
  * SD 0.2854
  * Prospect 0.2800
  * Ours 0.2822
* prospect shape 测试
  * CLIP Text-Image相似度
    * prospect 0.2795
    * ours 0.2798
* 昨日Arxiv整理
* * 整理Shape IoU Score 计算流程

## Backlog
* shape inversion实验  
  * stable diffusion 训练
  * stable diffusion 测试
  * stable diffusion 结果测试
* 论文定量实验表格更新
  * 空出user study
  * 采用高亮形式
* _上述做完，搞定v0的定量实验结果_

* 昨日backlog
  * 公众号文章整理

---


## 2024年1月19日


## TODO


* 写论文，搞定除消融实验之外的所有事项


* 昨日backlog
  * 公众号文章整理
* 18日 Arxiv整理
* User Study案例制作




## Doing






## Done
* shape inversion实验  
  * stable diffusion 训练
  * stable diffusion 测试
  * stable diffusion 结果测试
* 代码整理到github
* 论文定量实验表格更新
  * 空出user study
  * 采用高亮形式
* _上述做完，搞定v0的定量实验结果_


## Backlog

**2024年1月20日 记得看：！！！**
* Textual Inversion 在训练
  * 测试一下，观察是否过拟合
* Dreambooth 在训练
  * 通过减少训练steps，减轻过拟合问题   


---




## 2024年1月21日


## TODO

* Arxiv整理
* 新闻资讯阅览和记录


* 论文中图例修改
* 论文中所有图例的Caption
* Editing 能力画图



## Doing
* 消融实验
  * 去掉hypernetwork （搞定）
  * Filter冻结
  * embedding融合
  * 损失项 如果没有用 直接去掉吧



* Textual Inversion的训练


## Done

定量实验测试
  * Dreambooth
* 论文表格更新

* 定性实验，结果挑选，画图
* 论文相关文本内容撰写
* 定性实验文本内容更新


## Backlog

