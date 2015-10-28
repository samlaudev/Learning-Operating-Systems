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
由于`main.c`只是供程序员阅读的源代码，而计算机只能解释和执行0和1的字节序列，所以我们需要使用[编译器](https://en.wikipedia.org/wiki/Compiler)来将`main.c`源文件转化为可执行目标文件，这里我使用的是[gcc](https://en.wikipedia.org/wiki/GNU_Compiler_Collection)编译器：

```
$ gcc -o main main.c
```

编译完之后，就会产生一个可执行目标文件`main`。其实编译过程是经历以下**四个阶段：**

* __预处理阶段:__ 预处理器根据以字符`#`开头的指令修改C的源程序。例如，`main.c`程序第一行有预处理指令`#include <stdio.h>`，那么预处理器将读取头文件`stdio.h`的内容，然后插入到`main.c`源程序中，得到一个以`.i`为后缀的`main.i`文件。

* __编译阶段:__ 编译器将`main.i`文件翻译成`main.s`文件，里面内容都是存放汇编语言指令。
* __汇编阶段:__ 汇编器将`main.s`文件翻译成机器语言指令，把这些指令打包成一种叫可重定位目标程序(relocatable object program)格式，并将结果保存在`main.c`文件。
* __链接阶段:__ 由于`main.c`文件引用一个标准库的函数`printf`，这个`printf`函数存放在一个单独预编译好的`printf.o`文件中，因此，需要借助链接器以某种方式合并到`main.o`文件中，最后生成一个可执行目标文件(简称为可执行文件)`main`。

###程序运行
`main.c`源文件经过gcc编译器生成可执行文件`main`后，可以使用[unix shell](https://en.wikipedia.org/wiki/Unix_shell)来运行程序

```
$ ./main
Hello, world
```
虽然运行程序只需在shell敲入简单的命令行即可，实际上它是一个非常复杂的过程，它涉及到硬件设备、操作系统和应用程序之间的复杂交互。

####硬件系统
* __CPU(处理器)：__ 主要用来解释和执行存储在内存中的指令，它有很多寄存器来存储各种临时数据，其中有一个很重要的寄存器PC(Prorgram Counter)程序计数器，它总是指向执行指令的地址；而且它还有一个ALU(Arithmetic Logic Unit)算计逻辑单元来对数据进行运算。
* __Memory(内存)：__
* __Storage(存储设备)：__
* __Networks(网络设备)：__
* __Input/Output(输入/输出设备)：__

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