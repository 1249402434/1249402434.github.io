---
title: 2021-03-15未命名文件 
tags: 新建,模板,小书匠
category: /小书匠/日记/2021-03
renderNumberedHeading: true
grammar_cjkRuby: true
---

<h1>feature map上采样</h1>
<h3>
1、插值法
</h3>
速度快，效果也不错。常用的插值法有最近邻、双线性、双三次等。在Pytorch框架中，使用nn.functional.interpolate()函数实现。
<h3>2、反卷积</h3>
<h4>
a、Transpose Convolution
</h4>
对输入做padding，然后对kernel做180度的顺时针旋转，再做正常卷积。通常来说，padding的大小根据kernel去判断，让第一次卷积只会计算feature map的第一个元素。最后计算出feature map的宽高是正向卷积的逆求解。
<h4>
b、微步卷积
</h4>
顾名思义就是stride<1。首先和转置卷积一样做padding，然后再在输入特征之间插入0，来使得步长变小。