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

**cp**
---
```
目标文件存在时，会询问是否覆盖 cp -i 

一个目录及其档案复制到另一个目录下 cp -a 
```
 
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
ps –A 

ps -A | grep <processname> 
```
 

Kill 
---
 
```
kill PID 
```

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
grep
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






