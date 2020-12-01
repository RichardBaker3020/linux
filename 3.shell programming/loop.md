loop
========================
while loop
---
**Syntax**

```
while command
do
   Statement(s) to be executed if command is true
done
```
**e.g.**
```
#!/bin/sh

a=0

while [ $a -lt 10 ]
do
   echo $a
   a=`expr $a + 1`
done
```

for loop
---
e.g.
```
#!/bin/sh

for var in 0 1 2 3 4 5 6 7 8 9
do
   echo $var
done
```

break/continue
---
use break, continue and if statements to break out of a loop.
```
while command
do
   Statement(s) to be executed if command is true
   if condition
   then
       break/then
done
```
