 terminal command
====
**more**
---
`more 按页显示文件内容，空格翻页 b回到第一页`


**cat** 
---
```
cat 文件 查看文件内容 

cat > 文件 创建新文件 

cat file1 file2 合并显示文件1, 2

tac 反向显示文件 

cat .bashrc | less : show file content using scroll 
```

cp
---
```
目标文件存在时，会询问是否覆盖 cp -i 

一个目录及其档案复制到另一个目录下 cp -a 
```

touch
---
`touch filename` used to create empty file
`touch -a filename` use to update access time without changing the file
**rm**
---
```
rm -i 代替 rm ，删除前确认 

rm -r删除目录及其下面的所有档案 

rm -v：显示指令的详细执行过程 

rm -d 只删除空目录 ，代替 rmdir 不能删除非空目录 
```

tree 
---
 
```
show all directories and file in tree pattern 
```
 

mkdir 
---
```

递归创建多个目录 

mkdir -p test2/test22 
```
 

pwd 
---
 
```
Show current path 
```
 

 ls 
---
 
```
ls -a 

ls -l show files and detailed info(with -h can show you human readable info, size will be mb, kb)
    [detailed tutorial](https://www.garron.me/en/go2linux/ls-file-permissions.html)
    
    #drwxr-xr-x  2 patrick patrick     4096 Mar 26 12:54 bin
     -rw-r--r--  1 patrick patrick       99 Nov 15 17:12 bluetooth.txt
     
     The permissions info is represented by first ten characters, 
     first character identifies the type, d means directory and - means file
     the next nine characters represent permissions for each set.
         first three for user who owns the file
         middle three for group
         last three for others
     e.g. rwx means having all read write execute permissions, r-x means no write permissions.
     
     2 means number of dir or links
     patrick and patrick mean user and group
     4096 means size by bits
     
ls -R 

 

计算当前目录下的文件数和目录数 

ls -l * |grep "^-"|wc -l ---文件个数 

ls -l * |grep "^d"|wc -l ---目录个数 



ll: show files and detailed info including hidden files 

 

列出current directory 文件 and child-dir 的绝对路径 

ls | sed "s:^:`pwd`/:" 

```
cd
---
 
```
cd / 

cd .. 

cd cd ~ 

cd /dir/dir2 / means from root directory 

cd dir means from current directory 

cd - 
```
 


Ps 
---
 
```
ps :without parameter will only show process executed by root
ps –A :all process including those started by bootloader(systemd)
ps -A | grep <processname> 

Usually when we use the command ps we add parameters like -a, -x and -u.
While -a lists processes started by all users, -x also lists processes started at boot like daemons, the parameter -u will add columns with additional information on each process:
ps -aux
```
 

Kill 
---
```
kill PID
killall prcname 
```

jobs
---
show all backgroud process with id
> fg %(id) :bring process back to foregroud
> bg


alias
---
```
alias dtwt='syndaemon -d -i 1.0s'
```

chmod
---
```
chmod [ugao] [+-=] [rwx] [file or dir]
    1. u:user g:group a:all o:other, if none of these are used, the 'a' is default.
    2. +:add permissions -:remove them =:set a permission and remove others
    3. read write execute 

e.g. chmod u=rw, og+r, new_file.txt
     chmod -R u+x directory  -R means changing permissions recersively for a dirctory.
     
the other way is to use number to change permissions
```

curl
---
```
to retrieve content with url 
with -o option download content to filr curl url -o filename
```

df
---
```
df -h show disk space condition
```

find
---
```
find . -name <filename> :this will show all file and directories named <filename>
find . iname <name> : means case insensitive
find . type f -name <name>: means only show content whose type is file
dot '.' means current folders

```
grep(负责过滤的命令)
---
```
grep 'import' new.py :Search any line that contains the word in filename (with -i option search case-insensitive)
grep -r 'import' <path>: serch all files in current dir for word 'import'(with path option search for given dir)
grep -c 'nixcraft' frontpage.md : Search and display the total number of times that the string ‘nixcraft’ appears in a file named frontpage.md
grep -w "boo" file :with -w option search exact word 'boo' only, will not match 'boo1', '2boo' ...
with -n option show the line number of the result
Use the -l option to list file name whose contents mention main():  grep -l 'main' *.c

```

history
---
```
history | less : show command histories
and you could use '!id' to run the history command
```

less
---
```
like cate, less could also show content of a file: less new.py
```

man
---
```
man to show instructions of a command: man ps
```

