---
{"dg-publish":true,"dg-permalink":"tech/machine-learning/ji-chu-zhuan-ti.md","permalink":"/tech/machine-learning/ji-chu-zhuan-ti.md/"}
---


# 基础专题

## 经验误差

前提：$$m$$个样本中$$\alpha$$个样本分类错误

* 错误率：$$E=\alpha / m$$
* 精度：$$1-E = (1-\alpha/m)\times 100\%$$
* 误差（error）：实际输出与真实输出的差异
  * 训练集上的误差：训练误差（training error）或经验误差（empirical error）
  * 新样本上的误差：泛化误差（generalization error）
* 过拟合（over fitting）：训练样本自身特点当成泛化规律，模型变得教条
* 欠拟合（under fitting）：未能掌握足够的泛化规律

## 评估方法

### 留出法（hold-out）

1. 主要思路：将数据集分成两个部分，一个较大的训练集（用于训练模型）和一个较小的测试集（用于评估模型性能）。
2. 划分比例：训练集（2/3～4/5），测试集（1/3～1/5）
3. 各种样本按照类别采用分层采样，比如正例和反例需要分别分成两部分然后再组成训练集和测试集
4. 单次使用留出法会使结果不稳定（被分到测试集的数据永远不会提供经验），一般会多次使用留出法，每次都进行随机划分。

### k 折交叉验证（ k-fold cross validation）

1. 主要思路：将整个数据集随机分成k个大小大致相等的子集。每个子集都将成为一次测试集。
2. k 通常取 10，也可以取 5 或 20
3. p 次 k 折交叉验证：k 折交叉验证做 p 次求平均。比如 10 次 10 折交叉验证，做了 100 次训练。
4. 留一法（Leave-One-Out，LOO）：一种特殊的交叉验证方法，其中k的值等于数据集中的样本数量。

### 自助法（bootstrapping）

1.