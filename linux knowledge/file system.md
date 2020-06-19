file system
========================
partition and filesystem
--
传统的磁盘与文件系统之应用中,一个分区就是只能够被格式化成为一个文件系统,所以我们可以说一个 filesystem 就是一个 partition。但是由于新技术的利用, 这些技术可以将一个分区格式化为多个文件系统,也能够将多个分区合成一个文件系统, 通常我们可以称呼一个可被挂载的数据为一个文件系统而不是一个分区

super block/inode/block
---
**superblock**:记录此 filesystem 的整体信息,包括inode/block的总量、使用量、剩余量, 以及文件系统的格式与相关信息等;

**inode**:记录文件的属性,一个文件占用一个inode,同时记录此文件的数据所在的 block号码;

**block**:实际记录文件的内容,若文件太大时,会占用多个 block 。

> 每个 inode 与 block 都有编号,而每个文件都会占用一个 inode ,inode 内则有文件数据放置的 block 号码。如果能够找到文件的 inode 的话,自然就知道这个文件所放置数据的 block 号码, 也就能够读出该文件的实际数据了。

Ext2 文件系统在格式化的时候基本上是区分为**多个区块群组 (blockgroup)** 的,每个区块群组都有独立的 inode/block/superblock 系统。
![qownnotes-media-Z15850](../../media/2012253410.png)


> *how does rm work?*
Whenever you delete a file using rm command, the file's data is never deleted. In other words the blocks in the file system containing data is still there.
What happens is when you run the rm command, the system marks the inode belonging to that file as unused and the data blocks of that file also as unused (but not wiped out). However ext3 zeros most of the fields in the inode, when a file is deleted.
This normal marking of unused is done for the speed... Otherwise for deletion it will take some more time. That's why you might have noted deleting even large files are faster (you can recover the data if that data blocks are not overwritten).

hard link /symbolic link
---
在 Linux 下面的链接文件有两种,一种是类似 Windows 的捷径功能的文件,可以让你快速的链接到目标文件(或目录); 另一种则是通过文件系统的 inode 链接来产生新文件名,而不是产生新文件!这种称为实体链接 (hard link)。 

**hard link**

每个文件都会占用一个 inode ,文件内容由 inode 的记录来指向; 想要读取该文件,必须要经过目录记录的文件名来指向到正确的 inode 号码才能读取。 hard link 只是在某个目录下的 block 多写入一个关连数据而已,既不会增加 inode 也不会耗用 block 数量


也就是说,其实文件名只与目录有关,但是文件内容则与 inode 有关。hard link 只是在某个目录下新增一笔文件名链接到某 inode 号码的关连记录而已。

 如果你将任何一个“文件名”删除,其实 inode 与 block都还是存在的 此时你可以通过另一个“文件名”来读取到正确的文件数据!不论你使用哪个“文件名”来编辑, 最终的结果都会写入到相同的 inode 与 block 中

  *hard link 限制*:
1. 不能跨 Filesystem;
2. 不能 link 目录。

![qownnotes-media-r15850](../../media/1756271750.png)

**symbolic link**

Symbolic link 就是创建一个独立的文件,而这个文件会让数据的读取指向他 link 的那个文件的文件名!由于只是利用文件来做为指向的动作, 所以,当来源文件被删除之后,symbolic link 的文件会“开不了”, 会“无法打开某文件!”。实际上就是找不到原始“文件名”

两个文件指向不同的 inode 号码,就是两个独立的文件存在, 由Symbolic link 所创建的文件为一个独立的新的文件,所以会占用 inode 与 block 

当你修改 Linux下的 symbolic link 文件时,则更动的其实是“原始文件”
![qownnotes-media-e15850](../../media/949972138.png)