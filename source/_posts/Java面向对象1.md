---
title: Java面向对象(上)
author: Yancey
top: false
cover: false
toc: true
img: 'https://gitee.com/yancey597/img-load/raw/master/images/20220122022454.png'
summary: 什么，你还没有对象？那你来对地方了！
tags: Java
categories: 笔记
abbrlink: 24752
date: 2022-01-13 23:59:22
password:
---
# 五、面向对象（上）



## 1. Java面向对象学习的三条路径

**1. Java类及类的成员：
属性、方法、构造器；代码块、内部类；

2. 面向对象的三大特征
封装性、继承性、多态性、(抽象性)；

3. 其它关键字
this、super、static、final、abstract、interface、import、package

大处着眼，小处着手。**

## 2. 面向过程和面向对象

**面向过程(POP) 与 面向对象(OOP)

1. 二者都是一种思想，面向对象是相对于面向过程而言的。

面向过程，强调的是功能行为，以函数为最小单位，考虑怎么做。
面向对象，将功能封装进对象，强调具备了功能的对象，以类/对象为最小单位，考虑谁来做。

2. 面向对象更加强调运用人类在日常的思维逻辑中采用的思想方法与原则，如
抽象、分类、继承、聚合、多态等**

### 2.1 面向过程和面向对象的例子对比

```java
//人把大象装进冰箱

//面向过程
1.把冰箱门打开
2.抬起大象,放进冰箱
3.关闭冰箱门

```

```java
//面向对象
人{
		//打开(冰箱){
					冰箱.open();
		}
		//抬起(大象){
					大象.setin(冰箱);
		}
		//关闭(冰箱){
					冰箱.close();
		}
}
冰箱{
			open(){}
			close(){}
}

大象{
			setin(冰箱){}
}
```

> **程序员从面向过程的执行者转化成了面向对象的指挥者**
> 

**面向对象分析方法分析问题的思路和步骤：

1. 根据问题需要选择问题所针对的现实世界中的实体。
2. 从实体中寻找解决问题相关的属性和功能，这些属性和功能就形成了概念世界中的类。
3. 把抽象的实体用计算机语言进行描述，形成计算机世界中类的定义。即借助某种程序
语言，把类构造成计算机能够识别和处理的数据结构。
4. 将类实例化成计算机世界中的对象。对象是计算机世界中解决问题的最终工具。**

**实体>(抽象)>属性、功能>(计算机语言描述)>类>(实例化类)>对象**

## 3.类和对象思想

### 3.1 思想概述

**类(Class)和对象(Object)是面向对象的核心概念。

1. 类是对一类事物的描述，是抽象的、概念上的定义。
2. 对象是实际存在的该类事物的每个个体，因而也称为实例(instance)。**

**面向对象程序设计的重点是类的设计
类的设计就是类的成员的设计。**

> **人是一个类，具体的某个人是一个对象**
> 

### 3.2 类属性、方法的概念

<img src="https://yancey597.github.io/posts/24752/1.jpg" ></img>

**Field = 属性 = 成员变量 = 域、字段
Method = 成员方法 = 函数

创建类对象 = 实例化类**

> **生活中描述事物无非就是描述事物的属性和行为。
如:人有身高，体重等属性，有说话，打球等行为。**
> 

### 3.3 类和对象的使用(面向对象思想落地的实现)

**1.创建类：设计类的成员。
2.创建类的对象。
3.通过"对象名.属性"或“对象名.方法"调用对象的结构。**

```java
**修饰符 class 类名 {
		属性声明;
		方法声明;
}
说明：修饰符public：类可以被任意访问
类的正文要用{ }括起来**
```

```java
public class PersonTest {
	public static void main(String[] args) {
		//类的实例化
		Person p1 = new Person();
		
		//调用类的属性、方法
		//调用属性："对象名.属性"
		p1.name = "Yancey";
		p1.age = 12;
		//调用方法："对象名.方法"
		p1.eat();
		p1.sleep();
		p1.talk("Chinese");
		
		System.out.println(p1.name);
	}
}

class Person{
	//属性
	String name;
	int age;
	boolean isMan;
	
	//方法
	public void eat() {
		System.out.println("人可以吃饭");
	}
	
	public void sleep() {
		System.out.println("人可以睡觉");
	}
	
	public void talk(String language) {
		System.out.println("人可以说话,使用的是" + language);
	}
```

