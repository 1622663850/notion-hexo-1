---
categories: 开发
updated: '2024-07-29 11:48:00'
tags:
  - C#
  - WPF
date: '2024-07-26 08:00:00'
cover: /images/a89cbd1df5e82421db4a402169fdee85.jpg
description: ''
title: WPF无边框可拖动窗体
---

下面主要记录下创建无边框窗体，并且可以拖动。这种窗体主要用于弹出小窗体时。


```c#
<Window x:Class="WpfApplication1.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        xmlns:local="clr-namespace:WpfApplication1"
        mc:Ignorable="d" WindowStyle="None"
        Title="MainWindow" Height="350" Width="525"  AllowsTransparency="True">

    <Grid Name="grid" Height="350" Width="525" Background="Transparent">       
    </Grid>   
</Window>
```


这里需要注意的是grid控件一定要设置一个background的用于焦点的捕捉。


后台代码：


```c#
  public MainWindow()
        {
            InitializeComponent();
            this.grid.MouseLeftButtonDown += (o, e) => { DragMove(); };
        }
```


这样就可以实现拖动窗体功能。

