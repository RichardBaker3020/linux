if else/case
========================
if
---
```
if condition
then
    command1 
    command2
    ...
    commandN 
fi
```

e.g.
```
a=10
b=20

if [ $a == $b ]
then
   echo "a is equal to b"
fi
```

if...else
---
```
a=10
b=20

if [ $a == $b ]
then
   echo "a is equal to b"
else
   echo "a is not equal to b"
fi
```

elif
---
```
a=10
b=20

if [ $a == $b ]
then
   echo "a is equal to b"
elif [ $a -gt $b ]
then
   echo "a is greater than b"
elif [ $a -lt $b ]
then
   echo "a is less than b"
else
   echo "None of the condition met"
fi
```

case
---
```
case 值 in
    模式1)
        command1
        command2
        ;;
    模式2）
        command1
        command2
        ;;
    *)
        commnand others
        ;;
esac
```
> 取值后面必须为单词in，每一模式必须以右括号结束。
> 取值可以为变量或常数。
> 如果无一匹配模式，使用星号 * 捕获该值，再执行后面的命令。