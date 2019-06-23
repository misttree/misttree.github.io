---
layout: post
title: "UML用例图"
date: 2019-03-12 09:00:00 +0800
categories: UML语言
tag: UML语言

---
* content
{:toc}
---

<!-- more -->

### 用例图的概念
- 用例图是指由参与者（Actor）、用例（Use Case），边界以及它们之间的关系构成的用于描述系统功能的视图。
- 用例图（User Case）是外部用户（被称为参与者）所能观察到的系统功能的模型图。
- 用例图是系统的蓝图
	- 用例图呈现了一些参与者，一些用例，以及它们之间的关系，主要用于对系统、子系统或类的功能行为进行建模

---

### 用例图的主要元素

---


#### 参与者（Actors）
- 角色与实际的人物可能存在有多种对应关系

---

#### 用例（Use-case）
- 用户与软件系统进行交互进行的一种总体上的描述
- 一个Actor使用软件系统时为了达到某种功能而进行的总体上的描述
- 不用去考虑细节与异常的信息，将软件系统的意图描述在用例图中

---

#### 子系统(Subsystem)
- 用来展示系统的一部分功能，这部分功能联系紧密
- 子系统的部分通常使用一个框图框在一起

![picture]({{ '/styles/images/uml/usecasediagram/001.png' | prepend: site.baseurl }})

---

### 用例之间也存在一定的关系

---

#### 关联(Association)
- 表示参与者与用例之间的通信，任何一方都可发送或接受消息

---

#### 泛化（Generalization）
- 就是通常理解的继承关系，子用例和父用例相似，但表现出更特别的行为
	- 用户（Actor）可以进行泛化的关系处理
- 子用例将继承父用例的所有结构、行为和关系
- 子用例可以使用父用例的一段行为，也可以重载它
- 父用例通常是抽象的

---

#### 特化（Specializatio）

---

#### 包含关系
- 包含关系用来把一个较复杂用例所表示的功能分解成较小的步骤
![picture]({{ '/styles/images/uml/usecasediagram/002.gif' | prepend: site.baseurl }})

---

#### 扩展关系
- 扩展关系是指用例功能的延伸，相当于为基础用例提供一个附加功能

![picture]({{ '/styles/images/uml/usecasediagram/003.gif' | prepend: site.baseurl }})

![picture]({{ '/styles/images/uml/usecasediagram/004.png' | prepend: site.baseurl }})

---