### 3.4 类的多个对象

**如果创建了一个类的多个对象，则每个对象都独立的拥有一套类的属性(非static)。**

```java
Person p1 = new Person();
		Person p2 = new Person();
		p1.name = "Yancey";
		p1.age = 12;
		
		p2 = p1;//地址！
```

### 3.5 对象的内存解析

<img src="https://yancey597.github.io/posts/24752/2.jpg" ></img>

<img src="https://yancey597.github.io/posts/24752/3.jpg" ></img>

**虚拟机栈： 俗称的栈，局部变量放在栈中。**

**堆：**我们将**new出来的结构**(比如:数组、对象)加载在堆空间中。补充**:对象的属性**(非static的)加载在堆空间中。

**方法区：**类的加载信息、常量池、静态域。

### 3.6 理解万事万物皆对象

1. **在Java语言范畴中，我们都将功能、结构等封装到类中，通过类的实例化，来调用具体的功能结构。**
   
    >Scanner ,String等
    >文件:File
    >网络资源:URL
    
2. **涉及到Java语言与前端Html、后端的数据库交互时，前后端的结构在Java层面交互时，都体现为类、对象。**

### 3.7 匿名对象

1.理解：我们创建的对象，没有显式的赋给一个变量名。即为匿名对象

2.特征：匿名对象只能调用一次。

```java
public class AnonymousObject {
	public static void main(String[] args) {
		StudentFactory s1 = new StudentFactory();
		s1.showEat(new Student());//匿名对象的使用
	}
}

class StudentFactory{
	public void showEat(Student stu) {
		stu.eat();//调用student类的方法
	}
}

class Student{
	public void eat() {
		System.out.println("学生会吃饭！");
	}
}
```

### 4. 成员变量(属性)和局部变量的对比

```java
class user{
	String name;//属性(成员变量)
	int age;
	boolean isMale;
	
	public void talk(String language) {//形参
		String abc = "OK";//局部变量
		System.out.println("这个人说" + language);
		
	}
}
```

**相同点：**

1. **定义变量的格式：数据类型变量名 = 变量值**
2. **先声明，后使用**
3. **变量都有其对应的作用域**

**不同点：**

1. **在类中声明的位置不同**
   
    **成员变量：直接声明在类的{}内的变量**
    
    **局部变量：声明在方法内、方法形参、代码块内、构造器形参、构造器内部的变量**
    
2. **关于权限修饰符的不同
属性：可以在声明属性时，指明其权限，使用权限修饰符
常用的权限修饰符：private、 public、缺省、protected
局部变量：不能用权限修饰符(除了final，方法的权限即为局部变量的权限)**

3. **默认初始化值不同
属性：类的属性，根据其类型，都有默认初始化值
意味着，我们在调用局部变量之前，一定要显式赋值。
特别地：形参在调用时，我们赋值即可。**

4. **在内存中加载位置不同
属性：加载在堆空间中(非static)
局部变量：加载在栈空间**

<img src="https://yancey597.github.io/posts/24752/4.jpg" ></img>

## 4. 类中方法的声明、使用

> **方法：描述类应该具有的功能。
比如：Math类：sqrt()、random() 
Scanner类：nextXxx() ...
Arrays类：sort()、binarySearch()、toString()、equals() ...**
> 

### 4.1 方法的声明：

