---
title: Java基本语法
top: false
cover: false
toc: true
author: Yancey
img: 'https://gitee.com/yancey597/img-load/raw/master/images/20220122022454.png'
summary: Java 基本语法。
tags: Java
categories: 笔记
abbrlink: 22710
date: 2021-10-08 23:55:26
password:
---
# 二、Java基础语法

## 1. 关键字保留字

### 1.1 关键字的定义与特点

**定义：**Java中被赋予特殊含义，用做专门用途的字符串。

**特点：**全为小写。

### 1.2 保留字

**定义：**Java保留字:现有Java版本尚未使用，但以后版本可能会作为关键字。

**goto、const。**

## 2. 标识符

### 2.1 标识符定义

>Java对各种**变量、方法和类等要素**命名时使用的字符序列称为标识符。

><strong><font color = red>凡是可以自己起名字的地方都叫标识符</font></strong>
### 2.2 标识符命名规则

>由<strong> <font color = red>数字、字母、下划线、$</font> </strong>组成。
不能以数字开头，不能有空格。
不能使用关键字或保留字，但可以包含。
区分大小写。

### 2.3 标识符命名规范

**包名：**多字母**所有字母小写。**
**类名、接口名：多**单词<strong> <font color = red>每个单词首字母大写</font> </strong>（驼峰）
**变量名、方法名：**多单词**首字母小写**，其他大写（小驼峰）
**常量名：多单词大写，下划线分隔**
**要能够见名知义
Java 采用Unicode编码，可以用汉字声明，但不建议。**

## 3. 变量

### 3.1 变量的概念

**变量是程序中**<strong> <font color = red>最基本的存储单元</font> </strong>。
**包含** <strong> <font color = red>变量类型、变量名和存储的值。
变量作用域：{}。</font> </strong>

### 3.2 变量类型

**按数据类型来分：**

1. **基本数据类型**
    1. **数值型**
        1. 整数类型(byte,short,int,long)
        2. 浮点类型(float,double)
    2. **字符型**(char)
    3. **布尔型**(boolean)
2. **引用数据类型**
    1. 类(class) **字符串在这**
    2. 接口(interface)
    3. 数组(array)

    **按变量在类中声明的位置来分**

成员变量 vs 局部变量

### 3.3 整数类型

Java的整型常量**默认为 int型** ,声明long类型需要**加"l或L"。**

### 3.4 浮点类型

Java的浮点型常量**默认为double型**，声明float型常量，**须后加‘f'或‘F'。**

float表示数值的范围比long还大，因为浮点数在存储中是**以小数加幂的方式**存储

### 3.5 字符类型

Java中的所有字符**都使用Unicode编码**,所以一个字符可以表示字母、汉字或其他书面语的一个字符。

也可以用 Unicode值来表示，**\uxxxx**表示一个十六进制整数。

### **3.6 Boolean类型**

只能取**true、false**。用于条件判断、循环结构。

### 3.7 数值类型转换

**除了Boolean类型的基本数据类型**

1. **自动类型转换**
   
    **(byte、short、char)** → int → long → float → double **低精度 → 高精度**
    
    当byte、char、short 三种类型变量运算时，结果是**int**型。
    
    > **很重要！！！！**
    > 
    
2. **强制类型转换**
   
    **自动类型转换的逆运算**
    ```java
    double demo = 12.9
    int a = (int)demo;//向下取整，会造成精度损失
    
    //一个小细节
    
    long l = 123123;//没有L，可以编译；
    //右边默认是一个int类型, 赋值给一个long自动类型转换；
    
    float l = 12.9;//没有f，编译报错；
    //右边默认是一个double类型，赋值给float可能会精度损失，需要强制类型转换。
    
    byte b = 1；
    byte c = b + 1;//同样报错，原因与上述相同。 
```
### 3.8 字符串类型(String)

1. String属于**引用数据**类型。
2. 声明String类型变量时,使用**一对""**。

```java
String s1 = "";//可以为空
char c1 = ''//报错
char c1 = ' ';//可以
```

1. String**可以和8种基本数据**类型做运算，**只能做连接运算：+ 结果仍然是String类型**

```java
int number = 101;
String numberStr =“学号:";
String info = numberStr + number;
system.out.println(info) ;
```

Java中 + 的运算是**从左到右**。

1. 字符串**不能直接参与基本数据类型的赋值**，也**不能强制类型转换。**

```java
int num1 = Integer.parseInt(str1);//可以使用Integer.parseInt把字符串转换为int
system.out.println(num1); //123

```

## 4. 进制转换

> **世界上有10种人 ，认识和不认识二进制的。**
> 

### 4.1 进制的表示

```java
0b111;//二进制以0b/0B开头
061;//八进制以0开头
0x71;//十六进制以0x/0X开头
```

### 4.2 二进制整数的形式

> **二进制的整数有如下三种形式：**
> 

<strong> <font color = red>正数的原码反码补码：</font> </strong>直接将一个数值换成二进制数。最高位是符号位。

<strong> <font color = red>负数的反码</font> </strong>：是对**原码按位取反**，最高位（符号位）确定为1。
<strong> <font color = red>负数的补码</font> </strong>：其反码加1。

**Java整数常量默认是<strong> <font color = red>int类型</font> </strong>，当用二进制定义整数时，其第32位是符号位；
当是long类型时，二进制默认占64位，第64位是符号位**

**计算机底层都以补码的方式来存储数据！
可以只做加法。**

## 5. 运算符

### 5.1 算数运算符

**取余运算**

```java
%:取余运算
//结果的符号与被模数的符引

int m1 = 12;
int m2 = 5;
int m3 = -12;
int m4 = -5;

m1 % m2 = 2
m1 % m2 = 2
//不用刻意去记，仔细计算就行 
```

**自增运算**

```java
++:自增/自减运算
//注意区分++ & -- 前后位置带来运算结果的差异

short s1 = 10；
s1 += 1;//会报错！！需要强制类型转换~
//s1 = s1 + 1;

s1++;//正确，++不会改变本身变量的数据类型
```

### 5.2 赋值运算符

```java
+= 此类的运算符
不会改变变量的数据类型。
```

### 5.3 比较运算符

```java
instanceof //检查是否是类的对象；
"Hello" instanceof String >> true
```

### 5.4 逻辑运算符

```java
^ //异或
& && //逻辑与 短路与
| || //或 短路或
//短路是判断出结果就停止
```

### 5.5 位运算符

**操作整型数据，在一定范围类可以实现 x2 /2 的操作**

```java
<< //左移 x2
>> //右移 /2
>>> //无符号右移 
& //与运算
| //或运算
~ //取反运算
^ //异或运算
```

### 5.6 三元运算符

> **如果程序既可以使用三元运算符，又可以使用if-else结构，那么<strong> <font color = red>优先选择三元运算符。原因:简洁、执行效率高。</font> </strong>**
> 

### 5.7 运算符优先级

<img src="https://yancey597.github.io/posts/22710/1.jpg" ></img>

---

**永远相信美好的事情即将发生！**

**Yancey**
**2021-10-9 0:06:01**