top
---
```
The top command shows you a real-time display of the data relating to your Linux machine. The top of the screen is a status summary.

The first line shows you the time and how long your computer has been running for, how many users are logged into it, and what the load average has been over the past one, five, and fifteen minutes.

The second line shows the number of tasks and their states: running, stopped, sleeping and zombie.

The third line shows CPU information. Here’s what the fields mean:

us: value is the CPU time the CPU spends executing processes for users, in “user space”
sy: value is the CPU time spent on running system “kernel space” processes
ni: value is the CPU time spent on executing processes with a manually set nice value
id: is the amount of CPU idle time
wa: value is the time the CPU spends waiting for I/O to complete
hi: The CPU time spent servicing hardware interrupts
si: The CPU time spent servicing software interrupts
st: The CPU time lost due to running virtual machines (“steal time”)
The fourth line shows the total amount of physical memory, and how much is free, used and buffered or cached.

The fifth line shows the total amount of swap memory, and how much is free, used and available  (taking into account memory that is expected to be recoverable from caches).

top command in a terminal window

The user has pressed the E key to change the display into more humanly digestible figures instead of long integers representing bytes.

The columns in the main display are made up of:

PID: Process ID
USER: Name of the owner of the process
PR: Process priority
NI: The nice value of the process
VIRT: Virtual memory used by the process
RES: Resident memory used by the process
SHR: Shared memory used by the process
S: Status of the process. See the list below of the values this field can take
%CPU: the share of CPU time used by the process since last update
%MEM: share of physical memory used
TIME+: total CPU time used by the task in hundredths of a second
COMMAND: command name or command line (name + options)
(The command column didn’t fit into the screenshot.)

The status of the process can be one of:

D: Uninterruptible sleep
R: Running
S: Sleeping
T: Traced (stopped)
Z: Zombie
Press the Q key to exit from top.
```

wget
---
wget is a free utility for non-interactive download of files from the web. It supports HTTP, HTTPS, and FTP protocols, as well as retrieval through HTTP proxies.
```
'wget http://website.com/files/file.zip' : download the file from web
'wget www.pincong.rocks' :download html into index.html file
'wget url -O <filename> : download the file and change its name
'wget -o download.log url' : log output to a file
'wget -r url' : download a html page and all its links' htmls. (use -l option to specify the recursion level)

```

export
---
In general, the export command marks an environment variable to be exported with any newly forked child processes and thus it allows a child process to inherit all marked variables. 
detailed instructions [export - LinuxConfig.org](https://linuxconfig.org/learning-linux-commands-export)
> use **export** to set temporary environment variable:
`export PATH=$PATH:/home/patrick/clash` or `export PATH=$PATH:$(pwd)`(set env for current dir)
and then you can run executable by command in specified directory.

source
---
source is used to read and execute content of a file(usually a set of commands), such as .py or shell script.

netstat
---
[detailed tutorial](https://www.howtogeek.com/513003/how-to-use-netstat-on-linux/)

> socket
Sockets have two main states: They are either connected and facilitating an ongoing network communication, or they are waiting for an incoming connection to connect to them. 
The listening socket is called the server, and the socket that requests a connection with the listening socket is called a client.These names have nothing to do with hardware or computer roles. They simply define the role of each socket at each end of the connection.

The `netstat` command lets you discover which sockets are connected and which sockets are listening. Meaning, it tells you which ports are in use and which processes are using them. It can show you routing tables and statistics about your network interfaces and multicast connections.

1. `netstat -a` The -a (all) option makes netstat show all the connected and waiting sockets. 
**output**:

    Active Internet connections (servers and established)
    |Proto |Recv-Q |Send-Q |Local Address     |Foreign Address     |State |
    |tcp   |    0      0     localhost:domain      0.0.0.0:*        LISTEN 
    |tcp   |    0      0     0.0.0.0:ssh           0.0.0.0:*        LISTEN 
    |tcp   |    0      0     localhost:ipp         0.0.0.0:*        LISTEN 
    |tcp   |    0      0     localhost:smtp        0.0.0.0:*        LISTEN 
    |tcp6  |    0      0     [::]:ssh              [::]:*           LISTEN 
    |tcp6  |    0      0     ip6-localhost:ipp     [::]:*           LISTEN 
    
    
    Active UNIX domain sockets (servers and established)
    Proto RefCnt Flags   Type     State       I-Node  Path
    unix  24     [ ]     DGRAM                12831   /run/systemd/journal/dev-log
    unix  2      [ ACC ] STREAM    LISTENING  24747   @/tmp/dbus-zH6clYmvw8
    unix  2      [ ]     DGRAM                26372   /run/user/1000/systemd/notify
    unix  2      [ ]     DGRAM                23382   /run/user/121/systemd/notify
    unix  2      [ ACC ] SEQPACKET LISTENING  12839   /run/udev/control

The “Active Internet” section lists the connected external connections and local sockets listening for remote connection requests. That is, it lists the network connections that are (or will be) established to external devices.

The “Active Internet” columns are:
**Proto**: The protocol used by this socket (for example, TCP or UDP).
**Recv-Q**: The receive queue. These are incoming bytes that have been received and are buffered, waiting for the **local process** that is using this connection to read and consume them.
**Send-Q**: The send queue. This shows the bytes that are ready to be sent from the send queue.
**Local address**: The address details of the local end of the connection. The default is for netstat to show the **local hostname** for the address, and the name of the service for the port.
**Foreign address**: The address and port number of the remote end of the connection.
**State**: The state of the local socket. For UDP sockets, this is usually blank.(check out tcp notes in onenote)


The “UNIX domain” section lists the connected and listening internal connections. In other words, it lists the connections that have been established within your computer between different applications, processes, and elements of the operating system.

2. `netstat -au | less` -u option means show only udp, you can also use -t option to show tcp
3. `netstat -s` -s shows Network Statistics , use -t or other option to show result by Protocol
4. `netstat -p` -p shows process id with socket.


ifconfig
---
command that allows for diagnosing and configuring network interfaces.
[detailed explanation](https://goinbigdata.com/demystifying-ifconfig-and-network-interfaces-in-linux/)
> `tcpdump -D` can also show list of available interfaces

