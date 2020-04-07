directory tree
========================
necessary directory in root directory.
---

![qownnotes-media-N22397](../../media/595118422.png)
![qownnotes-media-Z22397](../../media/44315389.png)

`/usr` 的意义与内容:
依据FHS的基本定义,/usr里面放置的数据属于可分享的与不可变动的(shareable, static), usr是Unix Software Resource的缩写, 也就是“Unix操作系统软件资源”所放置的目录. FHS建议所有软件开发者,应该将他们的数据合理的分别放置到这个目录下的次目录,而不要自行创建该软件自己独立的目录因为是所有系统默认的软件(distribution发布者提供的软件)都会放置到/usr下面,因此这个
目录有点类似Windows 系统的“C:\Windows\ (当中的一部份) + C:\Program files\”这两个目录的综合体

> /usr is a place for system-wide, read-only files. So all your installed software goes there. It does not duplicate any names of / except /bin and /lib, but, originally, with a different purpose: /bin, /lib is only for binaries and libraries required for booting, while /usr/bin, /usr/lib is for all the other executables and libraries. (now be a good boy and don't ask about /sbin, this is the Short Version after all)
Nowadays, the distinction between "required for booting" and not has diminished, since most modern distros, including Ubuntu, cannot properly boot without several files from /usr. And that's why there is a strong movement towards merging /usr/bin and /bin, so probably in the near future (Ubuntu 12.10 perhaps?) /bin will be a symlink to /usr/bin.
detailed info about /usr and its subfolders: [link](https://askubuntu.com/questions/130186/what-is-the-rationale-for-the-usr-directory)


`/var` 的意义与内容:
/var目录主要针对常态性变动的文件,包括高速缓存(cache)、登录文件(log file)以及某些软件运行所产生的文件, 包括程序文件(lock file, run file),或者例如MySQL数据库的文件等等。

unnecessary directory
---
![qownnotes-media-l22397](../../media/503746933.png)

other directory
---
![qownnotes-media-g22397](../../media/1843252684.png)
