---
layout: post
title: "UML顺序图"
date: 2019-03-12 09:00:00 +0800
categories: UML
tag: UML顺序图

---
* content
{:toc}
---
### 顺序图的概念
- 顺序图（Sequence Diagram）是显示对象之间交互的图，这些对象是按时间顺序排列的
- 用于描述对象之间的协作关系情况，与用例图不同，顺序图的设计与软件设计存在一定的关系
- 顺序图中显示的是参与交互的对象及其对象之间消息交互的顺序

### 顺序图的主要元素
<!-- more -->
- 对象（Actor）
- 生命线（Lifeline）
	- 虚线表示对象未被创建
	- 使用白色的框线来进行表示
- 控制焦点（Focus of control）
- 消息（Message）
    - 使用带箭头的线表示消息的传递情况



### 顺序图的时间线
- 表示时间的流逝过程
- 消息的发送表示为两个对象之间在生命线的联系
- 选中一个对象的顺序图

![picture]({{ '/styles/images/uml/sequancediagram/001.png' | prepend: site.baseurl }})

### 删除一个对象的顺序图
- 在生命线上标注X即可

![picture]({{ '/styles/images/uml/sequancediagram/002.png' | prepend: site.baseurl }})

### 移动一个对象的顺序图

![picture]({{ '/styles/images/uml/sequancediagram/003.png' | prepend: site.baseurl }})
- 与用例图存在extension的关系

### 条件消息

![picture]({{ '/styles/images/uml/sequancediagram/004.png' | prepend: site.baseurl }})

- 使用一个中括号进行标识，仅当内部的条件成立时，发送消息
- 当参与对象较多，设计关系复杂时，引入顺序图会变得很复杂
- 顺序图中用户可以对于自身进行泛化的处理

![picture]({{ '/styles/images/uml/sequancediagram/005.png' | prepend: site.baseurl }})

- 并且用户也可以进行泛化的处理

### 异步的消息与多线程的处理方式
- 使用半箭头的方式进行表示
- 发送方不会去等待消息的执行结束，而是使用异步的方式进行处理

![picture]({{ '/styles/images/uml/sequancediagram/005.png' | prepend: site.baseurl }})