```java
**权限修饰符 返回值类型 方法名(形参列表){
	方法体
}

1. 权限修饰符：

		默认方法的权限修饰符先都使用public
Java规定的4种权限修饰符：private、public、缺省、protected

2. 返回值类型： 

		有返回值  vs 没有返回值
		如果方法有返回值，则必须在方法声明时，指定返回值的类型。
		方法中需要使用return关键字来返回指定类型的变量或常量：“return 数据”。

		如果方法没有返回值，则方法声明时，使用void来表示。通常，没有返回值的方法中，就不需要
		使用return。如果使用的话，只能“return;”表示结束此方法的意思。

3. 方法名：
		
		属于标识符，遵循标识符的规则和规范，“见名知意”**

4. 形参列表： 

		方法可以声明0个，1个，或多个形参。
		格式：数据类型1 形参1,数据类型2 形参2,...

5.方法体：方法功能的体现。
方法的使用中，可以调用当前类的属性或方法；
特殊的：方法A中又调用了方法A:递归方法。
方法中，不可以定义方法。

public static void main(String[] args){
	
}
注意：static、final、abstract 来修饰的方法，后面再讲**。

```

### 4.2 方法的重载

**重载的概念
在同一个类中，允许存在一个以上的同名方法，只要它们的参数个数或者参数
类型不同即可。

重载的特点：
与返回值类型无关，只看参数列表，且参数列表必须不同。(参数个数或参数类
型)。调用时，根据方法参数列表的不同来区别。**

```java
class overLoadTest{
	public void add(int i, int j) {
		int sum = i + j;
		System.out.println("两个数之和是"+ sum);
	}
	
	public void add(double i, double j) {
		double sum = i + j;
		System.out.println("The sum is " + sum);
	}
}//方法的重载
```

**通过对象调用方法时，如何确定执行指定的方法？**

**方法名 —> 参数列表**

### 4.3 可变参数的形参

**可变个数形参的格式：数据类型 ... 变量名

当调用可变个数形参的方法时，传入的参数个数可以是：0个,1个,2个，。。。
可变个数形参的方法与本类中方法名相同，形参不同的方法之间构成重载
可变个数形参的方法与本类中方法名相同，形参类型也相同的数组之间不构成重载。换句话说，二者不能共存。
可变个数形参在方法的形参中，必须声明在末尾
可变个数形参在方法的形参中,最多只能声明一个可变形参。**

```java
public class OverLoadTest2 {
	public static void main(String[] args) {
		OverLoadTest2 printtest = new OverLoadTest2();
		printtest.printTest("a","b","c");
	}
	
	public void printTest(String ... string) {//**可变个数形参在方法的形参中，必须声明在末尾
																						//可变个数形参在方法的形参中,最多只能声明一个可变形参。**
		for(int i = 0;i < string.length;i++) {
			System.out.println(string[i]);
		}
	}
}
```

### 4.4 方法中的值传递机制

> **方法的形参的传递机制：值传递**
> 

**形参：**

方法定义时，声明的小括号内的参数 

**实参：**

方法调用时，实际传递给形参的数据

**值传递机制**：

**如果参数是基本数据类型，此时实参赋给形参的是实参真实存储的数据值。**

**如果参数是引用数据类型，此时实参赋给形参的是实参存储数据的地址值。**

### 4.5 递归



## 5 封装与隐藏

> 为什么需要封装？封装的作用和含义？
> 我要用洗衣机，只需要按一下开关和洗涤模式就可以了。有必要了解洗衣机内部的结构吗？有必要碰电动机吗？

程序设计追求“高内聚，低耦合”。


高内聚 ：类的内部数据操作细节自己完成，不允许外部干涉；
低耦合 ：仅对外暴露少量的方法用于使用。
隐藏对象内部的复杂性，只对外公开简单的接口。便于外界调用，从而提高系统的可扩展性、可维护性。通俗的说，把该隐藏的隐藏起来，该暴露的暴露出来。这就是封装性的设计思想。


> 问题引入，属性封装性的体现：类的属性私有化，提供公共(Public)方法设置获取属性的值
> 拓展：封装性的体现：不对外暴露的私有方法，单例模式。
> 封装性的体现：需要权限修饰符的配合。

```java
class Animal{
	
	String name;
	int age;
	private int legs;//private修饰符
	
	//对某些特定属性的设置
	public void setLegs(int l) {
		legs = l;
		if(legs%2 != 0 || legs >=0) {
			legs = l;
		}else {
			legs = 0;
			//抛出一个异常，暂时没有讲
		}
	}
	//对属性的获取
	public int getLegs() {
		return legs;
	}
```

