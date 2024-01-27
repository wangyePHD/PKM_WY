---
id: hd9c4n3nrzledawchezajwr
title: 2024胰腺癌本子
desc: ''
updated: 1706244243896
created: 1706244243896
---


第 4 段: 使用图神经网络挖掘癌症标志物的现状: 包含五个方面: 基因层面、转录组学层面、蛋白组学层面、代谢组学层面、多组学层面: 即基因-疾病预测非编码 RNA-疾病预测、PPI 互作预测疾病、代谢-疾病预测、多数据融合-疾病预测。(可以着重找一下，有没有通过网络的方法预测胰腺癌标志物的) (平姐)



## 论文收集

* A deep learning algorithm to predict risk of pancreatic cancer from disease trajectories，nature medicine，20230331
    * 转录组学和蛋白组学
      * Pathway analysis of genome-wide association study data highlights pancreatic development genes as susceptibility factors for pancreatic cancer，Carcinogenesis 33, 1384–1390 (2012)."
    * 基因和遗传风险因素
      * Genome-wide meta-analysis identifies five new susceptibility loci for pancreatic cancer. Nat. Commun. 9, 556 (2018)
    * 代谢组学：
      * "Genetic and circulating biomarker data improve risk prediction for pancreatic cancer in the general population. Cancer Epidemiol. Biomark. Prev. 29, 999–1008 (2020)."
    * 电子健康记录（EHR）分析：
      * Can we screen for pancreatic cancer? Identifying a sub-population of patients at high risk of subsequent diagnosis using machine learning techniques applied to primary care data. PLoS ONE 16, e0251876 (2021)."



---



* 基因层面
  * 基因-疾病预测
