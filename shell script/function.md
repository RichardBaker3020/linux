```sh
myfunction() {
    #do things with parameters like $1 such as
    mv "$1" "$1.bak"
    cp "$2" "$1"
}
```