# Operating Systems and Systems Programming
![](https://raw.githubusercontent.com/samlaudev/Learning-Operating-Systems/master/ScreenShots/Unix-History.png)


这个课程目的就是讲授操作系统的核心概念和设计，以及如何将它应用到其他高级系统中。其中涉及的主题包括操作系统的概念，系统编程，网络，分布式系统，存储系统，多进程(进程、进程间通信和同步)，内存分配(分段、分页)，资源分配和调度，文件系统，基本网络编程(sockets，分层，API，可靠性)，事务，安全和隐私。

我们将会使用[Pintos](https://cs162.eecs.berkeley.edu/projects/general/logistics/)来讲授操作系统的三个项目。

作业(个人任务)和项目(分组任务)将会提交到GitHub中。


#课程列表
具体的课程安排可以从[这里](https://cs162.eecs.berkeley.edu)查看，这里整理好所有的资料(讲义、扩展阅读、作业等)


1. [Intro to CS162](https://raw.githubusercontent.com/samlaudev/Learning-Operating-Systems/master/Handouts/PDF/Lecture%201-%20What%20is%20an%20Operating%20System.pdf) [[ppt](https://github.com/samlaudev/Learning-Operating-Systems/raw/a0262dc3370d4f0eb890b8c8b07a1e9857581dec/Handouts/PPT/Lecture%201-%20What%20is%20an%20Operating%20System.pptx)]
2. [Introduction to the Process](https://raw.githubusercontent.com/samlaudev/Learning-Operating-Systems/master/Handouts/PDF/Lecture%202-%20Introduction%20to%20Process.pdf) [[ppt](https://raw.githubusercontent.com/samlaudev/Learning-Operating-Systems/master/Handouts/PPT/Lecture%202-%20Introduction%20to%20Process.pptx)]
3. [Processes, Fork, I/O, Files](https://github.com/samlaudev/Learning-Operating-Systems/raw/master/Handouts/PDF/Lecture%203-%20Processes%2C%20Fork%2C%20I:O%2C%20Files.pdf)[[ppt](https://github.com/samlaudev/Learning-Operating-Systems/raw/master/Handouts/PPT/Lecture%203-%20Processes%2C%20Fork%2C%20I:O%2C%20Files.pptx)]
4. [I/O Continued, Sockets, Networking](https://github.com/samlaudev/Learning-Operating-Systems/raw/master/Handouts/PDF/Lecture%204-%20I:O%20Continued%2C%20Sockets%2C%20Networking.pdf)[[ppt](https://github.com/samlaudev/Learning-Operating-Systems/raw/master/Handouts/PPT/Lecture%204-%20I:O%20Continued%2C%20Sockets%2C%20Networking.pptx)]
5. [Concurrency: Processes and Threads](https://github.com/samlaudev/Learning-Operating-Systems/raw/master/Handouts/PDF/Lecture%205-%20Concurrency%20Processes%20and%20Threads.pdf)[[ppt](https://github.com/samlaudev/Learning-Operating-Systems/raw/master/Handouts/PPT/Lecture%205-%20Concurrency%20Processes%20and%20Threads.pptx)]
6. [Cooperating threads, Synchronization](https://github.com/samlaudev/Learning-Operating-Systems/raw/master/Handouts/PDF/Lecture%206-%20Cooperating%20threads%2C%20Synchronization.pdf)[[ppt](https://github.com/samlaudev/Learning-Operating-Systems/raw/master/Handouts/PPT/Lecture%206-%20Cooperating%20threads%2C%20Synchronization.pptx)]
7. [Mutual Exclusion, Lock Implementation](https://github.com/samlaudev/Learning-Operating-Systems/raw/master/Handouts/PDF/Lecture%207-%20Mutual%20Exclusion%2C%20Lock%20Implementation.pdf)[[ppt](https://github.com/samlaudev/Learning-Operating-Systems/raw/master/Handouts/PPT/Lecture%207-%20Mutual%20Exclusion%2C%20Lock%20Implementation.pptx)]
8. [Semaphores, Condition Variables, Readers/Writers](https://github.com/samlaudev/Learning-Operating-Systems/raw/master/Handouts/PDF/Lecture%208-%20Semaphores%2C%20Condition%20Variables%2C%20Readers:Writers.pdf)[[ppt](https://github.com/samlaudev/Learning-Operating-Systems/raw/master/Handouts/PPT/Lecture%208-%20Semaphores%2C%20Condition%20Variables%2C%20Readers:Writers.pptx)]
9. [Synchronization (Finish), Scheduling](https://github.com/samlaudev/Learning-Operating-Systems/raw/master/Handouts/PDF/Lecture%209-%20Synchronization%20(Finish)%2C%20Scheduling.pdf)[[ppt](https://github.com/samlaudev/Learning-Operating-Systems/raw/master/Handouts/PPT/Lecture%209-%20Synchronization%20(Finish)%2C%20Scheduling.pptx)]
10. [Advanced Scheduling, Deadlock](https://github.com/samlaudev/Learning-Operating-Systems/raw/master/Handouts/PDF/Lecture%2010-%20Advanced%20Scheduling%2C%20Deadlock.pdf)[[ppt](https://github.com/samlaudev/Learning-Operating-Systems/raw/master/Handouts/PPT/Lecture%2010-%20Advanced%20Scheduling%2C%20Deadlock.pptx)]
11. [Deadlock, Address Translation, Virtual Memory](https://github.com/samlaudev/Learning-Operating-Systems/raw/master/Handouts/PDF/Lecture%2011-%20Deadlock%2C%20Address%20Translation%2C%20Virtual%20Memory.pdf)[[ppt](https://github.com/samlaudev/Learning-Operating-Systems/raw/master/Handouts/PPT/Lecture%2011-%20Deadlock%2C%20Address%20Translation%2C%20Virtual%20Memory.pptx)]
12. [Address Translation, Caching](https://github.com/samlaudev/Learning-Operating-Systems/raw/master/Handouts/PDF/Lecture%2012-%20Address%20Translation%2C%20Caching.pdf)[[ppt](https://github.com/samlaudev/Learning-Operating-Systems/raw/master/Handouts/PPT/Lecture%2012-%20Address%20Translation%2C%20Caching.pptx)]
13. [Address Translation, Caching(Continue)](https://github.com/samlaudev/Learning-Operating-Systems/raw/master/Handouts/PDF/Lecture%2013-%20Address%20Translation%2C%20Caching%20Continue.pdf) [[ppt](https://github.com/samlaudev/Learning-Operating-Systems/raw/master/Handouts/PPT/Lecture%2013-%20Address%20Translation%2C%20Caching%20Continue.pptx)]
14. [Caching (finished), Demand Paging](https://github.com/samlaudev/Learning-Operating-Systems/raw/master/Handouts/PDF/Lecture%2014-%20Caching%2C%20Demand%20Paging.pdf)[[ppt](https://github.com/samlaudev/Learning-Operating-Systems/raw/master/Handouts/PPT/Lecture%2014-%20Caching%2C%20Demand%20Paging.pptx)]
15. [Input/Output, I/O Layers, Storage DevicesI/O Performance and Low-level Optimization](https://github.com/samlaudev/Learning-Operating-Systems/raw/master/Handouts/PDF/Lecture%2015-%20Input:Output%2C%20I:O%20Layers%2C%20Storage%20DevicesI:O%20Performance%20and%20Low-level%20Optimization.pdf)[[ppt](https://github.com/samlaudev/Learning-Operating-Systems/raw/master/Handouts/PPT/Lecture%2015-%20Input:Output%2C%20I:O%20Layers%2C%20Storage%20DevicesI:O%20Performance%20and%20Low-level%20Optimization.pptx)]
16. [Input/Output (con't)](https://github.com/samlaudev/Learning-Operating-Systems/raw/master/Handouts/PDF/Lecture%2016-%20Input:Output%20Continue.pdf)[[ppt](https://github.com/samlaudev/Learning-Operating-Systems/raw/master/Handouts/PPT/Lecture%2016-%20Input:Output%20Continue.pptx)]
17. [Performance, Storage Devices, Queueing theory](https://github.com/samlaudev/Learning-Operating-Systems/raw/master/Handouts/PDF/Lecture%2017-%20Performance%2C%20Storage%20Devices%2C%20Queueing%20theory.pdf)[[ppt](https://github.com/samlaudev/Learning-Operating-Systems/raw/master/Handouts/PPT/Lecture%2017-%20Performance%2C%20Storage%20Devices%2C%20Queueing%20theory.pptx)]
18. [File SystemsDesign: Concept to FAT, Advanced File Systems: FFS, NTFS, COW](https://github.com/samlaudev/Learning-Operating-Systems/raw/master/Handouts/PDF/Lecture%2018-%20File%20Systems%20Design-Concept%20to%20FAT%2C%20Advanced%20File%20Systems-FFS%2C%20NTFS%2C%20COW.pdf)[[ppt](https://github.com/samlaudev/Learning-Operating-Systems/raw/master/Handouts/PPT/Lecture%2018-%20File%20Systems%20Design-Concept%20to%20FAT%2C%20Advanced%20File%20Systems-FFS%2C%20NTFS%2C%20COW.pptx)]
19. [FileSystems (finished), MMAP](https://github.com/samlaudev/Learning-Operating-Systems/raw/master/Handouts/PDF/Lecture%2019-%20FileSystems%20(finished)%2C%20MMAP.pdf)[[ppt](https://github.com/samlaudev/Learning-Operating-Systems/raw/master/Handouts/PPT/Lecture%2019-%20FileSystems%20(finished)%2C%20MMAP.pptx)]

####视频链接：[UC Berkeley Computer Science 162 Fall 2015](https://www.youtube.com/watch?v=1IcZB26STUE&list=PLmJS5QR6Sdxy4XHQ5A__3irZvSQh1yI8V)



#学习笔记
1. [什么是操作系统？](https://github.com/samlaudev/Learning-Operating-Systems/blob/master/Blogs/2015-10-12/2015-10-12-What's-Operating-System.md)
2. [进程简介](https://github.com/samlaudev/Learning-Operating-Systems/blob/master/Blogs/2015-10-16/2015-10-16-Introduction-to-the-Process.md)
3. [进程，Fork，I/O，文件](https://github.com/samlaudev/Learning-Operating-Systems/blob/master/Blogs/2015-10-30/2015-10-30-Processes%2C%20Fork%2C%20I:O%2C%20Files.md)
4. [高级I/O，Sockets，Networking](https://github.com/samlaudev/Learning-Operating-Systems/blob/master/Blogs/2015-11-5/2015-11-5-I:O%20Continued%2C%20Sockets%2C%20Networking.md)

#基本工具
###vagrant & virtual box
###vim
作为一个程序员，一个常用的工具就是**编辑器**，我选择一个能极大提高自己开发效率的编辑器**vim**。[这里](http://derekwyatt.org/vim/tutorials/)有一系列的视频教程，也可以参考我的[Vim配置、插件和使用技巧](http://www.jianshu.com/p/a0b452f8f720)这篇文章。

###make
编写完程序之后，下一步就是编译程序。一般来说，如果程序规模不大的话，在终端中使用简单命令行编译即可。但随着程序规模越来越大，就需要自动化编译和构建工具[make](https://en.wikipedia.org/wiki/Make_(software))，make通过读取`Makefile`的编译规则来编译程序和函数库。具体用法可以参考这篇文章[A tutorial by example](http://mrbook.org/blog/?s=make)。更深入的用法可以参考[GNU make](http://www.gnu.org/software/make/manual/make.html)

###gdb
当你运行程序后，发现与自己预想的结果不对，这时你需要调试工具[gdb](https://sourceware.org/gdb/)。gdb是[GNU Project](https://en.wikipedia.org/wiki/GNU)开发的调试器，它能够在程序中设置断点，启动程序后运行到断点之后停止运行，然后查看各个变量的值。要想学习如何使用，可以参考陈皓的[用GDB调试程序](http://blog.csdn.net/haoel/article/category/9197)系列文章，想深入学习的话，可以查阅官方的[Debugging with gdb](https://sourceware.org/gdb/current/onlinedocs/gdb/)

###valgrind
[valgrind](http://www.valgrind.org)是一个用于内存调试、内存泄露检查以及性能分析工具。它的子工具Memcheck能够检查到以下内存问题：
* 使用未初始化的内存
* 使用已经释放了的内存
* 使用超过malloc分配的内存空间
* 对堆栈的非法访问
* 申请的空间是否有释放
* 不匹配使用malloc/free/new/delete等方法来申请和释放内存
* 重复free

官方提供一个入门教程[The Valgrind Quick Start Guide](http://www.valgrind.org/docs/manual/QuickStart.html)和深入学习的[Valgrind User Manual](http://www.valgrind.org/docs/manual/manual.html)参考手册。

###git
[git](http://www.git-scm.com)是一个开源分布式版本控制工具，它能够跟踪所有提交数据的历史记录，方便你回溯到任何历史版本来查看和修改。不仅如此，它还能够让不同的团队成员协同完成一项任务。关于如何使用git官方已经有详细讲解，如果想了解git的工作流以及多个人如何协作，可以参考[Git版本控制与工作流](http://www.jianshu.com/p/67afe711c731)


#项目
