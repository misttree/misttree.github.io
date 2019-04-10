---
layout: post
title: "UML类图"
date: 2019-03-07 09:00:00 +0800
categories: UML
tag: UML类图

---
* content
{:toc}
---
### 类图的概念
- UML图本身较为简洁，内部蕴含较深刻的含义

---

### 类图的绘制
- UML中使用斜体来表示一种抽象类
- 在UML的成员属性设置中其中成员前面的 +为属性为Public； -为属性Private； #为属性protect

![picture]({{ '/styles/images/uml/classdiagram/007.png' | prepend: site.baseurl }})

- 解释
	- position：由若干个元素组成的，并且为私有成员不可访问
	- contains（Point）：Boolean
<!-- more -->
		- 类内部的成员函数，接收的参数成员为Point类型
		- 返回值为Boolean类型，用于判断给定的点是否为与该图形的内部
- 绘制UML图
	- 在设计阶段完成的事情，而不是在编码阶段完成的事情
		- 无需详细考虑每一个部分的设计细节
	- 没有必要给出类的全部的详细信息，给出类的所有成员
	- 数据成员可以在设计之初不罗列出来，只给出成员函数
	- 可以在开始时，只给出设计的数据成员的名字

![picture]({{ '/styles/images/uml/classdiagram/008.png' | prepend: site.baseurl }})

- 一个详细的UML设计图
- 0..1以及0..n这种使用的方式
- 在UML模式图中，要考虑位于连接线的上方的文字的位置
- 在完成软件之前已经完成了对于软件的设计

---

### 类图的关系
- 两个类之间可能存在有多种关系，但是两个对象之间只能有一种关系
- 类图中的关系可以分为以下几部分

![picture]({{ '/styles/images/uml/classdiagram/029.PNG' | prepend: site.baseurl }})

---

#### 依赖关系
- 类之间的关系中最为简单的即为依赖关系
- 依赖(Dependency)关系是类与类之间的联接，依赖关系表示一个类依赖于另一个类的定义
- 并且依赖关系在UML图中使用虚线+箭头的方式进行表示
- 在依赖关系的左右添加数字可以用于标识两个类对应的个数关系

![picture]({{ '/styles/images/uml/classdiagram/030.gif' | prepend: site.baseurl }})

---

#### 关联关系

![picture]({{ '/styles/images/uml/classdiagram/001.png' | prepend: site.baseurl }})

- 表示一种两个类的内部存在某种函数调用的对应关系
	- 关联暗示了依赖，二者都用来表示无法用聚合和组合表示的关系
	- 如果两边都不存在有箭头的话，则可以表示是一种双向的依赖关系
	- 在关联关系的左右添加数字可以用于标识两个类对应的个数关系

![picture]({{ '/styles/images/uml/classdiagram/002.png' | prepend: site.baseurl }})

- 解释
	- 一个DiagramEditor可能会对应多个Diagram
	- 任意时刻仅存在一个Diagram活动中（curent）


---

#### 继承关系
继承可以分为两种分别对应实现，泛化  
- 实现：对于虚基类的继承abstract class的继承，使用三角箭头加虚线的方式进行处理
- 泛化：对于实类的继承，使用三角箭头加实线的方式进行处理
    - 是一种继承关系，表示一般与特殊的关系，它指定了子类如何特化父类的所有特征和行为,如下图所示  

![picture]({{ '/styles/images/uml/classdiagram/003.png' | prepend: site.baseurl }})

- 对于上图的继承关系做一定的修改，得到一种更为直接的方式：类的继承  

![picture]({{ '/styles/images/uml/classdiagram/004.png' | prepend: site.baseurl }})

- 再进一步得到拓展得到的结果  

![picture]({{ '/styles/images/uml/classdiagram/005.png' | prepend: site.baseurl }})

- 类之间存在一些共同的关系，使用一个基类Element对于其进行描述 

---


#### 聚合关系（Aggregation）
- 定义：是整体与部分的关系，且部分不可以离开整体而单独存在，且部分的生命周期与整体相同
- 聚合关系是关联关系的一种，是强的关联关系
- 关联和聚合在语法上无法区分，必须考察具体的逻辑关系

![picture]({{ '/styles/images/uml/classdiagram/015.png' | prepend: site.baseurl }})

- 标识一个类于其他类之间的包含关系（使用一个空心的菱形来标识，指向聚合的本体）

- 聚合关系限制的属性
	- **反自身**：
		- 给定一个对象，该对象不能够与自身存在关系（不是类）
	- **推导关系**：
		- A是B的一部分，B是C的一部分，所以，A是C的一部分
-合理的判断是否满足之前的两种性质，即可以判断是否为聚合关系

---

#### 组合关系 Composition
- 定义：是整体与部分的关系，且部分不能够离开整体而单独存在，组合中部分的生命周期与整体的生命周期不相同

- 组合关系不同于聚合关系
	- 使用实心菱形来进行表示，并且指向组合方

![picture]({{ '/styles/images/uml/classdiagram/016.png' | prepend: site.baseurl }})

---

### 类图的其他概念

#### 类内部的关系
- 用于描述针对于类的内部的存在的一种关系

![picture]({{ '/styles/images/uml/classdiagram/017.png' | prepend: site.baseurl }})

- 跳出连接的方式，进行处理

![picture]({{ '/styles/images/uml/classdiagram/018.png' | prepend: site.baseurl }})

---

#### 实例化关系
- 用于表示两个类之间存在某种实例化的关系

![picture]({{ '/styles/images/uml/classdiagram/006.png' | prepend: site.baseurl }})

