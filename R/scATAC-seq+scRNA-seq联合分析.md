# scATAC-seq+scRNA-seq联合分析

### 1. scRNA-seq预处理

- Python - ./scRNA/0.1-py_preprocessing.ipynb
  - 读取h5ad文件`adata-fixFemale.h5ad`
  - 切分每个样本的注释文件
  - 读取细胞类型`majorType-fix`，并保存csv（./data/batch.csv）
- R - ./scRNA/02-preprocessing.ipynb
  - 读取scRNA-seq数据
  - 删除不重合细胞、添加细胞类型
  - 预处理
    - 归一化
    - 高变基因
    - 缩放、PCA、TSNE、UMAP
  - 保存（./data/batch.rds）

### 2. scATAC-seq预处理

- ./scATAC/01-preprocessing.ipynb

  - 读取scATAC-seq数据，创建 seuart 对象

  - 注释基因

  - qc（绘图、保存）

  - 归一化、降维

  - 聚类、UMAP

  - 基因活性矩阵

  - 保存（./data/batch.rds）


### 3. 标签转移

- ./scATAC/02-anntation.ipynb

  - 读取scRNA-seq、scATAC-seq

  - FindTransferAnchors

  - TransferData

  - 将预测标签添加到atac对象中

  - 保存（./data/cellType）




---

1. `FindTransferAnchors()`报错找不到variable Features？

`FindTransferAnchors()`使用的是单细胞转录组数据中的高变基因来寻找锚点。因为高变基因在不同数据集之间的表达模式较为保守，可用作数据集之间的共享特征。

