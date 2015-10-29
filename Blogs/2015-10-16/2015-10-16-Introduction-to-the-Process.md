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

![](https://raw.githubusercontent.com/samlaudev/Learning-Operating-Systems/master/Blogs/2015-10-16/Loading-Program.png)


####硬件系统
* __CPU(处理器)：__ 主要用来解释和执行存储在内存中的指令，它有很多寄存器来存储各种临时数据，其中有一个很重要的寄存器PC(Prorgram Counter)程序计数器，它总是指向执行指令的地址；而且它还有一个ALU(Arithmetic Logic Unit)算计逻辑单元来对数据进行运算。

* __Memory(内存)：__ 在CPU执行程序时，主要用来存储代码和数据。从物理上来看，内存是由DRAM(Dynamic Random-Access Memory)动态随机存取存储器组成；从逻辑上来看，它是一个线性的字节数组，每个字节都有唯一的地址(数组索引)。

* __Storage(存储设备)：__ 内存只能临时保存数据，一旦断电，数据就会消失。而硬盘这些存储设备能够用于长期存储数据，即使断电，数据也不会消失。

* __Networks(网络设备)：__ 如果没有网络，计算机只是一个孤立的个体，不能与其他计算机交流。如果有了网络之后，就能够与其他计算机系统相互发送和接收数据。

* __Input/Output(输入/输出设备)：__ 常用输入设备有键盘、鼠标等，输入设备有显示器。

####指令周期
CPU是如何逐条解释和执行加载到内存中的指令呢？过程如下：

1. 根据PC从内存中获取将要执行的指令
2. 解码
3. 执行(可能需要用到寄存器)
4. 将结果写回寄存器或内存
5. 更新PC(下一条指令)
6. 重复 

![](https://raw.githubusercontent.com/samlaudev/Learning-Operating-Systems/master/Blogs/2015-10-16/Instruction-Cycle.png)

####运行main程序
前面简单地描述系统的硬件组成和功能之后，我们正式解释在shell中执行以下命令行后

```
$ ./main
```
应用程序、操作系统以及硬件系统是具体如何工作：

1. 将存储在硬盘中的程序加载内存中
2. CPU执行内存中指令，这些指令将`Hello, world`字符串从内存复制到寄存器
3. 再将寄存器数据复制到显示设备，最终显示在屏幕上

##核心概念

###Process
####Process与Program的区别
* __Program:__ 编译器将源代码转化为一系列的机器指令后存储到一个文件，此时程序还没运行。
* __Process:__ 当程序加载到内存，然后CPU逐条解释和执行时，此时就变成进程。所以说进程只是程序运行中的一个实例。


####Thread
* __Process:__ 
* __Thread:__

###Dual Mode Operation
####User&Kernel模式
OS提供两种操作**硬件资源**的方式

* __Kernel mode(内核模式):__ 在内核模式中，处理器执行指令时无需检查权限
* __User mode(用户模式):__ 在用户模式中，处理器在执行指令之前，先检查指令是否被进程允许执行。有些指令或操作在用户模式中禁止执行。例如，不能修改分页表

####Prorection
**Protection**是操作系统的一个很重要的设计特性，它的主要作用是为了保护操作系统不受每个应用程序的影响。通过保护机制可以实现之前提及的目标：

* __可靠性(Reliability):__ 防止某个程序出现bug时不会导致另一个程序或操作系统会crash
* __安全性(Security):__ 限制进程可以做什么，不可以做什么
* __私隐(Privacy):__ 限制每个进程可以访问哪些数据，不能访问哪些数据
* __效率(Efficiency):__ 高效分配资源给每个进程，防止进程滥用资源

硬件需要提供什么才能允许操作系统保护自己不受其他应用程序影响呢？至少，硬件必须提供以下三样东西：

* __Privileged instructions(特权指令):__ 在用户模式执行所有潜在不安全的指令时，都会被禁止
* __Memory protection(内存保护):__ 在用户模式访问非法边界的内存空间时，都会被禁止
* __Timer interrupts(定时器中断):__ 不管进程做什么，内核都必须有一种方式从当前进程定期重新获取控制权。

####模式切换
一旦内核已经将用户进程放在一个精心构造的sanbox里面，下一个问题就是我们如何安全地从用户模式切换到内核模式，或反之？

* __User to kernel mode:__ 系统调用(System call)，中断(Interrupt)，异常(Exception)
* __Kernel to user mode:__ 创建进程(New process)，从系统调用、中断、异常中恢复(Resume after an exception, interrupt or system call)，切换到不同进程(Switch to a different process)，用户层向上调用(User-level upcall)

####Interrupt Vector
当中断、异常或系统调用发生时，操作系统根据不同的事件(除零异常、读取文件的系统调用或定时器中断)来做出不同的处理。那么处理器怎么知道运行哪段代码呢？

为了识别在上下文切换时运行的代码，有一个特殊的寄存器指向一段内核的内存区域叫*interrupt vector*。interrupt vector其实就是一个指针数组，每个元素都指向不同handler procedure的首地址。

因此，当中断、异常或系统调用发生时，硬件根据interrupt vector来选择对应的入口地址来调用handler procedure。

![](https://raw.githubusercontent.com/samlaudev/Learning-Operating-Systems/master/Blogs/2015-10-16/Interrupt-Vector.png)


##参考资料
* [深入理解计算机系统](http://book.douban.com/subject/5333562/)
* [Operating Systems: Principles and Practice (2nd Edition)](http://ospp.cs.washington.edu)
* [Operating Systems Design and Implementation, 3/E](http://book.douban.com/subject/1764254/)
* [廖雪峰Python教程 - 字符串和编码](http://www.liaoxuefeng.com/wiki/001374738125095c955c1e6d8bb493182103fac9270762a000/001386819196283586a37629844456ca7e5a7faa9b94ee8000)