* 转录组学层面
  * 非编码 RNA-疾病预测
    * [JEM（IF 17.579）| 密歇根大学利用单细胞转录组揭示改变胰腺癌免疫微环境可以增强治疗效果](https://www.aptbiotech.com/market/6103)
* 蛋白组学层面
  * PPI 互作预测疾病
    * https://finance.sina.cn/2022-07-02/detail-imizmscu9770196.d.html
      * 这篇文章介绍了胰腺癌的严重性和治疗挑战，以及南方科技大学化学系终身教授田瑞军团队通过蛋白质组学研究发现了介导胰腺癌细胞与星状细胞之间信号转导的关键因子白血病抑制因子（LIF），并开发了高效的样品前处理技术Intact GlycoSISPROT。团队的研究成果为胰腺癌的精准诊断和治疗提供了新思路和希望。
* 代谢组学层面
  * 代谢-疾病预测
    * Metabolic classification suggests the GLUT1/ ALDOB/G6PD axis as a therapeutic target in chemotherapy-resistant pancreatic cancer, Cell Reports Medicine, 20230822
      * 研究团队通过分析胰腺导管腺癌（PDAC）的代谢特征，发现了两种不同的代谢亚型：高葡萄糖代谢（glucomet-PDAC）和高脂质代谢（lipomet-PDAC）。他们发现，与lipomet-PDAC相比，glucomet-PDAC对化疗的抵抗力更强，且患者的预后更差。
    * Metabolic detection and systems analyses of pancreatic ductal adenocarcinoma through machine learning， lipidomics， and multi-omics, Science Advances, 20211222
      * 北京大学尹玉新教授团队在《Science Advances》上发表的一项研究，该研究开发了一种结合人工智能（AI）和代谢组学的新方法，用于诊断胰腺导管腺癌（PDAC），这是胰腺癌中最常见的类型。尹玉新团队利用机器学习结合脂质组学和多组学技术，分析了PDAC的代谢特征，并开发了一种AI辅助的无创检测方法。他们基于支持向量机-贪心算法和高分辨质谱技术，从非靶向代谢组学数据中筛选出17个血清代谢标志物，并建立了液相色谱-质谱的多反应检测模式，以及AI疾病分类模型。
* 多组学层面
  * 多数据融合-疾病预测。
    * A deep learning algorithm to predict risk of pancreatic cancer from disease trajectories，nature medicine，20230331
      * 这篇文章主要关注的是利用机器学习模型从临床数据中预测胰腺癌的风险，这属于“多数据融合-疾病预测”类别。在这项研究中，研究者们并没有直接使用基因、转录组、蛋白组或代谢组学数据，而是使用了患者的临床记录，这些记录包含了患者的疾病诊断轨迹。通过分析这些轨迹，模型能够学习到疾病的模式，并预测患者未来患胰腺癌的可能性。
    * Multi-cancer risk stratification based on national health data: a retrospective modelling and validation study. Preprint at bioRxiv https://doi.org/10.1101/2022.10.12.22280908 (2022).
      * 这篇论文主要利用了丹麦国家健康数据库中的电子健康记录数据来预测癌症风险，这些数据包括了患者的医疗历史、家族癌症史和一些基本健康因素。这些信息可以被视为多组学数据的一部分，因为它们涵盖了个体在不同时间点的健康状况和医疗事件。
    * Genetic and Circulating Biomarker Data Improve Risk Prediction for Pancreatic Cancer in the General Population
      * 这篇论文的标题是《基因和循环生物标志物数据改善了一般人群胰腺癌风险预测》。研究团队通过分析来自美国四个大型前瞻性队列研究的500例胰腺癌病例和1091名匹配对照，开发了一个综合风险预测模型。这个模型结合了临床因素（如体重指数、腰臀比、体育活动量和糖尿病史）、遗传多态性（即基因变异）以及循环生物标志物（如胰岛素前体、脂肪因子、白细胞介素6和支链氨基酸）。






* 基因层面
  * 基因-疾病预测
    * **A novel biomarker selection method combining graph neural network and gene relationships applied to microarray data，BMC Bioinformatics，2022**
      * 这篇论文提出了一种新的方法，用于从微阵列数据中选择生物标志物。论文的主要贡献是提出了一种基于图神经网络（Graph Neural Network, GNN）的特征选择方法。这种方法利用了基因之间的实际依赖关系，通过构建图结构数据，然后应用图神经网络的信息传播和聚合操作来融合节点信息。接着，使用谱聚类方法对冗余特征进行聚类，最后通过多种特征评估方法对每个聚类子集进行特征选择。
* 转录组学层面
  * 非编码 RNA-疾病预测
* 蛋白组学层面
  * **Intratumor graph neural network recovers hidden prognostic value of multi-biomarker spatial heterogeneity，2022，NC**
    * 研究者们首先通过多光子显微镜（Multiphoton Microscopy, MPM）获取了乳腺癌患者的组织样本，并识别了肿瘤相关胶原签名（Tumor-Associated Collagen Signatures, TACS）。然后，他们将这些生物标志物的空间分布信息编码为图结构，其中每个节点代表一个区域（Region of Interest, ROI），节点之间的边代表区域间的相互作用。接着，他们训练了一个图神经网络模型，该模型能够学习这些节点（即生物标志物）之间的区域性相互作用，并预测患者的预后。
* 代谢组学层面
  * 代谢-疾病预测
    
* 多组学层面
  * 多数据融合-疾病预测。
    * [Spatially aware graph neural networks and cross-level molecular profile prediction in colon cancer histopathology: a retrospective multi-cohort study](https://www.shlab.org.cn/news/5443307)，柳叶刀杂志
      * 提出了一种基于病理图像的空间图神经网络（GNN）方法，用于预测癌症的多分子结果。研究的核心是开发了一种新的图网络模型，该模型能够通过分析肿瘤病理切片的区域相互关联来探索肿瘤微环境的空间信息。研究通过**整合病理图像（组织学层面）、基因突变、基因拷贝数变异和蛋白质表达等多源数据**，进行多组学分析，以预测癌症的临床结果。
