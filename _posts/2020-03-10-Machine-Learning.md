---
layout:     post
title:      Machine Learning
subtitle:   Coursera
date:       2020-03-10
author:     PZ
header-img: img/post-bg-github-cup.jpg
catalog: true
tags:
    - Machine Learning
    - Python
---

## 准确率 accuracy

当您使用分类不平衡的数据集（比如正类别标签和负类别标签的数量之间存在明显差异）时，单单准确率一项并不能反映全面情况
所以需要精确率和召回率

![img](https://raw.githubusercontent.com/pzheng16/pzheng16.github.io/master/img/ml/2.png)


## precision and recall

**Precision**:在被识别为正类别的样本中，确实为正类别的比例是多少？

![img](https://raw.githubusercontent.com/pzheng16/pzheng16.github.io/master/img/ml/3.png)

![img](https://raw.githubusercontent.com/pzheng16/pzheng16.github.io/master/img/ml/4.png)

## ROC AUC

![img](https://raw.githubusercontent.com/pzheng16/pzheng16.github.io/master/img/ml/5.png)

曲线下面积表示随机正类别（绿色）样本位于随机负类别（红色）样本右侧的概率。

曲线下面积因以下两个原因而比较实用：

- 曲线下面积的尺度不变。它测量预测的排名情况，而不是测量其绝对值。
- 曲线下面积的分类阈值不变。它测量模型预测的质量，而不考虑所选的分类阈值

## L1, L2 正则化

L1 正则化可以让一些不必要的权重变为0，减少RAM消耗，和计算量，如果用L2话不能使得权重变为0，那么计算量依然是很大的。

“非线性”意味着您无法使用形式为
b+w1x1+w2x2
的模型准确预测标签。也就是说，“决策面”不是直线。之前，我们了解了对非线性问题进行建模的一种可行方法

## **Learning Curves**

Training an algorithm on a very few number of data points (such as 1, 2 or 3) will easily have 0 errors because we can always find a quadratic curve that touches exactly those number of points. Hence:

- As the training set gets larger, the error for a quadratic function increases.
- The error value will plateau out after a certain m, or training set size.

![img](https://raw.githubusercontent.com/pzheng16/pzheng16.github.io/master/img/ml/1.png)

### Experiencing high bias:

If a learning algorithm is suffering from high bias, getting more training data will not (by itself) help much.

![img](https://raw.githubusercontent.com/pzheng16/pzheng16.github.io/master/img/ml/6.png)

### Experiencing high variance:

If a learning algorithm is suffering from high variance, getting more training data is likely to help.

![img](https://raw.githubusercontent.com/pzheng16/pzheng16.github.io/master/img/ml/7.png)


## Deal with High bias or high variance

- **Getting more training examples:** Fixes high variance
- **Trying smaller sets of features:** Fixes high variance
- **Adding features:** Fixes high bias
- **Adding polynomial features:** Fixes high bias
- **Decreasing λ:** Fixes high bias
- **Increasing λ:** Fixes high variance.

## ML-Clustering-Unsupervised Learning: Introduction

Using these variables we can define our cost function:

![img](https://raw.githubusercontent.com/pzheng16/pzheng16.github.io/master/img/ml/8.png)

With k-means, i**t is not possible for the cost function to sometimes increase**. It should always descend.
K-means can get stuck in local optima. To decrease the chance of this happening,** you can run the algorithm on many different random initializations**. In cases where K<10 it is strongly recommended to run a loop of random initializations.


**Choosing the Number of Clusters:**

The elbow method: plot the cost J and the number of clusters K. The cost function should reduce as we increase the number of clusters, and then flatten out. Choose K at the point where the cost function starts to flatten out.

Note: J will always decrease as K is increased. The one exception is if k-means gets stuck at a bad local optimum.


## Learning with Large Datasets

### Stochastic Gradient Descent

This algorithm will only try **to fit one training example** at a time. 
Mini-Batch Gradient Descent


### Mini-Batch Gradient Descent

Instead of using all m examples as in batch gradient descent, and instead of using only 1 example as in stochastic gradient descent, we will use some in-between number of examples b.

### Map Reduce and Data Parallelism

![img](https://raw.githubusercontent.com/pzheng16/pzheng16.github.io/master/img/ml/9.png)



