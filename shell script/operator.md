operator
========================

arithmetic operators
---
|+	|加法	|`expr $a + $b` |结果为 30 |
|-	|减法	|`expr $a - $b` |结果为 -10|
|*	|乘法	|`expr $a \* $b`|结果为 200|
|/	|除法	|`expr $b / $a` |结果为 2。|
|%	|取余	|`expr $b % $a` |结果为 0。|

note: expr command requires two backticks around the expression **``**
note2: 乘号(*)前边必须加反斜杠(\)才能实现乘法运算；
```
val=`expr 2 + 2`
echo "两数之和为 : $val"
```
```
val=`expr $a \* $b`
echo "a * b : $val"
```

numberic relation operator(only for number, not for string)
---
|-eq	|检测两个数是否相等，相等返回 true。	               |[ $a -eq $b ] 返回 false。|
|-ne	|检测两个数是否不相等，不相等返回 true。	           |[ $a -ne $b ] 返回 true。|
|-gt	|检测左边的数是否大于右边的，如果是，则返回 true。	   |[ $a -gt $b ] 返回 false。|
|-lt	|检测左边的数是否小于右边的，如果是，则返回 true。	   |[ $a -lt $b ] 返回 true。|
|-ge	|检测左边的数是否大于等于右边的，如果是，则返回 true。 |[ $a -ge $b ] 返回 false。|
|-le	|检测左边的数是否小于等于右边的，如果是，则返回 true。 |[ $a -le $b ] 返回 true。|

```
if [ $a -eq $b ]
then
   echo "$a -eq $b : a 等于 b"
else
   echo "$a -eq $b: a 不等于 b"
fi
```

boolean /logical operator
---
|-o	或运算，有一个表达式为 true 则返回 true。	[ $a -lt 20 -o $b -gt 100 ] 返回 true。 |
|-a	与运算，两个表达式都为 true 才返回 true。	[ $a -lt 20 -a $b -gt 100 ] 返回 false。|


**-a** and **-o** are the older and/or operators for the test command. 
**&&** and **||** are and/or operators for the shell.

`[ "$1" = 'yes' ] && [ -r $2.txt ]`
The shell is evaluating the and condition. 

`[ "$1" = 'yes' -a $2 -lt 3 ]`
The test command (or builtin test) is evaluating the and condition.

In modern shells, the if statement can be written:

`[[ $1 == yes && -r $2.txt ]]`
Which is more similar to modern programming languages and thus is more readable.

string operator
---
|=	    |检测两个字符串是否相等，相等返回 true。	        |[ $a = $b ] 返回 false。|
|!=	    |检测两个字符串是否相等，不相等返回 true。	    |[ $a != $b ] 返回 true。|
|-z    	|检测字符串长度是否为0，为0返回 true。	        |[ -z $a ] 返回 false。  |
|-n	    |检测字符串长度是否不为 0，不为 0 返回 true。    	|[ -n "$a" ] 返回 true。 |
|$	    |检测字符串是否为空，不为空返回 true。	        |[ $a ] 返回 true。      |

`=` and` == `are for string comparisons, `-eq` is for numeric ones.
`==` is a bash-ism, by the way. It's better to use the POSIX `=`. 
In bash the two are equivalent, and in plain sh` =` is the only one guaranteed to work.

test file operator
---
check test command for detailed info.