### 5.1 权限修饰符


Java规定的四种权限：从大到小
public、protected、缺省(default)、private。


可以修饰类及类的内部结构：属性、方法、构造器、内部类。

修饰类：只能是public、default。
总结封装性：Java提供了4种权限修饰符来修饰类及类的内部结构，体现类及类的内部结构在被调用时的可见性的大小。

<img src="https://yancey597.github.io/posts/24752/Untitled 13.png" ></img>

<img src="https://yancey597.github.io/posts/24752/Untitled 14.png" ></img>

## 6 构造器、构造方法的使用

### 6.1 构造器的作用：

**1.创建对象**

```java
class Person{
	String name;
	int age;
	
	public Person(){
		System.out.println("Person().....");
	} 

	public Person(String n){
		name = n;
	} 
	

}
```

**2.初始化对象的信息**

### 6.2 说明：

1.如果没有显式的定义类的构造器的话，则系统默认提供一个空参的构造器
2.定义构造器的格式：权限修饰符  类名(形参列表){}
3.一个类中定义的多个构造器，彼此构成重载
4.一旦我们显式的定义了类的构造器之后，系统就不再提供默认的空参构造器
5.一个类中，至少会有一个构造器。


### 6.3 属性赋值


总结：属性赋值的先后顺序

① 默认初始化
② 显式初始化
③ 构造器中初始化

④ 通过"对象.方法" 或 "对象.属性"的方式，赋值
以上操作的先后顺序：① - ② - ③ - ④



### 6.4 拓展知识：Java Bean

类是公共的：
有一个无参的公共的构造器
有属性，且有对应的get，set方法




### 6.5 UML图

<img src="https://yancey597.github.io/posts/24752/Untitled 15.png" ></img>

### 6.6 this 关键字

```java
class Person{
	String name;
	int age;
	
	public Person(){
		//空参构造器
	}
	
	public void setName(String name) {
		this.name = name;//当形参和类的属性名相同时需要用this关键字
	}
	
	public void age(int age) {
		this.age = age;
	}
}
```

1. this关键字的用途


this关键字的使用：


1.this 可以用来修饰、调用：属性、方法、构造器
2.this修饰属性和方法：
this理解为：当前对象  或 当前正在创建的对象**



1. **如何使用this关键字**


2.1  在类的方法中，我们可以使用"this.属性"或"this.方法"的方式，调用当前对象属性或方法。但是，通常情况下，我们都选择省略"this."。特殊情况下，如果方法的形参和类的属性同名时，我们必须显式的使用"this.变量"的方式，表明此变量是属性，而非形参。


2.2 在类的构造器中，我们可以使用"this.属性"或"this.方法"的方式，调用当前正在创建的对象属性或方法。但是，通常情况下，我们都选择省略"this."。特殊情况下，如果构造器的形参和类的属性同名时，我们必须显式的使用"this.变量"的方式，表明此变量是属性，而非形参。



1. **this调用构造器**


① 在类的构造器中，可以显式的使用"this(形参列表)"方式调用本类中指定的其他构造器
② 构造器中不能通过"this(形参列表)"方式调用自己
③ 如果一个类中有n个构造器，则最多有 n - 1构造器中使用了"this(形参列表)"
④ 规定："this(形参列表)"必须声明在当前构造器的首行
⑤ 构造器内部，最多只能声明一个"this(形参列表)"，用来调用其他的构造器




### 6.7 MVC设计模式

<img src="https://yancey597.github.io/posts/24752/Untitled 16.png" ></img>

<img src="https://yancey597.github.io/posts/24752/Untitled 17.png" ></img>

### 6.8 JDK常用包

<img src="https://yancey597.github.io/posts/24752/Untitled 18.png" ></img>

### 6.9 Package 关键字


package关键字的使用


1. 为了更好的实现项目中类的管理，提供包的概念
2. 使用package声明类或接口所属的包，声明在源文件的首行
3. 包，属于标识符，遵循标识符的命名规则、规范(xxxyyyzzz)、“见名知意”
4. 每"."一次，就代表一层文件目录。

