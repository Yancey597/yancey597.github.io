---
title: Java语言概述
top: false
cover: false
toc: true
author: Yancey
tags: Java
categories: 笔记
abbrlink: 25287
date: 2021-10-06 12:59:23
img: 'https://gitee.com/yancey597/img-load/raw/master/images/20220122022454.png'
password: 
summary: Java 语言概述。
---
# Java语言概述

> Hello Java.
## 一、Java语言概述
### 1. 基础的DOS命令

```
dir:    列出当前目录下的文件及文件夹
md:   创建目录 make dictionary 
**rd:     删除目录**
cd:     进入指定目录
cd..:   退回到上一级目录
cd\:   退回到根目录
**del:   删除文件 针对目录的话是删除目录下的所有文件**
del *.txt :删除所有类型为txt的文件
exit:   退出命令行

echo name: Tom,age:12>1.doc 创建1.doc 并把内容放置进去

```

### 2. Java特性
#### 2.1 面向对象

**两个概念：** <font color = "red">类、对象</font>

**三大特征：** <font color = "red">封装、继承、多态</font>

#### 2.2 健壮性

去掉指针等、提供了<font color = "red">**相对安全的内存管理访问机制**</font>

#### 2.3 跨平台性

因为**JVM(Java虚拟机)**的存在，所以在不同的系统平台都可以运行。



<font color = "red">**Write once ,Run Anywhere.** </font>

#### **2.4 核心机制**
**JVM：**
**一个虚拟的计算机**，拥有指令集并使用不同的存储区域，负责执行指令，管理数据、内存、寄存器。
<img src="https://yancey597.github.io/javayuyangaishu/JVM.jpg#pic_center"></img>


**垃圾回收机制：**
在C/C++等语言，由程序员回收内存。
在Java中由程序自行控制，**<font color ="red">但还是会有内存泄露、溢出。</font>**

### 3. Java环境搭建

#### 3.1 Java环境有哪些

**JDK：**Java开发工具包
包括JRE、开发工具集（编译Javac.exe，打包jar.exe）。

**JRE：**Java运行环境
包括JVM和Java需要的核心类库。
<img src="https://yancey597.github.io/javayuyangaishu/JDK.jpg#pic_center" ></img>

#### 3.2 配置环境变量

> **为什么要配置环境变量？**

**PATH 环境变量:**是Windows系统执行命令时的搜索路径。
**配置的原因：** 希望Java开发指令在任何的文件路径下都可以执行。

#### 3.3 **配置方法**

**计算机属性 —> 高级设置 —>环境变量**

``` 
JAVA_HOME = JDK\bin的上一层目录   （添加为系统变量）
PATH = %JAVA_HOME%\bin        （添加为用户变量）

```

### 4. 开发体验 HelloWorld

#### 4.1 步骤

1. 将Java代码**编写**到扩展名为.java的文件中。<font color = "red">（源文件）</font>
2. 通过javac.exe对源文件进行**编译**生成class文件。<font color = "red">（字节码文件）</font>
3. 通过java.exe对class文件进行**运行**。
<img src="https://yancey597.github.io/javayuyangaishu/bianyi.jpg#pic_center" ></img>

### 5. 注释

**单行注释、多行注释、文档注释**

```java
/**
文档注释
@author yancey
@version 1.0
这是我的第一个Java程序。

*/
```

### 6 Java API

**API：**应用程序编程接口

JavaAPI文档：告诉开发者如何使用这些类，以及这些类里包含的方法。

### 7. HelloWorld的总结

#### 6.1 public类必须和文件名相同

```java
//Hello.java
public class Hello{
	public static void main(String[] args){
		System.out.println("Hello World");
}
}
//java里面可以有多个类，但只能有一个声明为public
//public只能加到和文件名相同的类中
```

####	 6.2 对输出语句的理解

```java
//
public class Hello{
	public static void main(String[] args){
		System.out.println("Hello World");//ln输出默认带换行符
		System.out.print("Hello World");//对比参照，此输出结果不带换行符
}
}
```
---
**永远相信美好的事情即将发生！**

**Yancey**
**2021-10-6 13:36:01**