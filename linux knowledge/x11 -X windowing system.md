x11 -X windowing system
========================

*X11 is a network protocol designed for Unix and similar operating systems to enable remote graphical access to applications*. 

A machine running an X windowing system can *launch a program on a remote computer*. All the CPU processing happens on the remote computer but the display of the application appears on the local machine.

For a time it was popular to have dedicated "X terminals". Similar to a character cell terminal these terminals had no "brains" except for what was needed to operate their X windowing system. Such terminals started to disappear as personal desktop computers became popular, more powerful, and inexpensive enough to run an X windowing system on top of the installed OS (or to have the applications ported to run locally on the personal computer). Interestingly, today the popularity of similar terminals is slowly picking up again as large businesses realize the need for easily maintainable, interchangeable "thin clients".

Although X terminals really did not catch on, the X windowing system did *become the standard graphical system for graphical programs running in Unix and Linux environments.* These systems use the X11 protocol to draw graphics to their local video display. The local display is treated as a remote display that just happens to be on the same machine.


X能为GUI环境提供基本的框架：在屏幕上描绘、呈现图像与移动程序窗口，同时也受理、运行、及管理电脑与鼠标、键盘的交互程序。

X采用Clinet/Server的架构模型(*X中所提及的“客户端”和“服务器”等字眼用词也经常与人们一般想定的相反，“服务器”反而是在用户本地端的自有机器上运行，而非是在远程的另一部机器上运行。*)，由一个X服务器与多个X客户端程序进行通讯，服务器接受对于图形输出（窗口）的请求并反馈用户输入（键盘、鼠标、触摸屏），服务器可能是一个能显示到其他显示系统的应用程序，也可能是控制某个PC的视频输出的系统程序，也可能是个特殊硬件。

X的一大特点在于“网络透明性”：应用程序（“客户端”应用程序）所运行的机器，不一定是用户本地的机器（显示的“服务器”）。

在图例中，X服务器从键盘、鼠标端获取输入信息，之后将输入反馈显示于银幕，而网页浏览器及终端模拟器则在客户端的本机系统上运行。此外客户端也通过网络与远程的机器、服务器保持联系，以保消息状态的更新。如此的机制及架构能使远程运行的软件如同在本机端运行一样。

服务器和客户端之间的通信协议的运作对计算机网络是透明的：客户端和服务器可以在同一台计算机上，也可以不是，或许其架构和操作系统也不同，但都能运行。客户机和服务器还能够使用安全连接在互联网上安全地通讯。

为了使远端客户程序显示到本地服务器，用户一般需要启动一个终端窗口和到达远端计算机的telnet或者ssh，令其显示到用户计算机，然后启动客户端。然后客户端就会连接到本地计算机，并且远端应用程序会显示到本地屏幕并被本地输入设备所控制。

实际的远端客户端的例子有：图形化管理远程计算机；在远端UNIX计算机上运行计算密集的仿真程序并把结果显示到本地的Windows桌面计算机；用一套显示器、键盘和鼠标控制同时运行在多台计算机上的图形化软件。