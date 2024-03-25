---
id: 0nzjvpm4h19klgpppu8bjin
title: 01 你已连接到不受Visual Studio Code支持的OS版本
desc: ''
updated: 1710770418459
created: 1710764372328
---



今天遇到一个bug，整整折磨了我两个多小时。

## 问题描述

我远程登录昆仑万维的长沙计算节点，发现提示我当前如下警告：

```
you are connected to an OS version that is unsupported by VisuaStudio Code

```
这个问题，我查了一下，发现是1.86之后的vscode版本，将不再适配老的OS版本。也就是说长沙节点的服务器有点旧了。

## 解决方法

* 首先，vscode我直接降版本到1.85。
  * [下载链接](https://code.visualstudio.com/updates/v1_85)
* 然后设置vscode不允许自动更新
  * 打开设置，直接搜索自动更新，将其关闭即可。

好蠢，我一直以为是网络的问题。这些解决了，目前vscode+fitten code 写代码爽到飞起。

