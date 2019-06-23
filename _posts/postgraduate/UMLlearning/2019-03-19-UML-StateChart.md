---
layout: post
title: "UML状态图"
date: 2019-03-19 09:00:00 +0800
categories: UML
tag: UML状态图

---
* content
{:toc}
---

<!-- more -->

### 出现状态图的原因  
- 类图不能够完整的描述对于处于不同状态下的事件的处理
- 状态图即用于描述处于这种状态下的行为
- 类图描述静态下的行为
- 状态图描述动态下的事件与行为

---

### 状态图的描述

- 状态名
- 事件名
- 初始状态
- 终止状态

---

### 状态图的参数

---

#### Guard condition
- 使用一个中括号包含内容表示在该条件被满足时才会出现跳转

![picture]({{ '/styles/images/uml/statechart/001.png' | prepend: site.baseurl }})

---

#### Entry action
- 进入一个状态时所要执行的操作，添加在状态的内部
- 在状态图中添加横线进行标识
- 表示方式：entry/操作指令

---

#### Exit action
- 退出一个状态时所要执行的操作，添加在状态的内部
- 在状态图中添加横线进行标识
- 表示方式：exit/操作指令

![picture]({{ '/styles/images/uml/statechart/002.png' | prepend: site.baseurl }})

---

#### Action
- 一般会是以外界触发的动作
- 当发生状态跳转的时候，所执行的动作，即连接两个图之间的命令
- 原子性的动作，不会被中断，出现的格式为Action[Guard condition]的方式

---

#### Activity
- 位于一个状态时，系统不断执行的动作
- 可以被中断的
- 表示方式：do/操作

---

#### Completion transition
- 中断Activity时，所触发的动作
- 当处于Activity状态时，会有一个轮询的出口称之为Completion transition

![picture]({{ '/styles/images/uml/statechart/003.png' | prepend: site.baseurl }})

---

#### Internal transition
- 在一个状态的内部完成的跳转，不存在状态的退出与进入
- 重点：不会触发Entry与Exit的事件响应
- 有事件的响应并且存在执行的动作：如上图的event info/display time 

![picture]({{ '/styles/images/uml/statechart/004.png' | prepend: site.baseurl }})

---

#### Compsite states
- 复合状态：由若干个状态逻辑上形成的一个状态
- 复合状态中有一个状态是活动的，即可称符合状态是活动的
    - 物理上只能有一个状态是活动的，是某一个子状态处于活动状态
- 复合状态的初始状态
    - 执行一个Entry action
- 复合状态的终止状态
    - 一个事件如果不存在名字，则称之为Completion transition
    - 执行一个Exit action
- 从边界出现的跳转表示符合系统状态的每一种子状态，即针对于整个的复合状态执行的动作
- 引入Composite states可以使UML图变得更加简单
- 注：上图中将Closed与Open合并为NotPlaying

![picture]({{ '/styles/images/uml/statechart/005.png' | prepend: site.baseurl }})

---

#### History states
- 历史状态：一个状态在上一次跳出的状态
- 使用一个圆圈加H进行表示
- 系统从未进入复合状态时，会在History states处添加一个空线
    - 这时历史状态为空

![picture]({{ '/styles/images/uml/statechart/006.png' | prepend: site.baseurl }})

---

#### Action states
- 表示一种不会响应系统中的任何事件的状态，如下图的Idle状态
- 只会在内部执行do/activity，并不会在其他的部分进行处理

![picture]({{ '/styles/images/uml/statechart/007.png' | prepend: site.baseurl }})

---

### 状态图的实例
- 从具体简单到抽象复杂的设计

---

#### 地铁的售票机系统

![picture]({{ '/styles/images/uml/statechart/008.png' | prepend: site.baseurl }})

---

#### 考虑到是否实现放入硬币的方式

![picture]({{ '/styles/images/uml/statechart/009.png' | prepend: site.baseurl }})

---

#### 考虑设置计时系统方式Time Event事件
- 引入after事件
- 引入when事件

![picture]({{ '/styles/images/uml/statechart/010.png' | prepend: site.baseurl }})

---

#### 设置的结果

![picture]({{ '/styles/images/uml/statechart/011.png' | prepend: site.baseurl }})

---

#### 可以考虑的两项设计

![picture]({{ '/styles/images/uml/statechart/012.png' | prepend: site.baseurl }})

---

### 状态图的实现
建立一种事件的响应机制

#### 解决方案一
- 每当面临一个事件，进行一个多路选择，根据系统的当前状态进行处理（Switch）
- 缺点：
    - 当增加了一个状态时，所有的事件处理函数都需要修改
    - 软件设计没有做到局部化的处理

#### 解决方案二

![picture]({{ '/styles/images/uml/statechart/013.png' | prepend: site.baseurl }})

- 一个类对应有多个状态参与，所有状态对应同一个root类，而该root类与原本的类相联系
- 多个状态类中只有一个是活动的状态类，其他的不会在内存中保存
- 原本的类会将事件转化给那个root类，并由root类转换给当前的活动类，存在一个指针，指向那个活动的状态
- 状态的转换不能够再子类中完成，上升到root基类中完成，进而再次回传给原本的类，完成操作，CreationTool才具有转换状态的能力
- 从root类执行状态的转换调用
- 在软件设计中，各个类应当各司其职，避免肥胖性的类
- 每当新增一个类的时候仅需要添加一个对应的状态里就可以了，主要为编写新的类的事件处理函数
- 注：斜体表示为虚基类