补充：同一个包下，不能命名同名的接口、类。
不同的包下，可以命名同名的接口、类。**



### 6.10 import关键字的使用


import：导入**


1. **在源文件中显式的使用import结构导入指定包下的类、接口
2. 声明在包的声明和类的声明之间
3. 如果需要导入多个结构，则并列写出即可
4. 可以使用"xxx."的方式，表示可以导入xxx包下的所有结构

5. 如果使用的类或接口是java.lang包下定义的，则可以省略import结构
6. 如果使用的类或接口是本包下定义的，则可以省略import结构
7. 如果在源文件中，使用了不同包下的同名的类，则必须至少有一个类需要以全类名的方式显示。
8. 使用"xxx."方式表明可以调用xxx包下的所有结构。但是如果使用的是xxx子包下的结构，则仍需要显式导入

import static：导入指定类或接口中的静态结构：属性或方法。**



## 7. 继承性

> **面向对象的特征之二：继承性    why?
> extends：延展、扩展**

### 7.1 继承性的好处：


① 减少了代码的冗余，提高了代码的复用性
② 便于功能的扩展
③ 为之后多态性的使用，提供了前提**




### 7.2 继承性的格式


class A extends B{
}
A:子类、派生类、subclass
B:父类、超类、基类、superclass


体现：一旦子类A继承父类B以后，子类A中就获取了父类B中声明的所有的属性和方法。

 	特别的，父类中声明为private的属性或方法，子类继承父类以后，仍然认为获取了父类中私有的结构。因为封装性的影响，使得子类不能直接调用父类的结构而已。
 	
 	   子类继承父类以后，还可以声明自己特有的属性或方法：实现功能的拓展。

子类和父类的关系，不同于子集和集合的关系。**



### 7.3 继承性的规定


1. 一个类可以被多个子类继承。
2. Java中类的单继承性：一个类只能有一个父类
3. 子父类是相对的概念。
4. 子类直接继承的父类，称为：直接父类。间接继承的父类称为：间接父类
5. 子类继承父类以后，就获取了直接父类以及所有间接父类中声明的属性和方法**





<img src="https://yancey597.github.io/posts/24752/Untitled 19.png" ></img>

### 7.4 Object 类


如果我们没有显式的声明一个类的父类的话，则此类继承于java.lang.Object类
所有的java类（除java.lang.Object类之外）都直接或间接的继承于java.lang.Object类
意味着，所有的java类具有java.lang.Object类声明的功能。**




## 8. 方法的重写

### 8.1 概念


子类继承父类以后，可以对父类中同名同参数的方法，进行覆盖操作**




### 8.2 应用


重写以后，当创建子类对象以后，通过子类对象调用子父类中的同名同参数的方法时，实际执行的是子类重写父类的方法。**




### **8.3重写的规定**


方法的声明： 


权限修饰符 返回值类型 方法名(形参列表) throws 异常的类型{
//方法体
}

约定俗称：子类中的叫重写的方法，父类中的叫被重写的方法
① 子类重写的方法的方法名和形参列表与父类被重写的方法的方法名和形参列表相同
② 子类重写的方法的权限修饰符不小于父类被重写的方法的权限修饰符

特殊情况：子类不能重写父类中声明为private权限的方法

③ 返回值类型：
父类被重写的方法的返回值类型是void，则子类重写的方法的返回值类型只能是void
父类被重写的方法的返回值类型是A类型，则子类重写的方法的返回值类型可以是A类或A类的子类
父类被重写的方法的返回值类型是基本数据类型(比如：double)，则子类重写的方法的返回值类型必须是相同的基本数据类型(必须也是double)
④ 子类重写的方法抛出的异常类型不大于父类被重写的方法抛出的异常类型

子类和父类中的同名同参数的方法要么都声明为非static的（考虑重写），要么都声明为static的（不是重写）。**



## 9 super关键字

> **super关键字的使用
> 1.super理解为：父类的
> 2.super可以用来调用：属性、方法、构造器**

### 9.1 **super调用属性和方法**


