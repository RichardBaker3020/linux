 terminal command
====
1.**more**
---
`more 按页显示文件内容，空格翻页 b回到第一页`


2.**cat** 
---
```
cat 文件 查看文件内容 

cat > 文件 创建新文件 

cat file1 file2 合并显示文件1, 2

tac 反向显示文件 
```

3.**cp**
---
```
目标文件存在时，会询问是否覆盖 cp -i 

一个目录及其档案复制到另一个目录下 cp -a 
```
 
4.**rm**
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

ls -l 

ls -R 

 

计算当前目录下的文件数和目录数 

ls -l * |grep "^-"|wc -l ---文件个数 

ls -l * |grep "^d"|wc -l ---目录个数 

 

specific info of dirs and files:

ll 

 

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


&& 
---


$
---
mkdir python-virtual-environments && cd python-virtual-environments 
