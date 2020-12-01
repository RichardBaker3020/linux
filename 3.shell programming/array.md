array
========================
`array=(var1 var2 var3)`

1. use space to separate elements
2. you can also define a array like this:
    `array[0]=1 ; array[1]=2 ; array[7]=8' `
    note: you can define element in array not in nummeric order, and the array will be like:
```
    set | grep array_a
    
    array_a=([0]="1" [1]="2" [2]="3" [3]="4" [6]="8")
```

get element by position
---
`${array[3]}`

use `@` char to access all elements:
`echo ${array_name[@]}`

array length
---
`echo ${#array_name[@]}`

note: the following will get the length of a element by position
`echo ${#array_name[3]}`