在子类的方法或构造器中。通过使用"super.属性"或"super.方法"的方式，显式的调用
父类中声明的属性或方法。但是，通常情况下，我们习惯省略"super."
特殊情况：当子类和父类中定义了同名的属性时，我们要想在子类中调用父类中声明的属性，则必须显式的使用"super.属性"的方式，表明调用的是父类中声明的属性。


特殊情况：当子类重写了父类中的方法以后，我们想在子类的方法中调用父类中被重写的方法时，则必须显式的
使用"super.方法"的方式，表明调用的是父类中被重写的方法。**



### 9.2 super调用构造器


💡 
**在子类的构造器中显式的使用"super(形参列表)"，调用父类中声明的指定的构造器"super(形参列表)"的使用，必须声明在子类构造器的首行！
在类的构造器中，针对于"this(形参列表)"或"super(形参列表)"只能二选一，不能同时出现
在构造器的首行，没有显式的声明"this(形参列表)"或"super(形参列表)"，则默认调用的是父类中空参的构造器：super()
在类的多个构造器中，至少有一个类的构造器中使用了"super(形参列表)"，调用父类中的构造器。**




### 9.3 子类对象实例化的全过程


从结果上来看：（继承性）
子类继承父类以后，就获取了父类中声明的属性或方法。
创建子类的对象，在堆空间中，就会加载所有父类中声明的属性。**





从过程上来看：
当我们通过子类的构造器创建子类对象时，我们一定会直接或间接的调用其父类的构造器，进而调用父类的父类的构造器，直到调用了java.lang.Object类中空参的构造器为止。正因为加载过所有的父类的结构，所以才可以看到内存中有父类中的结构，子类对象才可以考虑进行调用。


明确：虽然创建子类对象时，调用了父类的构造器，但是自始至终就只创建过一个对象，即为new的子类对象。**



## 10 多态性

> **多态性：可以理解为一个事物的多种形态。**

<img src="https://yancey597.github.io/posts/24752/Untitled 20.png" ></img>


何为多态性：
对象的多态性：父类的引用指向子类的对象（或子类的对象赋给父类的引用）


多态的使用：虚拟方法调用
有了对象的多态性以后，我们在编译期，只能调用父类中声明的方法，但在运行期，我们实际执行的是子类重写父类的方法。
总结：编译，看左边；运行，看右边。

多态性的使用前提：  ① 类的继承关系  ② 方法的重写
对象的多态性，只适用于方法，不适用于属性（编译和运行都看左边）**



### 10.2 instanceof 操作符

> **x instanceof A：检验x是否为类A的对象，返回值为boolean型。**

**有了对象的多态性以后，内存中实际上是加载了子类特有的属性和方法的，但是由于变量声明为父类类型，导致编译时，只能调用父类中声明的属性和方法。子类特有的属性和方法不能调用。**

**需要使用向下转型：使用强制类型转换符。**

```java
class Book{
}

class EnglishBook extends Book{
}

Book book = new Book();
EnglishBook englishbook = (EnglishBook)Book;
```

### 10.2 重载和重写的区别


重载：是指允许存在多个同名方法，而这些方法的参数不同。编译器根据方法不同的参数表，对同名方法的名称做修饰。对于编译器而言，这些同名方法就成了不同的方法。它们的调用地址在编译期就绑定了。Java的重载是可以包括父类和子类的，即子类可以重载父类的同名不同参数的方法。在方法调用之前，编译器就已经确定了所要调用的方法，
这称为“早绑定”或“静态绑定”；


多态：只有等到方法调用的那一刻，解释运行器才会确定所要调用的具体方法，这称为“晚绑定”或“动态绑定”。**



## 11 Object类的使用

> **主要结构
> 1 public Object() 构造 构造器
> 2 public boolean equals(Object obj) 普通 对象比较
> 3 public int hashCode() 普通 取得Hash码
> 4 public String toString() 普通 对象打印时调用**

### 11.1 ==操作符与equals方法


== :
基本类型比较数据值：值相等即为true
引用类型比较引用：指向同一个对象时为true
符号两边的数据类型必须兼容(可自动转换的基本数据类型除外)


