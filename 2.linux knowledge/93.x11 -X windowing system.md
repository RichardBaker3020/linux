x11 -X windowing system
========================

*X11 is a network protocol designed for Unix and similar operating systems to enable remote graphical access to applications*. 

A machine running an X windowing system can *launch a program on a remote computer*. All the CPU processing happens on the remote computer but the display of the application appears on the local machine.

For a time it was popular to have dedicated "X terminals". Similar to a character cell terminal these terminals had no "brains" except for what was needed to operate their X windowing system. Such terminals started to disappear as personal desktop computers became popular, more powerful, and inexpensive enough to run an X windowing system on top of the installed OS (or to have the applications ported to run locally on the personal computer). Interestingly, today the popularity of similar terminals is slowly picking up again as large businesses realize the need for easily maintainable, interchangeable "thin clients".

Although X terminals really did not catch on, the X windowing system did *become the standard graphical system for graphical programs running in Unix and Linux environments.* These systems use the X11 protocol to draw graphics to their local video display. The local display is treated as a remote display that just happens to be on the same machine.


X能为GUI环境提供基本的框架：在屏幕上描绘、呈现图像与移动程序窗口，同时也受理、运行、及管理电脑与鼠标、键盘的交互程序。

X采用Clinet/Server的架构模型(*X中所提及的“客户端”和“服务器”等字眼用词也经常与人们一般想定的相反，“服务器”反而是在用户本地端的自有机器上运行，而非是在远程的另一部机器上运行。*)，由一个X服务器与多个X客户端程序进行通讯，服务器接受对于图形输出（窗口）的请求并反馈用户输入（键盘、鼠标、触摸屏），服务器可能是一个能显示到其他显示系统的应用程序，也可能是控制某个PC的视频输出的系统程序，也可能是个特殊硬件。

X的一大特点在于“网络透明性”：应用程序（“客户端”应用程序）所运行的机器，不一定是用户本地的机器（显示的“服务器”）。


swtich between x and testmode
---
`[Ctrl] + [Alt] + [F2] ~[F6] ` :命令行登陆 tty2  tty6 终端机; 

`[Ctrl] + [Alt] + [F1]` :图形接口桌面。

当开机完成之后,默认系统只会提供给你一个 tty 而已, tty2~tty6 其实一开始是不存在的, 要切换时 (按下 [ctrl]+[alt]+[F2]),系统才产生出额外的 tty2, tty3... 

若你在纯文本环境中启动 X 窗口,那么图形界面就会出现在当时的那个 tty 上面。举例来说,你在 tty3 登陆系统,然后输入 `startx` 启动个人的图形界面, 那么这个图形界面就会产生在 

要让startx生效至少需要下面这几件事情的配合: 并没有其他的 X window 被启用; 你必须要已经安装了X Window system 

without X
---
To boot Ubuntu 16.04 Desktop without X and make this the default, use: 
`sudo systemctl set-default multi-user.target `


To return to default booting into X, use :
`sudo systemctl set-default graphical.target `

To see the current default target:
`sudo systemctl get-default `