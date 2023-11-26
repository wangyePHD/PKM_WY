---
id: ewo7ziymnvi0dm9svc89lnp
title: 刘明华_understanding_and Generating_3D_shapes_in_an_open_world
desc: ''
updated: 1699187400167
created: 1699185966627
---

![图 0](assets/images/8bed61ceebd026ab914cd5db4888aa2d5692c7feeb50c929086e155ecb075dbe.png)  

哈哈哈 "chair research"。

---

![图 1](assets/images/2aab21df59e319d8fbb4a99909d87552e00022ccef2a400f8104ae42cd5f660d.png)  

上图的分类有些东西：
1、要重点关注Multi-View Prediction-Based Methods

---

![图 3](assets/images/c899f726c9b9aad635e16094bee9b5ecb48ac19de5a870573126f72660f42175.png)  

![图 4](assets/images/21faca4e2a78d5e6f07a8342b63849add65913c349edd0be9907298e2c9bf4dd.png)  

---

![图 5](assets/images/6287b323419b47883536d3d422116aaf939ca9f54f303b082f326d58be56cb33.png)  

![图 6](assets/images/4654c2bd83493508fe9ed2f9191cb7ca4c8480b0752a9017028ea548f41803cd.png)  

直接将0123模型的输出结果，也就是多视角图像，拿来训练NeRF，得到3D Mesh，发现效果并不好。一部分原因是：0123得到的多视角图像并不一致。

![图 7](assets/images/e9c636e590fbf98255a0d572a46b4f2d997352e81450ad0049a5ae889ff8726c.png)  

基于coarse-volume的方法都3D的不一致，有更好的应对。

---

![图 8](assets/images/c974c72c16d8b42168c2d699a2b4e87236d8707f20ba4b17da1f8eb6a7f40fcc.png)  

