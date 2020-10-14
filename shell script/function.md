```
myfunction() {
    #do things with parameters like $1 such as
    mv "$1" "$1.bak"
    cp "$2" "$1"
}
```

So for instance you can call the earlier function like this
```
$ myfunction original.conf my.conf
```
