---
id: ckys32gxn157b3td5mryp5a
title: git总结
desc: ''
updated: 1702969122326
created: 1702968527380
---

## **Git使用之版本回退**

版本代码回退是一个非常重要的功能，尤其是当做实验的时候，总是会出现莫名其妙突然代码就有问题，之前的效果就跑不出来了。这个时候就需要代码回退，回退到之前work的代码。

**前提：**

* 需要养成push代码的习惯，同时每次push都要写好tag和相关的commit信息。方便以后使用。推荐使用Vscode+Git Graph插件。如下图所示，我的提交记录：

![图 0](assets/images/2c8d3d0e380f8be98c79423765b46ef69fd9b877f9a046435ebd11b0c7514de2.png)  


**使用：**
* 根据时间，你可以找到你希望回退的代码版本，然后点击，如下图所示：

![图 1](assets/images/d83fe2eda7209146ee4788b03974b08abc72e8b783fdcb05839130bfa9b4b5a8.png)  


每次commit，git都会默认赋给一个hash id。基于这个id，我们可以唯一指定的回退代码。

* 右键当前的版本

![图 2](assets/images/96684b9be65d9b49136de7bb110d074da34af8bf3be2f9bb3bd092dd38b42152.png)  
点击红色框内，进行回滚。

* 请注意，上述操作只是将目标版本的代码作为了这次commit的内容，你还需要提交到git，这样github上的代码，就是你希望回滚的代码版本了。执行如下命令：
```bash
git push --force origin main（注意main是分支名字）
```
