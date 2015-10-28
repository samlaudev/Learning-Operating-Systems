#Introduction to the Process
![](https://raw.githubusercontent.com/samlaudev/Learning-Operating-Systems/master/Blogs/2015-10-16/Loading-Program.png)



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
使用编辑器编辑完程序之后，程序就会保存在磁盘中。那么具体它怎么保存的呢？众所周知，计算机在本质上只能保存0或1的bit(位)，但由于0或1的bit太多了，所有又将它们分组，于是将8个bit组成一个byte(字节)，而每个字节表示程序中的某个字符。

由于一个byte有256种组合，足够表示英文中的大小写字母、数字和其他常用字符，[ASCII编码](https://en.wikipedia.org/wiki/ASCII)就产生了，那么就可以使用ACSII编码来表示英文或数字了。`main.c`程序以字节序列的方式存储在文件中，每个字节都是一个整数，每个整数都对应某个字符。例如，第一个字符`#`对应的整数是35，第二个字符`i`对应的整数是105，以此类推。

像`main.c`由ACSII字符构成的文件成为__文本文件__，其他文件称为__二进制文件__。

![](https://raw.githubusercontent.com/samlaudev/Learning-Operating-Systems/master/Blogs/2015-10-16/ASCII-Code-Chart-Quick-ref-card.png)

> __延伸一下：__ 系统中所有的信息，包括磁盘文件、存储器中的程序或数据和网络传送上的数据都是由0和1组成的字节序列，至于如何区分这些数据对象，是根据我们读到这些数据对象的**上下文(context)**。


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
* [廖雪峰Python教程 - 字符串和编码](http://www.liaoxuefeng.com/wiki/001374738125095c955c1e6d8bb493182103fac9270762a000/001386819196283586a37629844456ca7e5a7faa9b94ee8000)