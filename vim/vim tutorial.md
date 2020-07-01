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


copy cut paste/ select
---
yy	复制游标所在的那一行(常用)
p, P	p 为将已复制的数据在光标下一行贴上，P 则为贴在游标上一行！ 举例来说，我目前光标在第 20 行，且已经复制了 10 行数据。则按下 p 后， 那 10 行数据会贴在原本的 20 行之后，亦即由 21 行开始贴。但如果是按下 P 呢？ 那么原本的第 20 行会被推到变成 30 行。 (常用)

* v 字符选择,会将光标经过的地方反白选择!
	* b or w could move cursor to a word's beginning, and the vw could select this word
* V 列选择,会将光标经过的列反白选择!
* [Ctrl]+v **区块选择**可以用长方形的方式选择数据
* y 将反白的地方复制起来
* d 将反白的地方 cut
* p 将刚刚复制的区块,在光标所在处贴上!


replace and find
---
* /word	向光标之下寻找一个名称为 word 的字符串。and then press Enter to move cursor to the word postion.
* ?word	向光标之上寻找一个字符串名称为 word 的字符串。
* n	这个 n 是英文按键。代表重复前一个搜寻的动作。
* N	这个 N 是英文按键。与 n 刚好相反，为『反向』进行前一个搜寻动作。

* `:s/foo/bar/g`  Find each occurrence of 'foo' (in the *current* line only), and replace it with 'bar'
    * `%` means all lines: `:%s/foo/bar/g` replace in *all* lines
    * `c` means confirme: `:%s/\<foo\>/bar/gc` asks for confirmation
    * `i` means case insensitive, `I` means case sensitive: `:%s/foo/bar/gci`, `:%s/foo/bar/gcI`
    *  `:%s/\<foo\>/bar/gc` means replace words exactly matching foo

move cursor
---
* j, k, h, l
* 0 ：移动到这一行的最前面字符处 (常用)
* $ 移动到这一行的最后面字符处(常用)
* G	移动到这个档案的最后一行(常用)
* nG	n 为数字。移动到这个档案的第 n 行。例如 20G 则会移动到这个档案的第 20 行(可配合 :set nu)
* gg	移动到这个档案的第一行 (常用)
* go to particular line :  command mode and type number (:30) 
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
* ` '.`  Jump to the last-changed line.
* `` Return to the cursor position before the latest jump (undo the jump). Two back ticks. 
* `g;` move back cursor history,  `g,` move forward

* [Ctrl] + [f]	屏幕『向下』移动一页，相当于 [Page Down]按键 (常用)
* [Ctrl] + [b]	屏幕『向上』移动一页，相当于 [Page Up] 按键 (常用)
* [Ctrl] + [d]	屏幕『向下』移动半页
* [Ctrl] + [u]	屏幕『向上』移动半页

other
---
* u   undo operation
* ctrl+r redo

### open multiple files
 我们可以使用 vim 后面同时接好几个文件来同时打开, 相关的按键有:
 编辑下一个文件 :n

 编辑上一个文件 :N

 列出目前这个 vim 的打开的所有文件 :files


### tab several lines:
[link](https://stackoverflow.com/questions/235839/indent-multiple-lines-quickly-in-vi)
first, select block you wanna indent, and then use :
the **>** command. To indent five lines, **5>>**. NOTE: this is angle brackets < >

To mark a block of lines and indent it, Vjj> to indent three lines (Vim only). To indent a curly-braces block, put your cursor on one of the curly braces and use >% or from anywhere inside block use >iB.

If you’re copying blocks of text around and need to align the indent of a block in its new location, use ]p instead of just p. This aligns the pasted block with the surrounding text.

Also, the shiftwidth setting allows you to control how many spaces to indent.

### show line number
command mode (:set number)
cancel  (:set nonumber)

### comment
https://stackoverflow.com/a/1676690/11887333

comment a block of text:
1. First, go to the first line you want to comment, press **Ctrl+V**. This will put the editor in the VISUAL BLOCK mode.
2. Then using the arrow key and select until the last line
3. Now press **Shift+I**, which will put the editor in INSERT mode and then press **#**. This will add a hash to the first line.
4. Then press Esc (give it a second) twice, and it will insert a # character on all other selected lines.

uncomment:
Put your cursor on the first # character, press **Ctrl+V**, and go down until the last commented line and press **x**

### auto complete
Use `Ctrl-N` to get a list of word suggestions while in insert mode.

### show file path
`ctrl + G`

