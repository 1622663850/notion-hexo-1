---
categories: 开发
updated: '2024-05-15 13:38:00'
tags:
  - python
date: '2024-05-15 08:00:00'
cover: /images/676e58f53e170caf75c77817df0c367d.jpg
description: ''
title: 【Python】Python读取文件夹下的所有文件_python 读取文件夹里所有文件-CSDN博客
---

os.listdir(path)是得到在path路径下所以文件的名称列表。


open(path)是打开某个文件。


iter是python的迭代器。    


所以读取某文件夹下的所有文件如下：


```python
import os
path = "D:/Python34/news" #文件夹目录
files= os.listdir(path) #得到文件夹下的所有文件名称
s = []
for file in files: #遍历文件夹
     if not os.path.isdir(file): #判断是否是文件夹，不是文件夹才打开
          f = open(path+"/"+file); #打开文件
          iter_f = iter(f); #创建迭代器
          str = ""
          for line in iter_f: #遍历文件，一行行遍历，读取文本
              str = str + line
          s.append(str) #每个文件的文本存到list中
print(s) #打印结果
```


你也可以把遍历文件夹的操作定义成一个函数，如果是文件夹就不断迭代遍历。进而读取文件夹下所有的文件（包括文件夹里中的文件）

