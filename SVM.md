# suport vector machine
## 1 introduction
给定一个样本集，在样本空间中找到一个划分超平面，能够将两种类型的样本分开，且分割效果最好。所谓分割效果最好，就是距离两个类别最近点都最远，并且两种类别最近点的距离相等。

![avatar](/figure/introduction_of_%20svm.png)

## 2 支持向量
### 2.1 线性可分
所谓线性可分，就是对于两个不同类别的点集$D_0$和$D_1$，可以通过一条超平面（对于二维度空间就是常见的平面直线）$\vec{\omega}^T \cdot \vec{x}+b$分割开来，即对于$D_0$上的点$x_i$，$\vec{\omega}^T \cdot \vec{x}+b>0$，而对于$D_1$上的点$x_j$，$\vec{\omega}^T \cdot \vec{x}+b<0$。
### 2.2 最大间隔超平面
为了使这条直线对于样本的分割效果最好，受到偶然干扰导致分割错误的概率最小（鲁棒性），我们希望能够找到一个最佳的超平面，满足：
- 两类样本都在平面两侧；
- 两侧样本最近点到超平面的距离最大化。
### 2.3 支持向量
在2.2节中，离这个超平面最近的点称为支持向量。
### 2.4 SVM最优化问题
$n$维空间中向量到超平面之间的距离：
$$
D=\frac{\mid \vec{\omega}^Tx+b \mid}{\mid\mid \vec{\omega} \mid\mid}
$$
对于支持向量，距离$d=\frac{1}{\mid\mid \vec{\omega} \mid\mid}$.

## 3 对偶问题
### 3.1 拉格朗日乘数法
我们要求的是使得$d$最大，即$\frac{1}{\mid\mid \vec{\omega} \mid\mid}$最大，等价于使$\mid\mid \vec{\omega} \mid\mid$最小，也相当于使得$\frac{1}{2}\mid\mid \vec{\omega} \mid\mid$最小，至于为什么有$\frac{1}{2}$和平方，在于方便对目标函数进行求导。
最后SVM问题可以转化为一个有不等式约束的最优化问题：
$$
\min \frac{1}{2}\mid\mid \vec{\omega} \mid\mid \\
s.t. \  1-y_i(\vec{\omega}^T\vec{x_i}+b)\leq0 \ \ \ \ \ i=1,2,3,...m
$$