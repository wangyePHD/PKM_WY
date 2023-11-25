---
id: y94rhjlymjyn91hrfz1lfxe
title: '2023-11-19'
desc: ''
updated: 1700377171189
created: 1700361301062
traitIds:
  - journalNote
---
<!--
Based on the journaling method created by Intelligent Change:
- [Intelligent Change: Our Story](https://www.intelligentchange.com/pages/our-story)
- [The Five Minute Journal](https://www.intelligentchange.com/products/the-five-minute-journal)
-->



## **待做事项**

### <font color=red>**重要紧急**</font>
- [x]  每日Arxiv
- [x]  每日论文阅读
- [ ]  实验安排
  - [ ]  ![图 0](assets/images/ba1f26f8ed4f2cb3b157c3ae2ea076051f1d8cb9f5af3b39bd205c9bfa68be14.png)  
  - [ ] Xformer 真的会影响性能？
    - [ ] 自身的原因
    - [ ] 还是batch太大的原因呢
      - [ ] baseline代码一样，换成batch=2也不行

### <font color=#871F78>**不重要紧急**</font>




### <font color=blue>**重要不紧急**</font>


### <font color=green>**不重要不紧急**</font>




## **工作笔记**

* XFormers 性能的影响？
  * 是否是batch size造成的
    * 不是batch_size造成的影响，同样的代码，同样的batchsize=2设置，其余参数都一样，使用了XFormers就是无法得到好的结果。
  * Student-model保持一样的参数能跑出来吗？
    * 同样跑不出来，得到的结果都很糊。
  * 两次实验验证之后，还是不要用XFormers了，总是会引入一些不可预料的问题。

![图 5](assets/images/6f5f265ff48981cd199da5160ee44b8435903c651a98c8b724f5059d8f932481.png)  

![图 6](assets/images/1024206f9f45fa4ea060c24088b4bc196156ee4365487d82345ddc3221c4ea83.png)  

![图 7](assets/images/518786ba7617a6272be347b4b1a6512583b25fa396caa4f8ac3dbc44ec02f074.png)  



## **问题记录**

1.
2.
3.


## **今日总结**

1.
2.
3.
