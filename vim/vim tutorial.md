vim tutorial
========================

![media-H25803](../../media/41166119.jpeg)

command mode:
---
* :w	将编辑的数据写入硬盘档案中(常用)
* :w!	若文件属性为『只读』时，强制写入该档案。不过，到底能不能写入， 还是跟你对该档案的档案权限有关啊！
* :q	离开 vi (常用)
* :q!	若曾修改过档案，又不想储存，使用 ! 为强制离开不储存档案。

edit
--
* i, I	进入输入模式(Insert mode)：
* i 为『从目前光标所在处输入』， I 为『在目前所在行的第一个非空格符处开始输入』。 (常用)
* a, A	进入输入模式(Insert mode)：
* a 为『从目前光标所在的下一个字符处开始输入』， A 为『从光标所在行的最后一个字符处开始输入』。(常用)
* o, O	进入输入模式(Insert mode)：这是英文字母 o 的大小写。o 为『在目前光标所在的下一行处输入新的一行』； O 为在目前光标所在处的上一行输入新的一行！(常用)
* r, R	进入取代模式(Replace mode)：
* r 只会取代光标所在的那一个字符一次；R会一直取代光标所在的文字，直到按下 ESC 为止；(常用)

delete
---
* x, X	在一行字当中，x 为向后删除一个字符 (相当于 [del] 按键)， X 为向前删除一个字符(相当于 [backspace] 亦即是退格键) (常用)
* nx	n 为数字，连续向后删除 n 个字符。举例来说，我要连续删除 10 个字符， 『10x』。

* dw  - delete from cursor to the end of the word.
	* dW : word here means non-whitespaced characters
* db    delete from cursor to the beginning of the word.
	* dB :non-whitespaced characters

* dd	删除游标所在的那一整行(常用)
	* ndd	n 为数字。删除光标所在的向下 n 行，例如 20dd 则是删除 20 行 (常用)
* d$	删除游标所在处，到该行的最后一个字符
* d0	那个是数字的 0 ，删除游标所在处，到该行的最前面一个字符
j
* dgg	删除光标所在到第一行的所有数据
* dG	删除光标所在到最后一行的所有数据


copy paste/ select
---
yy	复制游标所在的那一行(常用)
p, P	p 为将已复制的数据在光标下一行贴上，P 则为贴在游标上一行！ 举例来说，我目前光标在第 20 行，且已经复制了 10 行数据。则按下 p 后， 那 10 行数据会贴在原本的 20 行之后，亦即由 21 行开始贴。但如果是按下 P 呢？ 那么原本的第 20 行会被推到变成 30 行。 (常用)

* v 字符选择,会将光标经过的地方反白选择!
	* b or w could move cursor to a word's beginning, and the vw could select this word
* V 列选择,会将光标经过的列反白选择!
* [Ctrl]+v **区块选择**可以用长方形的方式选择数据
* y 将反白的地方复制起来
* d 将反白的地方删除掉
* p 将刚刚复制的区块,在光标所在处贴上!


replace and find
---
* /word	向光标之下寻找一个名称为 word 的字符串。and then press Enter to move cursor to the word postion.
* ?word	向光标之上寻找一个字符串名称为 word 的字符串。
* n	这个 n 是英文按键。代表重复前一个搜寻的动作。举例来说， 如果刚刚我们执行 /vbird 去向下搜寻 vbird 这个字符串，则按下 n 后，会向下继续搜寻下一个名称为 vbird 的字符串。如果是执行 ?vbird 的话，那么按下 n 则会向上继续搜寻名称为 vbird 的字符串！
* N	这个 N 是英文按键。与 n 刚好相反，为『反向』进行前一个搜寻动作。 例如 /vbird 后，按下 N 则表示『向上』搜寻 vbird 。

move cursor
---
* j, k, h, l
* 0 ：移动到这一行的最前面字符处 (常用)
* $ 移动到这一行的最后面字符处(常用)
* G	移动到这个档案的最后一行(常用)
* nG	n 为数字。移动到这个档案的第 n 行。例如 20G 则会移动到这个档案的第 20 行(可配合 :set nu)
* gg	移动到这个档案的第一行 (常用)
* e : Move to the end of a word.
* w : Move forward to the beginning of a word.
	* nw
* W : Move forward a WORD (any non-whitespace characters).
* b : Move backward to the beginning of a word.
	* nb
* B : Move backward to the beginning of a word.(any non-whitespace characters)
* ) Jump forward one sentence.
* ( Jump backward one sentence.
* } Jump forward one paragraph.
* { Jump backward one paragraph.
* '.  Jump to the last-changed line.
* `` Return to the cursor position before the latest jump (undo the jump). Two back ticks. 

* [Ctrl] + [f]	屏幕『向下』移动一页，相当于 [Page Down]按键 (常用)
* [Ctrl] + [b]	屏幕『向上』移动一页，相当于 [Page Up] 按键 (常用)
* [Ctrl] + [d]	屏幕『向下』移动半页
* [Ctrl] + [u]	屏幕『向上』移动半页


other
---
* u   undo operation


