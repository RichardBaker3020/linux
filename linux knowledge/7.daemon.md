daemon
======
daemon,  process
---
1. A **daemon** is a background, non-interactive program/processe. It is detached from the keyboard and display of any interactive user. The word daemon for denoting a background program is from the Unix culture; In Windows, daemons are called services.
2. **Process** is a running program. At a particular instant of time, it can be either running, sleeping, or zombie (completed process, but waiting for it's parent process to pick up the return value).
	> A process is one or more threads of execution together with their shared set of resources, the most important of which are the address space and open file descriptors. A process creates an environment for these threads of execution which looks like they have an entire machine all to themselves: it is a virtual machine.
	Inside a process, the resources of other processes, and of the kernel, are invisible and not directly accessible (at least not to a thread which is executing user-space code). For example, there is no way to refer to the open files of another process, or their memory space; it is as if those things do not even exist.


systemd daemon unit type
---


| type     | info                                                                |
| -------- | ------------------------------------------------------------------- |
| .service | 系统服务,包括服务器本身所需本机服务以及网络服务,最常见                                        |
| .target  | unit集合,执行multi-user.target就是执行一堆其他.service 或.socket 服务              |
| .timer   | 循环执行的服务                                                             |
| .socket  |                                                                     |
| .mount   |                                                                     |

### .service
to start a .service daemon on startup(you wanna run a script or a line of commmand when bootup), see vbird page 862.


### .timer 

*e.g. 固定周期运行 .tmer*

 1. add .timer file in /etc/systemd/system/

 * make backup.timer file:
```
[Unit]
Description=backup my server timer
[Timer]
OnBootSec=2hrs
OnUnitActiveSec=2days
[Install]
WantedBy=multi-user.target
```

2. enable .timer
```
[root@study ~]# systemctl daemon-reload
[root@study ~]# systemctl enable backup.timer
[root@study ~]# systemctl restart backup.timer
[root@study ~]# systemctl list-unit-files | grep backup
backup.service disabled # 这个不需要启动!只要 enable backup.timer 即可!
backup.timer enabled
```

3. check the execution time.
```
[root@study ~]# systemctl show timers.target
ConditionTimestamp=Thu 2015-08-13 14:31:11 CST # timers.target这个unit 启动的时间!

[root@study ~]# systemctl show backup.service
ExecMainExitTimestamp=Thu 2015-08-13 14:50:19 CST # backup.service 上次执行的时间

[root@study ~]# systemctl show backup.timer
NextElapseUSecMonotonic=2d 19min 11.540653s # 下一次执行距离 timers.target 的时间
```
> backup.timer纪录的下次执行时间,是the period from timers.target纪录的时间 up to next execution time, so 时间差 it shows is 2d 19min

daemon directory
---
* `/lib/systemd/system/` 每个服务最主要的启动脚本设置
* `/etc/systemd/system/` 系统执行过程中所产生的服务脚本,这些脚本的优先序要比 /lib/systemd/system/ 高!
* `/etc/systemd/system/` :管理员依据主机系统的需求所创建的执行脚本, 执行优先序又比 /run/systemd/system/ 高

> 系统开机会不会执行服务其实是看 /etc/systemd/system/ 下面的设置,所以该目录下面a bunch of链接文件。而实际执行的 systemd 启动脚本配置文件, 都是放置在 /lib/systemd/system/ ,如果想要修改某个服务启动的设置,要去 /lib/systemd/system/ 下面修改, /etc/systemd/system/ 仅是链接到正确的执行脚本配置文件而已。想要看执行脚本设置,应该要到 /lib/systemd/system/查阅

