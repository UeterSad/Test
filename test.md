#### go基础
(a)

```go
type user struct {
    username string
    nickname string
    sex      uint8
    birthday time.Time
}

func main() {
    u := user{
        username: "坤坤",
        nickname: "阿坤",
        sex:      20,
        birthday: time.Now(),
    }
    bs, err := json.Marshal(&u)
    if err != nil {
        log.Println(err)
        return//使用json.marshal不用&
    }
    
    fmt.Println(string(bs))
}
```


(b)

```go
func main() {
    var a = true
    defer func() {
        fmt.Println("1")
    }()

    if a {
        fmt.Println("2")
        return//执行return前只执行return之前的defer
    }

    defer func() {
        fmt.Println("3")
    }()
}
```

#### 并发基础

(a)

```go
func main(){
    ch := make(chan int)
    ch<-101
    go func(){
        ch->
        fmt.Println("出现")
    }()
}
```

(b)

```go
var ch = make(chan bool)

func main() {
	go Work("goroutine1")
	<-ch
	go Work("goroutine2")
	<-ch
	go Work("goroutine3")
	<-ch
	fmt.Println("successful")
}

func Work(workName string) {
	time.Sleep(time.Second) // 模拟逻辑处理
	fmt.Println(workName)
	ch <- true
}

```

