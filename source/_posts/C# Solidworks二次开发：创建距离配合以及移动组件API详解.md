---
categories: 开发
updated: '2025-02-15 14:06:00'
tags:
  - C#
  - Solidworks二次开发
date: '2024-08-06 08:00:00'
cover: /images/fbfcbc0d1318ffec0aa374570746a68a.jpg
description: ''
title: C# Solidworks二次开发：创建距离配合以及移动组件API详解
---

今天要讲的文章是关于如何创建距离配合和移动组件的API详解。


## （1）创建配合API，CreateMate()


![Untitled.png](/images/0b3b229cd3beea6de870d3bc88415cd6.png)


这个API的解释是根据指定的特性数据对象来创建配合，也就可以理解为输入什么样的特征对象就可以创建出什么配合，这个API的输入[参数类型](https://so.csdn.net/so/search?q=%E5%8F%82%E6%95%B0%E7%B1%BB%E5%9E%8B&spm=1001.2101.3001.7020)为object，返回的参数类型为Feature。


而输入参数的类型有以下几种：


![Untitled.png](/images/976940b4be92f41fa56b1af708824003.png)


## （2）距离配合特征数据对象为


```c#
IDistanceMateFeatureData
```


这个特征对象中有几个比较常用的属性如下所示：


1、FlipDimension：bool类型，是否设置翻转维度。


2、MateAligment：int类型，翻译为对齐，具体值如下图所示：


![Untitled.png](/images/f0decdbc44485e9b591a007911f3af08.png)


3、Distance：double类型，距离配合值。


在使用距离配合时需要有一些注意的地方：


创建距离配合的时候，距离值不能输入负值，如果想要反向的话，可以把FlipDimension设置为true，这个设置就相当于Solidworks软件中距离值下方的反转尺寸打勾，也就实现了反向配合。我本人觉得这个功能设计的十分不便捷。


## （3）创建移动组件的API，Transform2（）


![Untitled.png](/images/ff491eafa828b67c7468e054c37098a0.png)


下面介绍一个使用的例子：


```c#
var swXfms = (double[])swComp1.Transform2.ArrayData;
swComp1.Select(true);
double[] TransformData = new double[16];
TransformData[0] = 1;
TransformData[1] = 0;
TransformData[2] = 0;
TransformData[3] = 0;
TransformData[4] = y;
TransformData[5] = 0;
TransformData[6] = 0;
TransformData[7] = 0;
TransformData[8] = 1;
TransformData[9] = totaldis;//X
TransformData[10] = 0;//Y
TransformData[11] = 0;//Z
TransformData[12] = 1;
TransformData[13] = 0;
TransformData[14] = 0;
TransformData[15] = 0;
var TransformDataVariant = TransformData;
var swMathUtil = (MathUtility)swApp.GetMathUtility();
var swTransform = (MathTransform)swMathUtil.CreateTransform((TransformDataVariant));
boolstatus = swComp1.SetTransformAndSolve2(swTransform);
```