- RectangleTool的对象可以用于创建Rectangle的对象
- UML中的双尖括号：表示一种实例化的关联关系

---

#### 类的多元性关系
- *表示0个或多个
- 在类图边缘写1表示类周边仅存在1个对象（Singleton）
- 存在static关键字的属性加下划线（Class Scope）

![picture]({{ '/styles/images/uml/classdiagram/009.png' | prepend: site.baseurl }})

- 而普通的属性为（Object Scope）
- Object identify
	- 能够唯一标识一个对象的属性成员

---

#### 类之间的关系

![picture]({{ '/styles/images/uml/classdiagram/010.png' | prepend: site.baseurl }})

- employee/employer代表扮演的角色
- 使用+加上扮演的角色名进行使用
- 在两个类之间的连接上添加内容表示两个类之间的关系

---

#### 类自身之间存在一定的关联关系
- 即类可以与自身之间存在一定的关系

![picture]({{ '/styles/images/uml/classdiagram/011.png' | prepend: site.baseurl }})

---

#### 类之间关联关系的约定
- 两个对象之间仅能够存在有一个关联关系的（下图是错误的示范）
	- 但并不是指两个类之间仅能存在有一个关联关系
	- 两个类之间可以存在有多个关系

![picture]({{ '/styles/images/uml/classdiagram/012.png' | prepend: site.baseurl }})

- 可以对于这种关系进行一定的修改，变为如下格式

![picture]({{ '/styles/images/uml/classdiagram/013.png' | prepend: site.baseurl }})

- 对于关联关系的一种限制，一个Customer仅能够拥有一个CurrentAccount一个Customer可以拥有多个Account但是只能够拥有0或1个CurrentAccount

![picture]({{ '/styles/images/uml/classdiagram/014.png' | prepend: site.baseurl }})

---

#### 关系类（Association Class）
- 用于在描述一种关联关系的时候，使用一个类来进行处理
- 面向对象的原则：每一个类都应当各司其职
- 创建较多的类来描述其中存在的关系的属性

![picture]({{ '/styles/images/uml/classdiagram/019.png' | prepend: site.baseurl }})

---

#### 限制性的关联（Qualified association）
- 在关联端紧靠源类图标处可以有限定符（qualifier）
- 带有限定符的关联称为限定关联（qualified association）
- 说明：
	- 限定符是关联的属性
	- 限定符的作用是，给定关联一端的一个对象和限定值，可确定另一端的一个对象或对象集

![picture]({{ '/styles/images/uml/classdiagram/020.png' | prepend: site.baseurl }})

- Directory类中通过name关键字唯一的确定一个File对象

![picture]({{ '/styles/images/uml/classdiagram/021.png' | prepend: site.baseurl }})

- University通过id来唯一的标识Student对象，确立了一种映射关系

---

#### 多继承（Multiple inherited in UML）
- 多继承：一个类会继承自多个父类的情况

---

#### 掺和类（Mixin class）
- 一般在考虑针对于一个类设置多种功能时使用
	- Mixin有利于代码复用又避免了多继承的复杂
	- 使用Mixin享有单一继承的单纯性和多重继承的共有性
	- 接口与mixin相同的地方是都可以多继承，不同的地方在于 mixin 是带实现的
	- Mixin也可以看作是带实现的interface
	- 这种设计模式实现了依赖反转原则
- 使用多继承来实现设计中的目标，Mixin类通常作为功能模块使用，在需要该功能时“混入”

![picture]({{ '/styles/images/uml/classdiagram/022.png' | prepend: site.baseurl }})

- 将Mixin Class以附加功能的方式进行处理
- 并采用多继承的方式进行处理，实现某一种功能的添加

![picture]({{ '/styles/images/uml/classdiagram/023.png' | prepend: site.baseurl }})

---

#### 辨别者（Discriminators）
- 通过依据某种分类的标准，将某一种类分为多个不同的子类

![picture]({{ '/styles/images/uml/classdiagram/024.png' | prepend: site.baseurl }})

- 关联关系的实现（Implementation association）
	- 单向连接（Uni-directional links）
		- 两个类的对象呈现单一的可抵达性，仅能够从一个对象的指针访问另一个对象
		- 较为简单，但是不利于后期向双向连接的转换的过程中维护一致性
	- 双向连接（Bi-directional links）
		- 两个类的对象可以呈现互相的访问形式
		- 软件演化过程中需要一直考虑关联关系的一致性
- mutable/inmutable的指向性（双向的关系）

![picture]({{ '/styles/images/uml/classdiagram/025.png' | prepend: site.baseurl }})

- 注：
	- DebitCard对象的创建必须存在有一个Account对象
	- Account对象能够关联一个或零个DebitCard对象
- mutable 易变的
	- 在一个对象的生存周期中可以对应一个对象也可以不存在该对应的对象
	- 一段时间内对应一个其他对象，但是可以删除后可以再指向其他的对象
- immutable
	- 在该对象的生存周期中仅能够存在有一个有关系的对象
	- 且一定存在有一个有关系的对象
- 双向的immutable关系

---

#### 关联关系的实现（Implementation of association class）

![picture]({{ '/styles/images/uml/classdiagram/026.png' | prepend: site.baseurl }})

- 在语言的实际创建过程中，采用Registration位于中间部分的方式进行处理

![picture]({{ '/styles/images/uml/classdiagram/027.png' | prepend: site.baseurl }})

- 一个创建的相关的实例

![picture]({{ '/styles/images/uml/classdiagram/028.png' | prepend: site.baseurl }})

---
