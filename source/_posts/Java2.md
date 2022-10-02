---
title: Java面向对象(下)
author: Yancey
top: false
cover: false
toc: true
img: 'https://gitee.com/yancey597/img-load/raw/master/images/20220122022454.png'
summary: 什么，你还没有对象？那你来对地方了！
tags: Java
categories: 笔记
abbrlink: a60e6267
date: 2022-01-22 02:18:03
password:
---

# 六、面向对象（下）

## 1.static 关键字的应用

static可以用来修饰：属性、方法、代码块、内部类

### 1.1 修饰属性

使用static修饰属性：静态变量（或类变量）


属性分为：静态属性  vs 非静态属性(实例变量)

实例变量：我们创建了类的多个对象，每个对象都独立的拥有一套类中的非静态属性。当修改其中一个对象中的非静态属性时，不会导致其他对象中同样的属性值的修改。

静态变量：我们创建了类的多个对象，多个对象`共享同一个静态变量`。当通过某一个对象修改静态变量时，会导致其他对象调用此静态变量时，是修改过了的。

![](https://gitee.com/yancey597/img-load/raw/master/images/%E9%9D%99%E6%80%81%E4%BF%AE%E9%A5%B0%E6%88%90%E5%91%982.JPG)

### 1.2 static修饰属性的其他说明：

- 静态成员跟随自己的类进入到元数据区(静态区域)

- 静态成员属于自己的类,不属于对象

- 静态成员进入内存后,赋默认值

- 静态成员变量的初始化实际早于对象

  - 类变量	实例变量

  类		yes		no
  对象		yes		yes

- 静态属性举例：System.out; Math.PI;


![](https://gitee.com/yancey597/img-load/raw/master/images/%E9%9D%99%E6%80%81%E4%BF%AE%E9%A5%B0%E6%88%90%E5%91%98%E7%9A%84%E5%86%85%E5%AD%98%E5%9B%BE3.JPG)

```java
public class Person{
	static int i;
	
	public static void add(){
	}
}
```

### 1.3 使用static修饰方法：静态方法

- `随着类的加载而加载`，可以通过"类.静态方法"的方式进行调用
  - ​	静态方法	非静态方法

类.		yes		no
对象.	  yes		yes

- `静态方法`中，`只能调用静态`的方法或属性
  `非静态方法`中，`既可以`调用非静态的方法或属性，`也可以`调用静态的方法或属性

### 1.4 static注意点：

- 在静态的方法内，不能使用this关键字、super关键字
- 关于静态属性和静态方法的使用，大家都从生命周期的角度去理解。

### 1.5 如何确定是否要声明为static

属性是可以被多个对象`所共享的`，不会随着对象的不同而不同的。

类中的常量也常常声明为static



开发中，如何确定一个方法是否要声明为static的？

- 操作静态属性的方法，通常设置为static的

- 工具类中的方法，习惯上声明为static的。 比如：Math、Arrays、Collections


### 1.6 单例模式

1. 所谓类的`单例设计模式`，就是采取一定的方法保证在整个的软件系统中，对`某个类只能存在一个对象实例`。
2. 如何实现？
   饿汉式 vs 懒汉式
3. 区分饿汉式 和 懒汉式

**饿汉式：**

坏处：对象加载时间过长。
好处：饿汉式是线程安全的

```java
class Order{
	private  Order(){
	}//私有化构造器
	
	private static Order order = new Order();//创建静态对象
	
	public static Order getOrder()[
		return order;//创建静态方法返回静态对象
	}

}
```

**懒汉式**：
好处：延迟对象的创建。
目前的写法坏处：线程不安全。--->到多线程内容时，再修改

```java
class Order{
	private Order(){
	}

	private static Order order = null;
	
	private static Order getOrder(){
		if(order == null){
			order = new Order();
		}
		return order;
	}
}
```

### 1.7 main 方法理解

```java
main()方法的使用说明：
 1. main()方法作为程序的入口
 2. main()方法也是一个普通的静态方法
 3. main()方法可以作为我们与控制台交互的方式。（之前：使用Scanner）
    

public static void main(){
    
}

- public 最大权限 : main方法的调用者是JVM
- static 无需对象,被类名直接调用,JVM启动的时候使用类名.main启动程序
- void 无返回值,调用者是JVM,方法的返回值都是返回给调用者,JVM不需要返回值,没有意义
- main 固定方法名称
- args  字符串的数组,JVM调用方法main必须传递参数,后期对JVM设置参数
```

## 2.代码块

代码块的作用：用来`初始化类、对象`
分类：静态代码块 vs 非静态代码块
代码块如果有修饰的话，只能使用static


### 2.1 **静态代码块**

内部可以有输出语句
随着类的加载而执行,而且`只执行一次`

作用：`初始化类的信息`(数据库连接池等)
如果一个类中定义了多个静态代码块，则按照声明的先后顺序执行
静态代码块的执行要优先于非静态代码块的执行
静态代码块内只能调用静态的属性、静态的方法，不能调用非静态的结构

```java
public class Person{
	static int a;
	static{
			a = 1;
	}
	
	public Person(){};

	public static void main(String[] args){
		//a = 1;//随着类的加载只执行一次
	}
}
```

### 2.2 非静态代码块

内部可以有输出语句
随着`对象的创建而执行`
每`创建一个对象`，就`执行一次`非静态代码块
作用：可以在创建对象时，对对象的属性等进行初始化

如果一个类中定义了`多个非静态代码块`，则按照声明的`先后顺序执行`
非静态代码块内可以调用静态的属性、静态的方法，或非静态的属性、非静态的方法

```java
public class Person{
	static int a;
	static{
			a = 1;
	}
	
	public Person(){};

	public static void main(String[] args){
		new Person();
		//a = 1;//随着对象的创建执行
	}
}
```

**初始化过程**

> class ——> static ——> 代码块 ——> 构造器

- 父类.class文件先进入内存
- 子类.class文件再进入内存
- 初始化父类的静态成员(变量,代码块,方法)
- 初始化子类的静态成员
- 运行父类的静态代码块
- 运行子类的静态代码块
- 运行父类的构造代码块
- 运行父类的构造方法
- 运行子类的构造代码块
- 运行子类的构造方法

### 2.3 对属性可以赋值的位置

①默认初始化
②显式初始化/⑤在代码块中赋值
③构造器中初始化
④有了对象以后，可以通过"对象.属性"或"对象.方法"的方式，进行赋值

执行的先后顺序：① - ② / ⑤ - ③ - ④

## 3.final关键字

>final可以用来修饰的结构：类、方法、变量

修饰类：此类不能被其他类所继承。
比如：String类、System类、StringBuffer类

修饰方法：表明此方法不可以被重写
比如：Object类中getClass();
修饰变量：此时的"变量"就称为是一个常量

1. 修饰属性：可以考虑赋值的位置有：显式初始化、代码块中初始化、构造器中初始化

2. 修饰局部变量：
   尤其是使用final修饰形参时，表明此形参是一个常量。当我们调用此方法时，给常量形参赋一个实参。一旦赋值以后，就只能在方法体内使用此形参，但不能进行重新赋值。

**static final 用来修饰属性：全局常量**



```java
public final class Person{
	final int LEFT = 1;//显式初始化
	final int RIGHT;

static{
	RIGHT = 3;//代码块初始化
}

public Person(){
	RIGHT = 3;//构造器初始化
}

public final void test(final i){
	i++;//error;
}
	
}

public class Stu extends Person//error;
```

> final 表示该类、变量、方法是最终的，所以不能被重写、继承、改变

### 3.1 抽象类

> 随着继承层次中一个个新子类的定义，类变得越来越具体，而父类则更一般，更通用。类的设计应该保证父类和子类能够共享特征。有时将一个父类设计得非常抽象，以至于它没有具体的实例，这样的类叫做抽象类

用abstract关键字来修饰一个类，这个类叫做抽象类。

用abstract来修饰一个方法，该方法叫做抽象方法。

抽象方法：只有方法的声明，没有方法的实现。以分号结束：

```java
abstract class Person{
    
}

public abstract void talk();

```

`含有抽象方法`的类必须被声明为`抽象类`。

抽象类`不能被实例化`。抽象类是用来被继承的，抽象类的`子类必须重写父类的抽象方法`，并提供方法体。若`没有重写全部`的抽象方法，`仍为抽象类`。

不能用abstract修饰变量、代码块、构造器；

不能用abstract修饰私有方法、静态方法、final的方法、final的类。

> 有抽象方法一定是抽象类，抽象类不能被实例化。

### 3.2 模板方法设计

当功能内部`一部分实现是确定的`，`一部分实现是不确定的`。这时可以`把不确定的部分暴露出去`，`让子类去实现`。
换句话说，在软件开发中实现一个算法时，整体步骤很固定、通用，这些步骤已经在父类中写好了。

但是某些部分易变，易变部分可以抽象出来，供不同子类实现。这就是一种模板模式。

> 当一个问题`求解方式的步骤已经确定`，可以使用模板方法设计`利用多态把需要改变的某些代码重写`即可。

```java
abstract class Template{
	
	public final void getTime() {
		long start = System.currentTimeMillis();
		code();
		long end = System.currentTimeMillis();
		System.out.println("执行时间是：" + (end - start));
	}
	public abstract void code();	//模板方法设计
}

class Test extends Template{
	int sum;
	public void code() {
		for (int i = 0;i<1000000;i++) {
			sum += i;
		}
	}
```

## 4.接口 interface

**接口:就是一个规范,或者称为标准**，无论什么设备,只要符合接口标准,就可以正常使用。接口的扩展性很强大。

当一个抽象类中的所有方法全部是抽象的时候,可以将这个抽象类换一个更加贴切的名词,叫他接口。接口是`特殊的抽象类`。

### 4.1 接口的使用

1. 接口使用interface来定义

   ```java
   public interface 接口名{}//接口在编译后,依然还是.class文件
   ```

2. Java中，接口和类是`并列的两个结构`

3. 如何定义接口：定义接口中的成员

​	3.1 JDK7及以前：只能定义全局常量和抽象方法
​		>`全局常量`：public static final的.但是书写时，可以省略不写
​		>`抽象方法`：public abstract的

```JAVA
public static final 数据类型  变量名 = 值 ;
public abstract 返回值类型 方法名(参数列表) ;
```

​	3.2 JDK8：除了定义全局常量和抽象方法之外，还可以定义`静态方法、默认方法`（略）**

### 4.2 注意事项


- 接口中不能定义构造器的！意味着接口不可以实例化
- Java开发中，接口通过让类去实现(implements)的方式来使用
  如果实现类`重写`了接口中的`所有抽象方法`，则此实现类就`可以实例化`
  如果实现类没有覆盖接口中所有的抽象方法，则此实现类仍为一个抽象类
- Java类`可以实现多个接口` --->弥补了Java单继承性的局限性
  格式：class AA extends BB implements CC,DD,EE
- 接口与接口之间`可以继承`，而且可以多继承
- 接口的具体使用，体现多态性
- 接口，实际上可以看做是一种规范

**接口的使用**

1. 接口使用上也`满足多态性`
2. 接口，实际上就是定义了一种规范
3. 开发中，体会面向接口编程！




### 4.2 Java 8新特性

JDK8：除了定义全局常量和抽象方法之外，还可以定义静态方法、默认方法

public interface CompareA 

```java
/code//静态方法
public static void method1(){
	System.out.println("CompareA:北京");
}
//默认方法
public default void method2(){
	System.out.println("CompareA：上海");
}

default void method3(){
	System.out.println("CompareA：上海");
}
}
```

```java
package com.atguigu.java8;

public class SubClassTest {
	
	public static void main(String[] args) {
		SubClass s = new SubClass();
		
//		s.method1();
//		SubClass.method1();
		//知识点1：接口中定义的静态方法，只能通过接口来调用。
		CompareA.method1();
		//知识点2：通过实现类的对象，可以调用接口中的默认方法。
		//如果实现类重写了接口中的默认方法，调用时，仍然调用的是重写以后的方法
		s.method2();
		//知识点3：如果子类(或实现类)继承的父类和实现的接口中声明了同名同参数的默认方法，
		//那么子类在没有重写此方法的情况下，默认调用的是父类中的同名同参数的方法。-->类优先原则
		//知识点4：如果实现类实现了多个接口，而这多个接口中定义了同名同参数的默认方法，
		//那么在实现类没有重写此方法的情况下，报错。-->接口冲突。
		//这就需要我们必须在实现类中重写此方法
		s.method3();
		
	}
	
}

class SubClass extends SuperClass implements CompareA,CompareB{
	
	public void method2(){
		System.out.println("SubClass：上海");
	}
	
	public void method3(){
		System.out.println("SubClass：深圳");
	}
	
	//知识点5：如何在子类(或实现类)的方法中调用父类、接口中被重写的方法
	public void myMethod(){
		method3();//调用自己定义的重写的方法
		super.method3();//调用的是父类中声明的
		//调用接口中的默认方法
		CompareA.super.method3();
		CompareB.super.method3();
	}
}
```

## 5.内部类

> 概述 : 所谓内部类,就是在一个类的内部,定义了另外的一个类

```java
class A{ //外部类,封闭类
    class B{} //内部类,嵌套类
}
```

### **5.1 成员内部类**

成员内部类,是一个类定义在了另一个类的成员位置。

这个内部类可以使用成员修饰符,public static final private。

对于`内部`来说 : `可以直接使用外部类的成员`,如果`外部类要使用内部类的成员`,必须要`创建对象`.

> //公式 : 外部类名.内部类名 = new 外部类对象().new 内部类对象()

```java
 //外部类
 public class Outer {
 
     public void outer(){
         System.out.println("外部类的方法outer");
     }
 
     //内部类
     public class Inner{
        public void inner(){
            System.out.println("内部类的方法inner");
        }
     }
 }
```

```java
 public static void main(String[] args) {
     //调用内部类的方法inner()
     Outer.Inner oi = new Outer().new Inner();
     oi.inner();
 }
```

问题 : `内部类`Inner`,编译后`有class文件吗?有class文件,`名字是外部类$内部类`

内部类也是类,继承Object,可以实现接口

> 内部类是静态的调用方式 : `外部类名.内部类名 变量名 = new 外部类.内部类()`

### **5.2 局部内部类**

局部内部类 : 要定义在方法里面. 方法里面是局部位置,不能使用成员修饰符,权限,静态不能用

```java
 class A{
     public void a(){
         class B{} //局部内部类
     }
 }
```

```java
 public class Outer {
     /**
      *  Inner类,是方法Outer的局部
      *  依然方法,才能被外界访问
      */
     public void outer(){
         class Inner{
             public void inner(){
                 System.out.println("局部内部类的方法!!");
             }
         }
         //方法,建立对象
         Inner inner = new Inner();
         inner.inner();
     }
 }
```

```java
 public static void main(String[] args) {
     //调用内部类的方法inner()
     //直接调用,不能调用
     Outer outer = new Outer();
     outer.outer();
 }
```

> 局部内部类,访问局部变量,变量必须final修饰

### **5.3 匿名内部类**

匿名内部类,就是没有名字的内部类,只能写在方法中,为了简化代码书写.

简化 : 实现类,实现接口,重写方法,创建对象. 或者是子类继承父类,重写方法,创建对象.代码上少内容.

- 匿名内部类使用的前提 :
  - `必须有接口实现`,或者是类的继承

  - 格式 :

```java
        new 接口或者父类(){
             //重写抽象方法
         };
         格式 == 实现类,实现接口,重写方法,创建对象
```


```java
 public interface MyInter {
     public abstract void inter();
     public abstract void inter2();
 }

 public class InnerClassTest {
     public static void main(String[] args) {
         //匿名内部类,简化书写,不写实现类
         //同时调用多个重写方法
         /*
          *  new MyInter(){}; 是接口实现类的匿名对象
          * 多态 : 接口 变量 = 实现类对象
          */
        MyInter my =  new MyInter(){
 
             @Override
             public void inter() {
                 System.out.println("实现类实现接口重写方法");
             }
 
             @Override
             public void inter2() {
                 System.out.println("实现类实现接口重写方法2222");
             }
         };
        my.inter();
        my.inter2();
     }
 }
```


## **6. 非法修饰符组合**

非法的修饰符的组合,主要说的是抽象abstract

- abstract和private就是非法组合,抽象方法要重写,private不能继承
- abstract和final就是非法组合,抽象方法要重写,final修饰不能重写
- abstract和static就是非法组合,静态方法类名直接调用

---
**永远相信美好的事情即将发生！**

**Yancey**
{{ date }}