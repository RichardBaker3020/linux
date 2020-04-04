pass parameters 
========================
to run a shell script as followed and pass parameters:
```
#!/bin/bash

echo "Shell 传递参数实例！";
echo "执行的文件名：$0";
echo "第一个参数为：$1";
echo "第二个参数为：$2";
echo "第三个参数为：$3";
```
note: `$0` will be the name of the script file

run: `$ ./test.sh 1 2 3`
output: 
```
Shell 传递参数实例！
执行的文件名：./test.sh
第一个参数为：1
第二个参数为：2
第三个参数为：3
```

all special parameters:
---
$#	传递到脚本的参数个数
$*	以一个单字符串显示所有向脚本传递的参数。
    如"$*"用「"」括起来的情况、以"$1 $2 … $n"的形式输出所有参数。
$$	脚本运行的当前进程ID号
$!	后台运行的最后一个进程的ID号
$@	与$*相同，但是使用时加引号，并在引号中返回每个参数。
    如"$@"用「"」括起来的情况、以"$1" "$2" … "$n" 的形式输出所有参数。
$-	显示Shell使用的当前选项，与set命令功能相同。
$?	显示最后命令的退出状态。0表示没有错误，其他任何值表明有错误。

script test.sh:
```
#! /bin/bash
echo "Hello world!"
echo "filename: $0"
echo "var1: $1"
echo "var2: $2"
echo "var3: $3"
echo "the number of parameters: $#"
echo "all parameters: $*"
echo "PID: $!"
echo "all paramters with quote mark: $@"
echo "option: $-"
echo "status: $?"
```
run: `~$ ./test.sh 'bob' 'alice' 'linus'`
output:
```
Hello world!
filename: ./test.sh
var1: bob
var2: alice
var3: linus
the number of parameters: 3
all parameters: bob alice linus
PID: 
all paramters with quote mark: bob alice linus
option: hB
status: 0
```

