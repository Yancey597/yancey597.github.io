---
title: Java流程控制和数组
top: false
cover: false
toc: true
author: Yancey
img: 'https://gitee.com/yancey597/img-load/raw/master/images/20220122022454.png'
summary: Java流程控制和数组
tags: Java
categories: 笔记
abbrlink: 2006
date: 2021-10-17 10:13:27
password:
---

# 三. 流程控制

> **三种基本流程结构**

**顺序结构
选择结构
循环结构**

## 1. 选择结构

> **条件表达式必须是布尔表达式（关系表达式或逻辑表达式）、布尔变量。**

**if - else 就近配对**

## 2. Scanner类的使用

> 从键盘获取不同类型的变量

```java
import java.util.Scanner;//1. 导包

class ScannerTest{
	public static void main(String[] args){
			Scanner scan = new Scanner(System.in);//2. 实例化
			
			int num = scan.nextInt();//3. 调用方法获取变量next();nextXxxx();
			System.out.println(num);
		
	}
}
```

## 3. Math.random生成随机数

```java
int score = (int)(Math.random() * 100)//random() -> 
//random -> 生成double类型的随机数 -> [0.0,1.0)
//可以由此变化出任意范围的随机数。
//公式:[a,b] : (int)Math.random() *(b - a + 1 ) + a
```

## 4. Switch-case语法

**Switch (表达式)：** **Byte、short、char、int、枚举类型(JDK5.0新增)、String(JDK7.0新增)**

## 5. 循环结构

```java
label:for (int i=1; i<=4; i++){
	for (int j=1; j<=10; j++){
		if (j % 4 == 0){
			continue label;//使用加标签的方式可以结束指定的循环
			//break label; 
		}
	}
}
continue //跳转到循环的自增；
```



# 四. 数组

> **数组(Array)，是多个相同类型数据按一定顺序排列的集合，并使用一个名字命名，并通过编号的方式对这些数据进行统一管理。**

**特性**
>数组名
>角标、下标(或索引)
> 元素
>数组的长度：元素的个数
>引用类型的变量

## 1. 一维数组

### 1.1 数组声明

```java
int[] ids = new int[]{1001,1002,1003,1004};//数组的声明；
```

### 1.2 数组长度

```java
String[] names = new String[5];
names.length//获取数组长度
```

### 1.3 数组默认初始化值

**int：0
double：0.0
String：
Char：(/u0000)
Bool：false
引用类型：null**

### 1.4 内存结构解析*

<img src="https://yancey597.github.io/posts/2006/1.jpg" ></img>


**堆、栈、方法区
堆：heap
存放着new出来的结构：对象、数组。

栈：stack
存放着局部变量：声明的一些变量。

方法区：method area
常量池：字符串
静态域：static
类加载的信息**

### 1.5 内存**实例解析**

<img src="https://yancey597.github.io/posts/2006/2.jpg" ></img>


****

> **我的理解：
堆存放数据，栈存放堆的地址。**
> 

## 2. 二维数组

### 2.1 二维数组声明

```java
int[][] array = new int[][]{{123},{2,3,4}};//二维数组的声明及初始化；
int[][] array = new int[3][5];//true
int[][] array = new int[3][];//true
int[][] array = new int[][3];//false
```

### 2.2 二维数组长度

```java
int[][] arr4 = new int[][]{{1,2,3},{4,5,9,10},{6,7,8}};
arr4.length  = 3;
arr4[1].length = 4;
```

### 2.3 二维数组默认初始化值

**外层初始化值为地址值
内层初始化值为一维数组值相同。**

**[3][ ]//未指定第二个参数
[3] → null;**

```java
int[][] array = new int[3][4];
		System.out.println(array[0]);//地址
		System.out.println(array[0][0]);//0
```

### 2.4 二维数组内存分析

<img src="https://yancey597.github.io/posts/2006/3.jpg" ></img>


## 3. 数据结构

**1.数据与数据之间的逻辑关系：**
集合、一对一、一对多、多对多

**2.数据的存储结构:**
线性表：顺序表（比如:数组)、链表、栈、队列
树形结构：二叉树
图形结构：

**算法：**

## 4. 数组的算法

**数组的遍历，赋值，复制，反转
数组的查找、排序**

### 4.1 查找

**二分法查找：**
**前提：所要查找的数组必须有序**。

### 4.2 排序

**评价排序算法的好坏**

**1.时间复杂度
2.空间复杂度
3.稳定性：两个记录的关键字相等，但不改变他们的位置关系**

**选择算法的分类**

**选择排序：**
>**直接选择排序、堆排序**

**交换排序：**
>**冒泡排序、快速排序**

**插入排序：**
>**直接插入排序、折半插入排序、Shell排序**

**归并排序、桶式排序**

**算法的特性**

**输入** (Input )
**输出** (Output)
**有穷性** (有限性，Finiteness)
**确定性**(明确性，Definiteness )
**可行性**（有效性，Effectiveness)

### 4.3 排序算法横比

<img src="https://yancey597.github.io/posts/2006/4.jpg" ></img>

<img src="https://yancey597.github.io/posts/2006/5.jpg" ></img>

### 4.4 数组工具类Arrays的使用

1. **判断两个数组是否相等：Boolean equals(int[] a, int[] b)**

```java
int[] a = new int[]{1,2,3,4};
int[] b = new int[]{1,2,3,4};
Boolean isEquals = Arrays.equals(a,b);
System.out.println(isEquals);// True
```

1. **遍历数组：String toString(int[] a)**

```java
int[] a = new int[]{1,3,4,2};
System.out.println(Arrays.toString(a));//[1,3,4,2]
```

1. **填充数组: void fill(int[] a, int val)**

```java
int[] a = new int[]{1,4,2,3};
Arrays.fill(a, 2);
System.out.println(a);//2,2,2,2
```

1. **排序数组：void sort(int[] a)**

```java
int[] a = new int[]{1,4,3,2};
Arrays.sort(a);
System.out.println(a);//1,2,3,4
```

1. **二分查找  [有序]  数组元素：int binarySearch(int[] a, int key)** 

```java
int[] a = new int[]{1,4,3,2};
Arrays.sort(a);
Arrays.binarySearch(a, 1);//0
```

### 4.5 数组常见错误

1. **数组角标越界**

```java
int[] a = new int[]{1,2,3,4};
a[4];//error;
// ArrayIndexOutOfBoundsException
```

2. **空指针异常**

```java
int[] a = new int[]{1,2,3,4};
a = null;
System.out.println(a[0]);//error
//NullPointerException
```
---

**永远相信美好的事情即将发生！**

**Yancey**
**2021-10-17 10:17:01**
