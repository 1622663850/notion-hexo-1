---
categories: 开发
updated: '2025-02-13 08:11:00'
tags:
  - C#
  - Solidworks二次开发
date: '2024-08-19 08:07:00'
cover: /images/16dc4ba5af3125d58e684cbad3c8e1bb.jpg
description: ''
title: C# SolidWorks 二次开发 API --- 把零件中的坐标点转换到总装配中
---

今天我们来看下solidworks中的坐标矩阵转换，这个例子是把子零件中的一个基准轴的两个端点读出来，并转换到总装配的坐标系中，得到在总装配体坐标系的位置，可以进一步判断轴的真实安装方向。


![image.png](/images/cfb76a87545ce791232c928e75ff1189.png)


直接上代码：


```c#
 private void btn_Transform_PartToAsm_Click(object sender, EventArgs e)
 {
    //连接到Solidworks

    //这个例子是把零件中的一个基准轴 的两个点的坐标转换到装配体中

    //请打开装配体，并在某个零件下选择一下基准轴

    ISldWorks swApp = Utility.ConnectToSolidWorks();

    ModelDoc2 swModel = (ModelDoc2)swApp.ActiveDoc;

    SelectionMgr swSelMgr = swModel.ISelectionManager;

    Feature swFeat = (Feature)swSelMgr.GetSelectedObject6(1, 0);

    String sAxisName = swFeat.Name;

    RefAxis RefAxis = swFeat.GetSpecificFeature2();

    var vParam = RefAxis.GetRefAxisParams();

    Component2 inletPart = swSelMgr.GetSelectedObjectsComponent4(1, 0);

    double[] nPt = new double[3];
    double[] nPt2 = new double[3];

    object vPt;
    object vPt2;

    nPt[0] = vParam[0]; nPt[1] = vParam[1]; nPt[2] = vParam[2];
    nPt2[0] = vParam[3]; nPt2[1] = vParam[4]; nPt2[2] = vParam[5];

    vPt = nPt;
    vPt2 = nPt2;

    MathUtility swMathUtil = (MathUtility)swApp.GetMathUtility();

    MathTransform mathTransform = inletPart.Transform2;

    MathTransform swXform = (MathTransform)mathTransform;

    MathPoint swMathPt = (MathPoint)swMathUtil.CreatePoint((vPt));

    MathPoint swMathPt2 = (MathPoint)swMathUtil.CreatePoint((vPt2));

    //swXform.Inverse(); 反转的话就是把装配体中的点坐标转到零件对应的坐标系统中

    swMathPt = (MathPoint)swMathPt.MultiplyTransform(swXform);

    swMathPt2 = (MathPoint)swMathPt2.MultiplyTransform(swXform);

    var x = swMathPt.ArrayData[0];
    var y = swMathPt.ArrayData[1];
    var z = swMathPt.ArrayData[2];
    var x2 = swMathPt2.ArrayData[0];
    var y2 = swMathPt2.ArrayData[1];
    var z2 = swMathPt2.ArrayData[2];

    var v1 = x2 - x;
    var v2 = y2 - y;
    var v3 = z2 - z;

    if (Math.Round(v3, 4) != 0 && Math.Round(v1, 4) == 0 && Math.Round(v2, 4) == 0)
    {
        MessageBox.Show("此轴在Z方向上");
    }

  
}
```


比较全的关于矩阵转换的一篇文章：


[bookmark](https://cadbooster.com/complete-overview-of-matrix-transformations-in-the-solidworks-api/#available-transformations-solidworks)

