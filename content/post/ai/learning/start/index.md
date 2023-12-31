---
title: "人工智能 - 神经网络"
description: 
date: 2024-01-04T13:41:04+08:00
image: 
math: 
license: 
hidden: false
comments: true
draft: false
categories:
  - AI
  - DeepLearning
tags:
  - AI
  - DeepLearning
keywords:
  - AI
  - DeepLearning
---
### 人工智能

> 学习参考资料: [1.1.1 什么是神经网络 (captainbed.cn)](https://www.captainbed.cn/whatisnn/)

####  神经网络

##### 什么是神经网络

人工智能的神经网络受到人体大脑的启发，构建出来。

在人的大脑中，有着数十亿叫神经元的细胞，它们连接成为一个网络。

而在人工智能中，模仿人的大脑，也创建出N个神经元，它们连接成为神经网络。

而每个神经元负责接受外部刺激，处理信息，转化成结果。

![神经网络](https://pendjun.obs.cn-south-4.myhuaweicloud.com/img/timg-2.jpg)

![人工神经网络](https://pendjun.obs.cn-south-4.myhuaweicloud.com/img/TIME59BBEE7898720180827112521.png)

![神经元处理刺激](https://pendjun.obs.cn-south-4.myhuaweicloud.com/img/20181014193738897.png)



##### 数据传入神经网络

对于不同特征的数据（例如语音、图像、传感器或其他等等）在计算机中都会有对应的数字表示形式。通常它们会被转化成一个特征向量，传入到神经网络中。

举例：假设一个图像有64*64个像素，每个像素就是一个颜色点，每个颜色点在(红(0-255),蓝(0-255),绿(0-255))`三原色可以调配出所有色彩`之间,

所以在计算机中,3\*64\*64个颜色点构成这张图像 = 12288 总特征数,这个12288维特征向量就代表了这张图像.神经网络接收这个特征向量,预测并得出结果.



##### 神经网络如何进行预测

###### 逻辑回归公式

预测的过程其实只是基于一个简单的公式(`逻辑回归公式`)：`z = dot(w,x) + b `

`x`表示`输入特征向量`,如果有三个特征就可以用(x1,x2,x3)表示

`w`表示`权重`,代表每个特征的重要程度

`b`表示`阈值`,用于影响预测结果

`dot`表示`将w和x进行向量相乘`

`z`表示`预测结果`

于是上面的公式展开后就成 `z = (w1*x1 + w2*x2 + w3*x3) + b`

![逻辑回归公式](https://pendjun.obs.cn-south-4.myhuaweicloud.com/img/20181014210626518.png)

举例:

假设你现在想喝奶茶,但现在天气不好,配送时间太长,而你又可能马上要下班了.

那么影响结果的因素有3个特征,而你对每个因素的看重程度代表着权重,

- 天气好不好对你不重要.	`w1=0,x1=1`(w1=0表示无所谓,x1=1表示确实不好);

- 配送时间太长有影响.            `w2=3,x2=1` (w2=3表示有一定程度影响但不大,x2=1表示确实有影响)

- 马上要下班了,想马上回家.   `w3=6,x3=1`(w3=1表示想回家的优先级很高,x3=0表示想回家)

- 想回家的期望值很高.            `b=-10`

那么我们得出公式: `z = (0*1 + 3*1 + 6*1) - 10` ,结果是-1.

根据结果表示`z<0`则不会喝,`z>0`会喝,所以我们预测你不会现在想喝奶茶.



###### 激活函数

在实际的神经网络中,上面的`逻辑回归`只能适用于非常简单的逻辑.在复杂场景中计算得出的z值就不太准确,所以我们需要在`逻辑回归`外面再套一层函数.

这个函数就叫做`激活函数`.下面简单介绍一种激活函数:`sigmoid`

![激活函数公式](https://pendjun.obs.cn-south-4.myhuaweicloud.com/img/201810142126508048-3.png)

![激活函数图像](https://pendjun.obs.cn-south-4.myhuaweicloud.com/img/timg-34.jpg)

这个函数的作用是: 将z映射到[0,1]之间.x表示z值,y表示预测结果.可以看出,z越大,y越趋向于1,z越小,y越趋向于0.

在刚才的例子中,假设z的结果是1,而y'值=0.8,则表示有80%的概率会买.但z值是-1,所以不会买.



