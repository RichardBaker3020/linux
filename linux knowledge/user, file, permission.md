user, file, permission
========================

usr /group /password
---
Linux系统当中,默认的情况下,所有的系统上的帐号与一般身份使用者,还有那个root的相关信息, 都是记录在/etc/passwd这个文件内的。
至于个人的密码则是记录在/etc/shadow这个文件下。 [detailed explanation about the format of etc/shadow](https://linuxize.com/post/etc-shadow-file/)

此外,Linux所有的群组名称都纪录在/etc/group内


file types and extension
---
1. 正规文件(regular file ): 就是一般我们在进行存取的类型的文件, 第一个字符为 [ - ],例如 [-rwxrwxrwx ]。大略可以分为:
    1. 文本文件
    2. 二进制
    3. 数据格式文件: 他能够通过last这个指令读出来! 但是使用cat时,会读出乱码~因为他是属于一种特殊格式的文件。
2. 目录(directory): 就是目录啰~第一个属性为 [ d ]
3. 链接文件(link): 类似Windows系统下面的捷径, 第一个属性为 [ l ]例如 [lrwxrwxrwx] 
4. others: device, sockets, FIFO
5. 设备文件： 块设备，字符设备


permission for file
---
**x permission**
Windows下面一个文件是否具有执行的能力是借由“ 扩展名 ”来判断的, 例如:.exe, .bat, .com 等等,但是在Linux下面,我们的文件是否能被执行,则是借由是否具有“x”这个权限来决定的

**w permission**
当你对一个文件具有w权限时,你可以具有写入/编辑/新增/修改文件的内容的权限, *但并不具备有删除该文件本身的权限*!
对于文件的rwx来说, 主要都是*针对“文件的内容*”而言,与文件文件名的存在与否没有关系


permission for directory
---
**r permission**
表示具有读取目录结构清单的权限,所以当你具有读取(r)一个目录的权限时,表示你可以查询该目录下的文件名数据。
 所以你就可以利用 ls 这个指令将该目录的内容列表显示出来!

**w permission**
他表示你具有异动该目录结构清单的权限,也就是下面这些权限:
1. 创建新的文件与目录; 
2. 删除已经存在的文件与目录(不论该文件的权限为何!)
3. 将已存在的文件或目录进行更名;
4. 搬移该目录内的文件、目录位置。 总之,目录的w权限就与该目录下面的文件名异动有关就对了啦!

**x permission**
目录的x代表的是使用者能否进入该目录成为工作目录
所谓的工作目录(work directory)就是你目前所在的目录

![qownnotes-media-bK6724](../../media/1176768886.png)

if you want to modify(delete, edit, move) or read a file in a specified directory, the permission of the given file and directory needs to be set as follows:
*file1 in dir1*

![qownnotes-media-NP6724](../../media/1159409523.png)


default permission for file and directory
---
`umask` command to see default permission, output: `0022`
1. first number for root
2. the next three for u, g, o

If the default settings are not changed, files are created with the access mode `666`(no execution) and directories with `777`(all permission). 

In this example, `002`(first three num) is for normal users, and `022`(last three) is for root(for safety sake)
> for normal user:
directory permissions are 775 and default file permissions are 664.(777-002=775, and 666-002=664)

hidden attributes
---
to see hidden attributes:
` lsattr `

to change hidden attrs:
`chattr [+-=] [ASacdistu] 文件或目录名称`


> 1. S :一般文件是非同步写入磁盘的 ,如果加上 S当你进行任何文件的修改,该更动会“同步”写入磁盘中。
2. a :当设置 a 之后,这个文件将只能增加数据,而不能删除也不能修改数据,只有root 才能设置这属性
3. c :这个属性设置之后,将会自动的将此文件“压缩”,在读取的时候将会自动解压缩
3. i :这个 i 可就很厉害了!他可以让一个文件“不能被删除、改名、设置链接也无法写入或新增数据!”只有 root 能设置此属性

注意:属性设置常见的是 a 与 i 的设置值,而且很多设置值必须要身为 root 才能设置

