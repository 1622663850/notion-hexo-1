---
categories: 开发
tags:
  - Github
cover: /images/78250f03a48282372838cec4ed6db402.jpg
description: ''
title: 使用git命令将代码上传到GitHub
date: '2024-05-09 22:09:00'
updated: '2024-05-09 22:26:00'
---

### **1.简介:**


计算机专业的朋友们想必肯定听说过git和[GitHub](https://so.csdn.net/so/search?q=GitHub&spm=1001.2101.3001.7020)这两个名词吧.


git是什么呢?


简单来说:git是一款最流行的版本控制工具.通过git可以用来进行代码的提交 更新 下载等.


GitHub是什么呢?


GitHub是全球最大的代码托管平台,全球的开发人员将自己的代码托管给这个平台.上面有很多开源的项目,大家一起协作开发,共同开发和维护一个项目;


公司的员工的话,大家可以通过这个平台一起协作开发一个项目;学生的话,可以将自己练习过的代码和做过的笔记,通过git推送到GitHub上,托管给GitHub,可以记录自己的学习过程,也可以将自己的代码做个云备份!!!


### **2.下载git**


(1)到[git官网](https://git-scm.com/),点击Downloads


![Untitled.png](/images/6d23d2336f956add230842e7f690ce4b.png)


(2)根据自己电脑的系统进行选择,因为我电脑是Windows系统,所以我点击Windows


![Untitled.png](/images/df8ef036e4b21f8d9d4f75d23756877b.png)


(3)根据自己电脑位数进行选择,我这里选择64位


![Untitled.png](/images/d59bbdca0f1d77ac0e2c3b156a83ea35.png)


(4)下载完成后,双击进行安装


![Untitled.png](/images/4673eb4b4f950080b253eef56384d611.png)


(5)选择好安装位置,然后一路next


![Untitled.png](/images/65dc1944c561418683adc97b1bf950a2.png)


(6)这里选择这个


![Untitled.png](/images/a6150c24f01acd0d6f4ff81c594b7e16.png)


(7)点击finish,表示安装完成


![Untitled.png](/images/501c76f6e4710ae6a9874377f543a9da.png)


### **3.在GitHub上建立远程仓库**


(1)到[GitHub官网](https://github.com/)


打不开的,这里推荐下载网易UU加速器.[官网下载地址戳这里](https://uu.163.com/)


![Untitled.png](/images/ae054cdde2aaff59556193762d53cc3e.png)


(2)搜索框里面搜索:学术资源


![Untitled.png](/images/7912f7471960755a462528357f4ffb44.png)


(3)点击"立即加速”


![Untitled.png](/images/90f2b6ddf8c68035cfa153f23b6b01ad.png)


![Untitled.png](/images/552c4a2a9b594a03372039fbbd6559b5.png)


![Untitled.png](/images/559fa8e6b017e98ad34e0bb9adbbd668.png)


(4)加速之后,会跳出下面这个页面


![Untitled.png](/images/aaf609904b01fbcc1efbe181f82c6f8c.png)


(5)之后再进[官网](https://github.com/),就会很流畅!!!


(6)没有GitHub账户的朋友们,可以先创建一个!!!


(7)创建一个仓库


![Untitled.png](/images/ce924ccab5d6edcd5d1e84ecd3d8a779.png)


(8)填写仓库相关信息,有:仓库名,仓库描述,


选择仓库公开还是私有…大家自己选择,(只有仓库名是必填的)


填好仓库信息之后,点击创建!


![Untitled.png](/images/30fd92e759035f4dd69d940671eb19f8.png)


(9)点击创建之后,会显示这个页面,表明远程仓库创建成功!!!


![Untitled.png](/images/ff63a31bea3c24549e9d5f99353387c5.png)


### **4.绑定用户**


(1)找到gitbash.exe.(可以在开始菜单里面寻找)


![Untitled.png](/images/47c531350df1e29f317a39b3fc2fb47e.png)


(2)因为Git是分布式版本控制系统，所以需要填写用户名和邮箱作为一个标识，用户和邮箱为你github注册的账号和邮箱


补充说明:git config --global 参数，有了这个参数，表示你这台机器上所有的Git仓库都会使用这个配置，当然你也可以对某个仓库指定的不同的用户名和邮箱。


```javascript
git config --global [user.name](http://user.name/) "用户名"
```


```javascript
git config --global user.email "邮箱"
```


![Untitled.png](/images/7bc2aa8a304cf74c5414a73f59a1266d.png)


### **5.在本地生成SSH key**


(1)生成ssh key


打开gitbash,输入


```javascript
ssh-keygen -t rsa -C "邮箱"
```


第一个提示输入是路径确认，直接按回车存默认路径即可


第二个提示输入直接回车键，这里我们不使用密码进行登录, 用密码太麻烦;


第三个提示输入直接回车键


![Untitled.png](/images/3cc35b98c1888ea43f1514011e06d7ec.png)


找到这个默认路径


![Untitled.png](/images/2313189370119ac76b522a6ae589c319.png)


用记事本打开id_rsa.pub,里面的便是ssh key公钥


![Untitled.png](/images/76c87e9d4f878c12d1cab2b42442ad00.png)


### **6.在GitHub上配置ssh key**


(1)点击头像旁边的三角,然后点击setting


![Untitled.png](/images/e82de3c06e24fc767eaf612611d6e6ce.png)


(2)点击这里


![Untitled.png](/images/bcc2a6ce1c7d8664907c704744eb53a4.png)


(3)点击New SSH KEY


![Untitled.png](/images/2baddcf00ca92747d88f02f6375beec7.png)


(4)


![Untitled.png](/images/ee239c1f2e4eac8db5da05c3e40232de.png)


(5)输入GitHub的密码进行确认


![Untitled.png](/images/83e76d44905ee4010490cb0e3de06718.png)


(6)这样ssh key便在GitHub上配置成功


![Untitled.png](/images/63a8492991bc1664689cb010f42d62f4.png)


(7)这意味着GitHub和本地电脑便建立起了联系!


### **7.将本地代码上传至GitHub**


### **整体过程:**


![Untitled.png](/images/a4a193692a07d1aed06a9a85eb7c169f.png)


(1)命令一:


在要上传的文件夹下,右键Git Bash Here


![Untitled.png](/images/4d5bab73297571917472d9a8930db5a8.png)


然后输入:


```javascript
git init
```


这个git命令是将当前文件夹变成用git管理的文件夹


![Untitled.png](/images/6ef954f43b9b9f8fe7e5c6de88d8a41e.png)


执行成功之后,勾选这个


![Untitled.png](/images/3cdfc2a5faf5637cc7c12e7a6fd5b290.png)


(2)命令二:


```javascript
git add .
```


这个命令是将当前文件夹下的所有文件添加到缓存中


![Untitled.png](/images/3362b7ae87ec833ccccc2b9122e943c4.png)


(3)命令三:


```javascript
git commit -m "提交信息"
```


这个命令是将缓存中的内容提交到本地仓库


![Untitled.png](/images/185954461c36fe1cb3db3f8e59200160.png)


(4)命令四:


找到GitHub上新建立完仓库之后的这句命令


![Untitled.png](/images/d77b3ab357698d82173de18b0e87314b.png)


```javascript
git remote add origin [https://github.com/ZhangXiangyu23/smallpaper.git](https://github.com/ZhangXiangyu23/smallpaper.git)
```


复制到git bash中


这句命令是建立本地仓库和GitHub远程仓库的联系!!!


![Untitled.png](/images/3b9ed985dcd3ba5b2d224dd6c603c363.png)


(5)命令五:


```javascript
git push -u origin master
```


这句命令是将本地仓库中的代码推送到GitHub远程仓库,第一次推送的话应该加-u参数.之后推送就不用加-u参数了


![Untitled.png](/images/7e351ebd10861da74857f0faffd5398e.png)


![Untitled.png](/images/569a8b860615fde1c486310a15a7c12b.png)


看看GitHub上的远程仓库,远程仓库上也显示上传成功了!!!


![Untitled.png](/images/6afbd1487230f8b0d160666777787585.png)


**哦,大功告成了!!!撒花!!!**

