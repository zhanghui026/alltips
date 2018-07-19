#  递归神经网络RNN,DNN深度神经网络介绍

##1.1 内容

 主要介绍下神经网络和神经网络算法RNN，了解下其中原理

1. 神经网络，一个神经网络的例子
2. RNN、实现RNN使用Python和Theano
3. BPTT时间上反传的梯度下降（Backpropagation Through Time）和 Vanishing Gradients（消失问题）
4. 实现GNU和LSTM RNN
5. DNN介绍
6. RNN主要应用场景

## 1.2  神经网络

### 1.2.1 神经网络介绍

* 神经网络也是做分类，概念来源于人类大脑。人类大脑的核心神经元，人的神经元是细胞体和神经纤维组成，

  大脑中上百万感觉神经元和上百万的运动神经元，并且上百上千亿个中间神经元。神经网络算法在很多方面借鉴了人的神经元。人的感知是神经系统主要靠生物电、计算机电流，人类对大脑研究还远远不足。

  ![人类神经元](http://p3.pstatp.com/large/37dc00042a6e8cf9a80c)

* 神经网络结构图：

  ![结构图](/Users/zhanghui/Desktop/结构图.jpg)

* 直观认识，神经网络的主要用途也是分类

  * 垃圾邮件识别
  * 疾病判断
  * 猫狗分类

![逻辑回归分类器](http://www.wildml.com/wp-content/uploads/2015/09/nn-from-scratch-lr-decision-boundary.png)

* 使用神经网络实现后

  ![3层神经网络](http://www.wildml.com/wp-content/uploads/2015/09/nn-from-scratch-h3.png)

  

  

  

  

  ### 1.2.2 神经网络例子

  

  从头开始实现个3层神经网络，做一个上述图的分类神经图

  #### 1.2.2.1 数据集

  我们生成的数据集有两个类，绘制为红色和蓝色点。您可以将蓝点看作男性患者，将红点看作女性患者，x轴和y轴是医学测量值。

  ![数据集](http://www.wildml.com/wp-content/uploads/2015/09/nn-from-scratch-dataset.png)

数据不是线性可分的，线性逻辑回归后的结果，神经网络对特征数据不需要提前处理，隐藏层就处理了，

这是个优势。

![逻辑回归分类器](http://www.wildml.com/wp-content/uploads/2015/09/nn-from-scratch-lr-decision-boundary.png)

### 1.2.3 RNN神经网络

