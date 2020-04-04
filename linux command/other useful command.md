other useful command
========================

suspend or hibernate pc
---
> sudo systemctl suspend
> sudo systemctl hibernate

check all available commands in bash
---
> ls /bin/

internal command or external command
---
> whereis <cmd> , if the corresponding path is shown for a specified command, this command is a external command, or otherwise.
```
通俗地说，“内部命令”就是内置在 shell 中的命令；而“外部命令”则对应了某个具体的【可执行文件】。
当你在 shell 中执行“外部命令”，shell 会启动对应的可执行文件，从而创建出一个“子进程”；而如果是“内部命令”，就【不】产生子进程。
```

unzip .zip file
---
> gunzip <filename>


environment var
---
> env
allow you to run another program in a another environment without influencing the current one.
run without parameter, will print all environment variables.

> printenv
> printenv HOME
> printenv LANG PWD
print env variables

> set
set  **shell** variables
show a list of env, shell and variables without parameter `set `
to create shell variables: `var='sgjgdks'`

> unset
delete shell and env variables

__Persistent Environment Variables__
```
To make Environment variables persistent you need to define those variables in the bash configuration files. In most Linux distributions when you start a new session, environment variables are read from the following files:

1. /etc/environment - Use this file to set up system-wide environment variables. Variables in this file are set in the following format:
FOO=bar
VAR_TEST="Test Var"

2. /etc/profile - Variables set in this file are loaded whenever a bash login shell is entered. When declaring environment variables in this file you need to use the export command:
export JAVA_HOME="/path/to/java/home"
export PATH=$PATH:$JAVA_HOME/bin

3. Per-user shell specific configuration files. For example, if you are using Bash, you can declare the variables in the ~/.bashrc:
export PATH="$HOME/bin:$PATH"

To load the new environment variables into the current shell session use the source command:
source ~/.bashrc
```





