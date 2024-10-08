# 神经网络简介：感知机

## [课前测验](https://red-field-0a6ddfd03.1.azurestaticapps.net/quiz/103)

1957年，康奈尔航空实验室的弗兰克·罗森布拉特（Frank Rosenblatt）进行了类似于现代神经网络的首次尝试之一.这是一种名为“Mark-1”的硬件实现，旨在识别原始几何图形，如三角形、正方形和圆形.

|      |      |
|--------------|-----------|
|<img src='images/Rosenblatt-wikipedia.jpg' alt='Frank Rosenblatt'/> | <img src='images/Mark_I_perceptron_wikipedia.jpg' alt='The Mark 1 Perceptron' />|

> 图片来自 [维基百科](https://en.wikipedia.org/wiki/Perceptron)

输入图像由20x20的光电池阵列表示，因此神经网络有400个输入和一个二进制输出.一个简单的网络包含一个神经元，也称为**阈值逻辑单元**.神经网络的权重就像电位器，需要在训练阶段手动调整.

> ✅ 电位器是一种允许用户调整电路电阻的设备.

> 当时《纽约时报》关于感知机的报道写道：*这是电子计算机的雏形，海军预计它将能够行走、说话、看见、书写、自我复制并意识到自身的存在.*

## 感知机模型

假设我们的模型中有N个特征，那么输入向量将是一个大小为N的向量.感知机是一种**二分类**模型，即它可以区分两类输入数据.我们将假设对于每个输入向量x，感知机的输出将是+1或-1，取决于类别.输出将使用以下公式计算：

y(x) = f(w<sup>T</sup>x)

其中f是阶跃激活函数

<!-- img src="http://www.sciweavers.org/tex2img.php?eq=f%28x%29%20%3D%20%5Cbegin%7Bcases%7D%0A%20%20%20%20%20%20%20%20%20%2B1%20%26%20x%20%5Cgeq%200%20%5C%5C%0A%20%20%20%20%20%20%20%20%20-1%20%26%20x%20%3C%200%0A%20%20%20%20%20%20%20%5Cend%7Bcases%7D%20%5C%5C%0A&bc=White&fc=Black&im=jpg&fs=12&ff=arev&edit=0" align="center" border="0" alt="f(x) = \begin{cases} +1 & x \geq 0 \\ -1 & x < 0 \end{cases} \\" width="154" height="50" / -->
<img src="images/activation-func.png"/>

## 训练感知机

为了训练感知机，我们需要找到一个权重向量w，使得大多数值分类正确，即产生最小的**误差**.这个误差E通过**感知机准则**以以下方式定义：

E(w) = -&sum;w<sup>T</sup>x<sub>i</sub>t<sub>i</sub>

其中：

* 求和仅在导致分类错误的训练数据点i上进行
* x<sub>i</sub>是输入数据，t<sub>i</sub>根据负样本和正样本分别为-1或+1

这个准则被视为权重w的函数，我们需要最小化它.通常，使用一种称为**梯度下降**的方法，我们从一些初始权重w<sup>(0)</sup>开始，然后在每一步根据以下公式更新权重：

w<sup>(t+1)</sup> = w<sup>(t)</sup> - &eta;&nabla;E(w)

这里&eta;是所谓的**学习率**，&nabla;E(w)表示E的**梯度**.计算梯度后，我们得到

w<sup>(t+1)</sup> = w<sup>(t)</sup> + &sum;&eta;x<sub>i</sub>t<sub>i</sub>

Python中的算法如下：

```python
def train(positive_examples, negative_examples, num_iterations = 100, eta = 1):

    weights = [0,0,0] # 初始化权重（几乎是随机的 :)
        
    for i in range(num_iterations):
        pos = random.choice(positive_examples)
        neg = random.choice(negative_examples)

        z = np.dot(pos, weights) # 计算感知机输出
        if z < 0: # 正样本被分类为负
            weights = weights + eta*weights.shape

        z  = np.dot(neg, weights)
        if z >= 0: # 负样本被分类为正
            weights = weights - eta*weights.shape

    return weights
```

## 结论

在本课中，您了解了感知机，这是一种二分类模型，以及如何通过使用权重向量来训练它.

## 🚀 挑战

如果您想尝试构建自己的感知机，尝试[微软学习中的这个实验](https://docs.microsoft.com/en-us/azure/machine-learning/component-reference/two-class-averaged-perceptron?WT.mc_id=academic-77998-cacaste)，它使用[Azure ML设计器](https://docs.microsoft.com/en-us/azure/machine-learning/concept-designer?WT.mc_id=academic-77998-cacaste).

## [课后测验](https://red-field-0a6ddfd03.1.azurestaticapps.net/quiz/203)

## 复习与自学

要了解我们如何使用感知机解决一个玩具问题以及实际问题，并继续学习，请参阅[感知机](Perceptron.ipynb)笔记本.

这里有一篇有趣的[关于感知机的文章](https://towardsdatascience.com/what-is-a-perceptron-basics-of-neural-networks-c4cfea20c590)供您参考.

## [作业](lab/README.md)

在本课中，我们已经实现了用于二分类任务的感知机，并使用它在两个手写数字之间进行分类.在这个实验中，您需要完全解决数字分类问题，即确定哪个数字最有可能对应于给定的图像.

* [说明](lab/README.md)
* [笔记本](lab/PerceptronMultiClass.ipynb)