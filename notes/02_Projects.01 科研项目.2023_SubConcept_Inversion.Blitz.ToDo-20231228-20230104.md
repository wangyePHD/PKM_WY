---
id: zdig668f4h0g9lilw76ikzb
title: ToDo-20231228-20230104
desc: ''
updated: 1704093376645
created: 1703773107353
---


## 20231228晚 TODO

* 训练leaf，陶瓷三张图像，然后测试
  * hat
  * 其他一些事物等
* 测试appearance 例子中，对测试例子加一些修饰词，背景，场景等
  * 比如running dog--a running dog in the appearance of *a
  * a horse in the appearance of *a, which is grazing in the farm
  * 没问题，能够带来一定的效果，但是越到后面过拟合就比较严重了。
* 收集更多的测试例子，接着训练
  * 收集到了20张图像



* 思考更多炫酷的应用场景
* shape 评测指标，评测思路，给出一版本

---

## 20231229

### TODO

* 训练更多的appearance数据
* 对训练好的模型，测试，生成各种跨冲类的物体等
* 论文中得插图，绘制
* 学习Classifier Guidance和Classifier-free Guidance
  * https://sander.ai/2022/05/26/guidance.html
* 测试今天训练好的模型




### Doing

* 测试bark 预训练模型
  * a desk 
  * a building


* 训练fabric2，rainbow纹理两组数据
  * 注意 没有分割
* 推进论文TODO标记



### Done
* 改版训练代码
* 改版训练代码，accelerate config load
* 训练wall和树皮两组数据
  * 注意 没有分割
* 训练fabric fabric1两组数据
  * 注意 没有分割 
* 训练fabric3，marble纹理两组数据
  * 注意 没有分割
* Pipeline图已经修改完毕

---



## 20231230

## TODO
* 收集，训练更多的appearance图像
* 测试训练好的模型
* 训练脚本 dataset添加mask pkl，测试要求no_pkg



## Doing

* 重新训练，删除之前训练的模型



## Done
* 测试陶瓷, 项链 necklace 可以 


## Note

* 避免使用背景纹理图作为appearance 参考图像




## 20240101

## TODO
* 定量测试方案
* 定性结果整理



## Doing
* 训练新收集的appearance数据



## Done
* Appearance图像归类
* Appearance图像收集