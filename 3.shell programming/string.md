string
========================
singgle quote and double quotes
---
you can use single quote or double quote around a string variable. Difference:
1. single quote `''` won't interpolate(insert) anything, including varaible, `\` escapes, etc.
```
patrick@surface:~$ var=232

patrick@surface:~$ echo 'eth $var'
eth $var

patrick@surface:~$ echo "eth $var"
eth 232
```

2. double quote
```
your_name='runoob'
str="Hello, I know you are \"${your_name}\"! \n"
echo -e $str  # -e enable interpretation of backslash escapes

output:
Hello, I know you are "runoob"! 
```

string length
---
```
string="abcd"
echo ${#string}

output:
4
```

index and slice
---
`echo ${var:0}` get characters from 1th character up to the last one.
`echo ${var:0:2}` get chars from 1th up to next two.

```sh

${f:0:-2}
```

Last three characters of `string`:
``` lang-sh
${string: -3}
```
or
``` lang-sh
${string:(-3)}
```

get position
---
```
string="runoob is a great site"
echo `expr index "$string" o`

  # 输出 4
```
注意： 以上脚本中 ` 是backtick，而不是single quote