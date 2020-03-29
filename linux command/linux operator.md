linux operator
========================

&& and ||
---

1. The right side of **&&** will only be evaluated if the exit status of the left side is zero (i.e. true). (which means success)
2. **||** evaluate the right side only if the left side exit status is non-zero (i.e. false).

```
$ false && echo howdy!****

$ true && echo howdy!
howdy!

mkdir python-virtual-environments && cd python-virtual-environments

statement && statement1 || statement2: statements succeed then stmt1 or execute stmt2
```

&
---
make command run in backgroud
```
apt install <application> &
```

;
--
**;** is just a command separator. Thus command2 will be executed whatever command1 returned.
```
command1; command2
```

!
---
The NOT Operator **!** is much like an ‘except‘ statement. 
```
rm -r !(*.html) :delete all files except for html type
```

|
---
This PIPE operator is very useful where the output of first command acts as an input to the second command. 
```
find . *python* | less
```
{}
---
Command Combination Operator {}

()
---
to indicate the command precedence

\
---
to concatenate several lines into one command, used to handle long commands

```