equals：
只能比较引用类型，其作用与“==”相同，比较是否指向同一个对象。
格式：obj1.equals(obj2)
特例：当用equals()方法进行比较时，对类File、String、Date及包装类
（Wrapper Class）来说，是比较类型及内容而不考虑引用的是否是同一个对
象；**



### 11.2 ==和equals的区别


1 == 既可以比较基本类型也可以比较引用类型。对于基本类型就是比较值，对于引用类型
就是比较内存地址


2 equals的话，它是属于java.lang.Object类里面的方法，如果该方法没有被重写过默认也
是==；我们可以看到String等类的equals方法是被重写过的，而且String类在日常开发中
用的比较多，久而久之，形成了equals是比较值的错误观点。

3 具体要看自定义类里有没有重写Object的equals方法来判断。

4 通常情况下，重写equals方法，会比较类中的相应属性是否都相等。**



**基本数据类型用 == ，引用数据类型用equals**

### 11.3 toString 方法

> **toString()方法在Object类中定义，其返回值是String类型，返回类名和它的引用地址。**

**在进行String与其它类型数据的连接操作时，自动调用toString()方法**

```java
Date now=new Date();
System.out.println(“now=”+now); 相当于
System.out.println(“now=”+now.toString());
```

## 12 单元测试方法

> **Java中的 JUnit 单元测试**


步骤：
1. 选择当前工程，右击选择：build path — add libraries — JUnit 5 下一步
2. 创建Java类，进行单元测试，一般测试什么就命名为：testXxx
    对Java类的要求： 此类为public，无参数构造器。
3. 创建Java 单元测试方法。
    对方法的要求：此方法为public，无参数无返回值。
4. 测试方法需要加上注解：@Test，并在单元测试类导入import org.junit.Test
5. 在方法体类写需要测试的方法。
6. 双击单元测试方法名，run as JUnit test**




## 13 包装类的使用

<img src="https://yancey597.github.io/posts/24752/Untitled 21.png" ></img>

<img src="https://yancey597.github.io/posts/24752/Untitled 22.png" ></img>

> **装箱：包装类使得一个基本数据类型的数据变成了类。
> 有了类的特点，可以调用类中的方法。**

### 13.1 装箱和拆箱

**装箱：把基本数据类型转化为包装类**

**拆箱：把包装类对象转化为基本数据类型**

**JDK高版本可以实现自动装箱和拆箱**

```java
Integer i = 10;
int i1 = 11;
Integer i2 = 12;
```

### 13.2 **字符串转基本数据类型**

**谁转谁使用 parse+数据类型**

```java
String name = "1231";
int i1 = Integer.parseInt(name);
System.out.println(i1);//1231

String trueS = "true";
boolean b1 = Boolean.parseBoolean(trueS);//特别的，当字符串的数据不是true时均为false
System.out.println(b1);//true
```

### 13.3 **基本数据类型变字符串**

1. **利用字符串拼接**
2. **利用Integer.toString**

```java
int i2 = 1234;
		String s1 = i2 + "";
		System.out.println(s1);//1234

int i3 = 2222;
		String s3 = Integer.toString(i3);
		System.out.println(s3);

String name = String.valueOf(111);
```

### 13.4 两道面试题的理解

**三目运算符**

```java
Object o1 = true ? new Integer(1) : new Double(2.0);
		System.out.println(o1);//
		Object o2;
		if (true)
			o2 = new Integer(1);
		else
			o2 = new Double(2.0);
		System.out.println(o2);

//o1 是 1.0 而不是1，因为三目运算符的使用需要两个条件为相同的数据类型
//所以此处会进行自动数据类型提升
```

**Integer 封装类含有IntegerCache（-128~127）**

使用如上范围的int数据时不会重新在堆空间里面new出对应的结构，而是调用IntegerCache。

```java
public void method1() {
Integer i = new Integer(1);
Integer j = new Integer(1);
System.out.println(i == j);
Integer m = 1;
Integer n = 1;
System.out.println(m == n);//true
Integer x = 128;
Integer y = 128;
System.out.println(x == y);//false
}
```

# 


---
**永远相信美好的事情即将发生！**

**Yancey**
{{ date }}