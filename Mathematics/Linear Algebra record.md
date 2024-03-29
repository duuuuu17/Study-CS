# 线性代数部分笔记

此文档，主要用于记录线代的部分运算的实际意义。

The document's content is import of some theory that has some real means in the 3D-space。

## Vector：(向量)

### 基本含义：

向量相当于为

$$
\vec{x}= \begin{array}
{|c|}
x_{1}\\
x_{2}\\
 \vdots&\\
x_{n}
 \end{array},x\in{n-Dimensional(n\ components\ of\ numbers)}
$$

$$
another\ expression\ of\ vector\ is (x_1,x_2,\dots,x_n)
$$


$$
(x_1,x_2,\dots ,x_n)\ is\ a\ {(n-1)}-dimensional\ speace
$$

向量始终起始于原点，并且向量只能是平移。

可以利用坐标系，将分量看成不同的坐标轴所属位置，而构造出向量的空间意义。

它在线性运算（如：向量相加，向量的数乘）后，更多的表示是，他们在不同分量轴所做的运动距离

### 表示意义：

$$
In\ {2D}:\\
a\vec{v}+b\vec{w}\ (a,b \in R;\ \vec{v},\vec{w} \in basic\ vector)
$$

此处举例的是二维的基向量的线性运算表示，它所存在于二维空间中，并且它们的所有的a和b值，所得到的结果的集合(集合里可能有：零向量、一维向量（即二维中的一条线）和二维向量的一条线)，表示为整个二维空间，这个公式只是简单表示。

### 基向量：

基向量是线性无关的，不同的基向量可以组成n维空间。

$$
example:
2D:\vec{i}+\vec{j} \ (2D\ is\ compose\ of\  \vec{i}\ and\ \vec{j})
$$


### 线性相关：

概念：某一个向量是另外两个向量的运算组合。(当它们组成一个方阵时，因为有一行向量的值等于另两行的行线性变换，所以该det|方阵|=0，为奇异矩阵。再者通过向量间的线性相关的概念也可理解。)

从图形上理解就是：假设在三维空间(三维分量组成的空间)中，向量w和v线性运算后的所有线性集合可以组成一个平面，而向量u在前者所组成的平面内，向量u也就表示向量w和v的线性组合。

$$
\vec{u}=\vec{w}+\vec{v}
$$


### 线性无关：

概念:某一个向量不是另外两个向量的运算组合。（若在同一方阵，则为非奇异矩阵，即满秩矩阵）。

从图形上理解就是：假设在三维空间(三维分量组成的空间)中，向量w和v线性运算后的所有线性集合可以组成一个平面，而向量u不在前者所组成的平面内，向量u，向量w和v的线性组合可以表示整个三维空间。

$$
\vec{u} \neq \vec{w} + \vec{v}
$$

### 线性变换：

变换：指向量通过线性运算后，是保持网格平行等距变换：即直线在变换后仍为直线，其向量空间的原点也不会改变。当记住变换后的基向量，那么求其变换后的向量可以根据其进行计算。

$$
\vec{u}_{out} = a \vec{i}_{out} + b \vec{j}_{out}(in\ 2-dimensional\ speace)\\
\left [\begin{array}{cc}
i&j
\end{array} \right]_{2\times2}  (the\ matrix\ is\ composite\ of\ two\ basic\ verctor:ij )
$$

$$
\vec{u}_{out} = a \vec{x}_{out} + b \vec{y}_{out}+ c\vec{z}_{out}(in\ 3-dimensional\ speace)\\
\left [\begin{array}{ccc}
x&y&z
\end{array} \right]_{3\times3}  (the\ matrix\ is\ composite\ of\ three\ basic\ verctor:xyz )
 \\
$$

在三维空间中，其线性变换类似于二维空间，也是基于基坐标的变换，从而得到在变换后空间中的坐标。

### 行列式

**其空间意义，向量经过线性变换后的空间形体，是其原组成面积（二维）或体积（三维）的定向倍数关系。**

#### 注意

当行列式
$det(|n\times n|)=0$
时，我们可知其原方阵不可逆，为奇异（非满秩）矩阵。

**在空间上，表明原方阵可经过线性变换降维**

“取向”：也叫翻转。"定向"：也叫改变，旋转向指定的方向。

##### 二阶行列式中

$$
\det (\left[\begin{array}{cc} 
a&b\\
c&d
\end{array}\right])
$$



其bc有一个为0时，其空间为平行四边形，故bc表示的是**ab所构成的四边形对角的拉伸程度**。

空间理解

<img src=".\picture\二阶行列式.png" alt="image-20221030234944338" style="zoom:40%;" />

  
