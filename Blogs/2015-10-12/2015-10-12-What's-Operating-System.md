#What's Operating System?
![纪念C语言和Unix的创造者 -- Dennis Ritchie](https://raw.githubusercontent.com/samlaudev/Learning-Operating-Systems/master/Blogs/2015-10-12/Dennis-Ritchie.jpg)

不知不觉，[Dennis Ritchie](https://en.wikipedia.org/wiki/Dennis_Ritchie)已经离开我们4周年了，他是创造[C语言](https://en.wikipedia.org/wiki/C_(programming_language))和[Unix](https://en.wikipedia.org/wiki/Unix)操作系统，如果没有他，就不会有我们现在所熟知的现代计算。不可否认，Steve Jobs带来很多我们从未见过、具有创新和革命性的产品。但是苹果和Steve Jobs所创造的标志性产品一部分都要归功于Dennis Ritchie。在此纪念一下他，现在正式开始进入操作系统学习的正文。


在弄清楚什么是操作系统之前，我们有必要思考一下，**为什么要学习操作系统**？一般都基于以下原因：

* 有时你需要设计和构建操作系统或它的其中一个组件。
* 很多时候你构建其他系统时需要利用到操作系统的核心概念，有些概念和设计模式可以应用到很多方面。
* 所有人在构建应用程序时都是利用基于操作系统提供的API，只有你更好地理解它的设计和实现，才能更好地利用它。

通过学习本课程能掌握一下内容：

* OS的核心概念(进程、虚拟内存、I/O、网络)：如何进行系统编程
* 并发：线程、调度、锁、死锁、扩展性、公平性
* 地址空间：虚拟内存、地址转换、保护、共享
* 文件系统：I/O设备、文件、存储、命名、缓存、性能、分页、转换、数据库
* 分布式系统：协议、N-Tiers、RPC、NFS、DHTs、一致性、伸缩性、组播
* 可靠性&安全性：容错、保护、安全
* 云设施

##什么是操作系统？
![](https://raw.githubusercontent.com/samlaudev/Learning-Operating-Systems/master/Blogs/2015-10-12/OS-Role.png)

从**不同的角度**来看待同一样事物一般都会有不同的看法，下面我们从裁判、魔术师和胶水三个角度来看操作系统：

* __裁判(Isolation & Protection)：__ 裁判的作用就是根据`规则`界定场上的运动员有没有做出违反规则的动作，操作系统能够管理好共享资源，以防程序员编写出来的程序随意访问其他程序占用的资源(CPU、内存、磁盘空间)和随意分配和滥用资源，导致资源过快耗尽。
* __魔术师(Abstraction)：__ 提供一种简洁、易用的API来操作物理资源。没有操作系统之前，程序员需要了解硬件结构组成和工作原理才能正确地操作硬件，有了操作系统之后，程序员无需知道它内部的实现原理，只需正确地调用接口就能返回对应的结果。很多人就会感叹，这就好像魔术师施展了魔术一样神奇。
* __胶水(Common Services)：__ 操作系统提供一些基本服务(存储、窗口系统、网络、共享、授权等)，操作系统像胶水一样将它们粘在一起，构成一个强大的系统。


##系统的挑战：复杂性
###硬件复杂性
组成每台计算机的核心组件(CPU、内存、磁盘、SSD、键盘、显示器、网络环境)可能都__不同__：

* 不同类型的CPU：Pentium, PowerPC, ColdFire, ARM, MIPS
* 不同容量的内存、磁盘
* 不同类型的I/O设备：鼠标、键盘、传感器、摄像头、指纹读取器
* 不同的网络环境：电缆、DSL、无线、防火墙

针对以上硬件的复杂性，我们思考以下问题：

* 是否每个程序需要修改以便能够运行在不同的硬件？
* 一个错误程序会令整个系统崩溃吗？
* 是否每个程序能够访问所有的硬件设备？

###如何应对复杂性
为了应对硬件的复杂性，我们在硬件和应用程序之间引入一层__Virtual Machine Abstraction__来管理硬件资源和提供易用API给程序员编程。

![](https://raw.githubusercontent.com/samlaudev/Learning-Operating-Systems/master/Blogs/2015-10-12/Virtual-Machine-Abstraction.png)

####Virtual Machine
虚拟机有两种分类：

* __进程VM：__ 支持**单个程序**的执行。
* __系统VM：__ 支持**整个系统和应用程序**的执行。

![](https://raw.githubusercontent.com/samlaudev/Learning-Operating-Systems/master/Blogs/2015-10-12/Virtual-Machine.png)

__进程VM__具有以下特点：

* __易于编程：__ 每个进程都独立使用CPU、内存和访问其他硬件设备，并且每种不同的设备都可以使用相同层次的API来操作。
* __错误隔离：__ 每个进程不能直接影响其他进程，即使出现一些bugs都不会导致整个系统崩溃。
* __移植性：__ Java接口能够在多个平台使用。

__系统VM__有利于OS的开发：

* 当OS崩溃时，限制在一个VM
* 有助于在其他OSs测试程序

![](https://raw.githubusercontent.com/samlaudev/Learning-Operating-Systems/master/Blogs/2015-10-12/System-Virtual-Machine.png)


####Address Translation
* __地址空间：__ 就是一组内存地址，每个用户程序和kernel(内核)都有独立的地址空间。
* __地址转换：__ 通过MMU(Memory Management Unit)硬件映射将CPU的虚拟地址转换为内存的物理地址。

![](https://raw.githubusercontent.com/samlaudev/Learning-Operating-Systems/master/Blogs/2015-10-12/Address-Translation.png)

Address Translation**详情**如下：

* 地址转换借助__Page Table__完成
![](https://raw.githubusercontent.com/samlaudev/Learning-Operating-Systems/master/Blogs/2015-10-12/Address-Translation-Details.png)

* 地址转换有利于__控制转换和访问__
	

####Dual Mode Operation
OS提供两种操作**硬件**的方式：

* __Kernel mode(内核模式)：__ 也称为supervisor或protected模式
* __User mode(用户模式)：__ 普通程序执行模式，有些指令或操作在用户模式中禁止执行。例如，不能修改分页表

要想从用户模式切换到内核模式，可以通过以下几种方式：

* System Call(系统调用)
* Interrupts(中断)
* Other Exceptions(异常)

![](https://raw.githubusercontent.com/samlaudev/Learning-Operating-Systems/master/Blogs/2015-10-12/Mode-Transition.png)

##结论
* 操作系统提供一个virtual machine abstraction来处理各种各样的硬件
* 操作系统协调资源和防止用户之间相互访问资源
* 操作系统通过提供易于使用API来简化编程
* 操作系统提供一系列的fault tolerance和fault recovery措施。