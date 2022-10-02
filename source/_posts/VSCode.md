---
title: VSCode配置C/C++环境
author: Yancey
top: false
cover: false
toc: true
summary: VSCode 配置C/C++环境
tags: C/C++
categories: 技术分享
abbrlink: e2c5bfe8
date: 2022-01-16 06:04:41
img: 'https://gitee.com/yancey597/img-load/raw/master/images/image-20220122025027764.png'
password:
---

# VSCode 配置C/C++环境



## 1.VSCode 介绍

Visual Studio Code是一款由微软开发且跨平台的免费原始码编辑器。该软体支援语法突显、程式码自动补全、程式码重构功能，并且内建了命令列工具和 Git 版本控制系统。使用者可以更改布景主题和键盘捷径实现个人化设定，也可以透过内建的扩充元件程式商店安装扩充元件以加强软体功能。(Via:[维基百科](https://zh.wikipedia.org/wiki/Visual_Studio_Code))

<img src="https://gitee.com/yancey597/img-load/raw/master/images/image-20220122025027764.png"/>

## 二、下载VSCode

1.官网下载([官网链接](https://code.visualstudio.com/))

首先，通过搜索引擎或者点击上方链接进入VSCode官网，进入官网之后点击`Download for Windows`蓝色按钮旁边的下拉列表按钮，可以根据自身所用操作系统选取对应的版本。

> **Stable 与 Insiders版本的区别**
>
> Stable版本（蓝色）是稳定的发行版本，比较稳定
>
> Insiders版本（绿色）类似于Beta版本，会加入一些新功能，但可能存在Bug，

<img src="https://yancey597.github.io/posts/e2c5bfe8/image-20220116045834418.png" ></img>

Windows、Linux【默认提供的都是64位版本的】，如需32位版本点击红框下方的`Other downloads`即可

不知道自己的操作系统是32位还是64位的话(在我的电脑窗口中右击选择属性，即可查看)。

> **User Installer 和 System Installer的区别**
>
> The basic **differences between** the two is that the **system** version installs on the file **system** like every other app. The **user install** is basically a click-once (or web **installer**) version that installs **in the User** folder of the machine.(Via:[Quora](https://www.quora.com/What-is-the-difference-between-a-user-installer-and-a-system-installer))
>
> 两者之间的基本区别在于System版像其他所有应用程序一样安装在文件系统上，需要管理员权限。 
>
> User版基本上是安装在机器的用户文件夹中的单击一次（或 Web 安装程序）版本。  

<img src="https://yancey597.github.io/posts/e2c5bfe8/image-20220116050235142.png" ></img>

下载完成后，按提示安装,可以根据自己的个人情况选择安装路径。

在附加项`勾选添加到PATH`，可以在控制台打开VSCode，建议勾选，其余选项为可选项。

<img src="https://yancey597.github.io/posts/e2c5bfe8/image-20220116052040834.png" ></img>

## 三、配置环境

### 1. 设置简体中文环境

下载安装完后，打开VSCode，此时默认为英文环境，可根据自己的情况下载`Chinese语言包`实现汉化

<img src="https://yancey597.github.io/posts/e2c5bfe8/image-20220116052720865.png" ></img>



- 点击左侧边栏的`插件拓展中心`按钮进入插件拓展中心，在`搜索栏搜索Chinese` ,点击`Install`进行安装

<img src="https://yancey597.github.io/posts/e2c5bfe8/image-20220116052907063.png" ></img>



- 安装完后点击左下角`Restart按钮`或者手动重启即可完成对VSCode简体中文环境的配置

<img src="https://yancey597.github.io/posts/e2c5bfe8/image-20220116053130226.png" ></img>

<img src="https://yancey597.github.io/posts/e2c5bfe8/image-20220116053141621.png" ></img>

### 2.配置C/C++ 环境

> VSCode只是一款`文本编辑器`，不仅需要安装对应编程语言的扩展，还需要安装相应的`编译器或者解释器`。

#### 2.1 下载MinGW编译器

C/C++的编译器有很多，这里选择开源的MinGW编译器。大家可以从[官网下载](https://sourceforge.net/projects/mingw-w64/files/mingw-w64/mingw-w64-release/)上下载64位的编译器，直接打开进行安装。

`Version`选8.1.0最新版本，对语言的新特性有较好的支持；

`Architecture`是32位和64位的选择，32位请选择x86；

`Threads`选择win32(Linux选择posix；

`Exception`选择默认的seh;

<img src="https://yancey597.github.io/posts/e2c5bfe8/image-20220116053130226.png" ></img>

完成安装后，使用快捷键Win+R 输入Cmd 输入`gcc-v` 可以检查是否安装成功。

<img src="https://yancey597.github.io/posts/e2c5bfe8/image-20220116054109492.png" ></img>

#### 2.2 配置环境变量

在计算机窗口右击进入属性，点击`高级系统设置`，点击`环境变量`。

点击浏览，找到并将`MinGW\bin`目录放入环境变量，依次点击确定即可。

![image-20220116054310556](C:\Users\Yancey\Desktop\Programming master\Java\笔记\Java\image-20220116054310556.png)

#### 2.3 下载C\C++ 拓展

<img src="https://yancey597.github.io/posts/e2c5bfe8/image-20220116054704355.png" ></img>



#### 2.4 完成编译器配置

- 在VSCode界面，使用快捷键`Ctrl + Shift + p`，输入 `>C/C++`，选择编辑配置(UI);

<img src="https://yancey597.github.io/posts/e2c5bfe8/image-20220116054816053.png" ></img>



- 将编译器路径设置为刚刚下载好的路径bin下的`gcc.exe`

<img src="https://yancey597.github.io/posts/e2c5bfe8/image-20220116054921019.png" ></img>



- InteliSense 设置为自己系统对应的版本即可

<img src="https://yancey597.github.io/posts/e2c5bfe8/image-20220116055335079.png" ></img>



#### 2.4 测试

打开文件夹(`Ctrl + k + o`)，创建.c文件编写代码进行测试

- 编写完代码后点击`F5`即可开始调试
- 选择`C++(GDB)`

<img src="https://yancey597.github.io/posts/e2c5bfe8/image-20220116055726364.png" ></img>



- 选择`gcc.exe`(注意安装目录是否一致)

<img src="https://yancey597.github.io/posts/e2c5bfe8/image-20220116055733331.png" ></img>



- `Enjoy it!`

<img src="https://yancey597.github.io/posts/e2c5bfe8/image-20220116055710923.png" ></img>

## 四、Ending

尽管我自从用了Clion和IDEA后，打开VSC的次数屈指可数，但不可否认VSC仍然是一款不错轻量化的编辑器，搭配其拓展插件可以媲美部分IDE的体验，但用过IDEA后，我还是选择Jerbrains的IDE，Jerbrains YYDS！

<img src="https://yancey597.github.io/posts/e2c5bfe8/image-20220116060317042.png" ></img>



---
**永远相信美好的事情即将发生！**

**永远年轻，永远在路上。**

**Yancey**
2022.01.16

