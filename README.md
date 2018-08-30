﻿# ML


---

第一章 统计学习方法概论

1. 统计学习的研究对象：面向数据

2. 统计学习方法分类

 - 监督学习（supervised-leaning）：利用一组已知类别的样本调整分类器的参数，使其达到所要求性能的过程，也称为监督训练或有教师学习。
 - 无监督学习（unsupervised-leaning）：根据类别未知(没有被标记)的训练样本解决模式识别中的各种问题，称之为无监督学习。
 - 半监督学习（semi-supervised-leaning）：半监督学习使用大量的未标记数据，以及同时使用标记数据，来进行模式识别工作。当使用半监督学习时，将会要求尽量少的人员来从事工作，同时，又能够带来比较高的准确性。
 - 强化学习（reinfoucement-leaning）：智能系统从环境到行为映射的学习，以使奖励信号(强化信号)函数值最大，强化学习不同于连接主义学习中的监督学习，主要表现在教师信号上，强化学习中由环境提供的强化信号是对产生动作的好坏作一种评价(通常为标量信号)，而不是告诉强化学习系统RLS(reinforcement-learning-system)如何去产生正确的动作。由于外部环境提供的信息很少，RLS必须靠自身的经历进行学习。通过这种方式，RLS在行动-评价的环境中获得知识，改进行动方案以适应环境。

3. 统计学习方法的三要素

    模型（Model）+策略（Strategy）+算法（Algorithm)
 - 模型：找到一个能够解决问题的条件概率或者决策函数。
 - 策略：找到一个能够可以优化模型（或者衡量模型的）损失函数（比如0-1损失）。
 - 算法：找到一种可以优化损失函数的方法（比如：梯度下降法）。

4. 统计学习方法的步骤
    
    得到一个有限的训练数据集
    确定假设空间（即所有可能的模型）
    确定选择模型的准则（即策略）
    实现求解最优化模型的算法（即算法）
    选择最优模型
    利用最优模型对新来的数据进行预测和分析

5. 风险

 - 经验风险：对所有训练样本都求一次损失函数，再累加求平均。即模型f(x)对训练样本中所有样本的预测能力。所谓经验风险最小化（ERM）即对训练集中的所有样本点损失函数的平均最小化。经验风险越小说明模型f(x)对训练集的拟合程度越好。
 - 期望风险：对所有样本（包含未知样本和已知的训练样本）的预测能力，是全局概念。经验风险则是局部概念，仅仅表示决策函数对训练数据集里的样本的预测能力。对所有样本，包含未知样本和已知的训练样本，的预测能力，是全局概念。经验风险则是局部概念，仅仅表示决策函数对训练数据集里的样本的预测能力。
 - 结构风险：对经验风险和期望风险的折中，在经验风险函数后面加一个正则化项（惩罚项），是一个大于0的系数lamada。J(f)表示的是模型的复杂度。经验风险越小，模型决策函数越复杂，其包含的参数越多，当经验风险函数小到一定程度就出现了过拟合现象。也可以理解为模型决策函数的复杂程度是过拟合的必要条件，那么我们要想防止过拟合现象的方式，就要破坏这个必要条件，即降低决策函数的复杂度。也即，让惩罚项J(f)最小化，现在出现两个需要最小化的函数了。我们需要同时保证经验风险函数和模型决策函数的复杂度都达到最小化，一个简单的办法把两个式子融合成一个式子得到结构风险函数然后对这个结构风险函数进行最小化（SRM）。

6. 训练误差和测试误差和模型复杂度之间的关系
        ![此处输入图片的描述][1]

7. 交叉验证

    首先随机地将己给数据分为两部分，一部分作为训练集，另一部分作为测试集；然后用训练集在各种条件下(例如，不同的参数个数)训练模型，从而得到不同的模型；在测试集上评价各个模型的测试误差，选出测试误差最小的模型。
    
    方法如下:首先随机地将已给数据切分为S个互不相交的大小相同的子集；然后利用S-1个子集的数据训练模型，利用余下的子集测试模型；将这一过程对可能的S种选择重复进行；最后选出S次评测中平均侧试误差最小的模型。
    
8. 生成模型和判别模型

    监督学习方法又可以分为生成方法(generative-approach)和判别方法(discriminative approach).所学到的模型分别称为生成模型(geuemtive-model)和判别模型(discriminative-model)。生成方法由数据学习联合概率分布P(X,Y),然后求出条件概率分布P(YIX)作为预测的模型，即生成模型。
    这样的方法之所以称为生成方法，是因为模型表示了给定输入X产生输出Y的生成关系.典型的生成模型有:朴素贝叶斯法和隐马尔可夫模型。
    判别方法由数据直接学习决策函数f(X)或者条件概率分布P(Y|X)作为预测的模型，即判别模型.判别方法关心的是对给定的输入X，应该预测什么样的输出Y.典型的判别模型包括k近邻法、感知机、决策树、逻辑斯谛回归模型、最大嫡模型、支持向量机、提升方法和条件随机场等。
    
9. 模型评估标准

    精度（precision）、召回率（recall）、F1、准确率（accuracy）[（见这）][2]
    
    ROC曲线、EER。[（见这）][3]

10. 常用的损失函数总结：[这里][4]


  

    

 


  [1]: http://images0.cnblogs.com/blog/790160/201507/261025547016873.png
  [2]: http://blog.sina.com.cn/s/blog_900690c60101czyo.html
  [3]: https://zh.wikipedia.org/wiki/ROC%E6%9B%B2%E7%BA%BF
  [4]: https://www.cnblogs.com/luxiao/p/5783017.html
