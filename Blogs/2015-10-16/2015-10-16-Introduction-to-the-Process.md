#Introduction to the Process

##程序运行原理
从C语言最简单的例子`Hello, world`程序开始，从编辑完程序后保存到磁盘中，然后使用编译器编译程序，最后运行程序等来逐步深入理解程序的运行原理：

```
#include <stdio.h>

int main(void)
{
	printf("Hello, world\n");

	return 0;
}

```


###信息储存
使用编辑器编辑完程序之后，程序就会保存在磁盘中。那么具体它怎么保存的呢？众所周知，计算机在本质上只能保存0或1的bit(位)，但由于0或1的bit太多了，所有又将它们分组，于是将8个bit组成一个byte(字节)。由于一个byte有256种组合，足够表示英文中的大小写字母、数字和其他常用字符，[ASCII编码]()就产生了。


###编译系统

###程序运行
####硬件系统
* CPU(处理器)
* Memory(内存)
* Storage(存储设备)
* Networks(网络设备)
* Input/Output(输入/输出设备)

####指令周期

####操作系统
* Process(进程)：程序与进程区别，context切换，scheduling(调度)，protection(保护机制)
* I/O(输入/输出)：
* Loading(加载)：

##核心概念

###Process

###Dual Mode Operation

####User&Kernel模式
####保护机制
####模式切换
####Interrupt Vector


###Kernel启动



##参考资料
* [深入理解计算机系统](http://book.douban.com/subject/5333562/)
* [Operating Systems: Principles and Practice (2nd Edition)](http://ospp.cs.washington.edu)
* [Operating Systems Design and Implementation, 3/E](http://book.douban.com/subject/1764254/)