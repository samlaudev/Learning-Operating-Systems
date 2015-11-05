#Processes, Fork, I/O, Files

##Process
###PCB(Process Control Block)

###进程环境

###进程控制

###进程关系

###信号

##I/O

###文件I/O
####文件描述符
*文件描述符(file descriptor)*通常都是一个**非负整数**，内核使用它标识一个特定进程正在访问的文件。当打开一个已有文件或创建一个新文件时，它返回一个文件描述符，在读写文件的时候可以使用它。

一般来说，每当运行一个新程序，shell都会为新程序打开三个文件描述符：标准输入(standard input)、标准输入(standard output)和标准错误(standard error)，这个三个文件描述符都连接到**终端**。

###文件与目录

###标准I/O

##参考资料
* [Operating Systems: Principles and Practice (2nd Edition)](http://ospp.cs.washington.edu)
* [Operating Systems Design and Implementation, 3/E](http://book.douban.com/subject/1764254/)
* [UNIX环境高级编程](http://book.douban.com/subject/1788421/)