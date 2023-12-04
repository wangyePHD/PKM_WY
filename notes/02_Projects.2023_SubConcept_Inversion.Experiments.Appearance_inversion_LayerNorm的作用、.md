---
id: 9yle6i9ekd27ae57h7hhcbr
title: Appearance_inversion_LayerNorm的作用
desc: ''
updated: 1701712792510
created: 1701696170850
---


## LayerNorm的作用？

实验设置：
* dotdog 
* 添加LayerNorm
  * 1
* 不添加LayerNorm
  * z_work-exp-appearance-leopard-diffmse-no-LN_2023-12-04-21.52
* leopard 
  * 添加LayerNorm
  * 不添加LayerNorm
    * z_work-exp-appearance-dog-diffmse-no-LN_2023-12-04-21.56
* 测试文本：
  * dotdog
    * a cat in the appearance of *a
    * a horse in the apperance of *a
  * leopard
    * a cat in the appearance of *a
    * a dog in the appearance of *a




## dotdog实验

![图 0](assets/images/f38ef713a0b1f374004037cdfdb2ce38524382f722f96356da7ff630f79a13b7.png)  
![图 1](assets/images/87da81fe8ff32867987550b9599748ed03685957fc1c1bb8967d6728d79467e5.png)  


## leopard实验