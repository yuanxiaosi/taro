## 基础[0]

## 教程
http://www.runoob.com/go/go-tutorial.html     
http://c.biancheng.net/golang/
    
## 介绍 [in]

### 1.1 go的功能
- Go语言从底层原生支持并发，无须第三方库、开发者的编程技巧和开发经验就可以轻松地在 Go语言运行时来帮助开发者决定怎么使用 CPU 资源。   
- Go语言的并发是基于 goroutine 的，goroutine 类似于线程，但并非线程。可以将 goroutine 理解为一种虚拟线程。Go语言运行时会参与调度 goroutine，并将 goroutine 合理地分配到每个 CPU 中，最大限度地使用CPU性能。   
- 多个 goroutine 中，Go语言使用通道（channel）进行通信，通道是一种内置的数据结构，可以让用户在不同的 goroutine 之间同步发送具有类型的消息。这让编程模型更倾向于在 goroutine 之间发送消息，而不是让多个 goroutine 争夺同一个数据的使用权。  

### 1.2 基本概念 [1.2]

- 基础文件构成
```go
package main                        //自身包名
import "fmt"                        //依赖，相当于node require
func main() {                       //每个包都有自身的main函数，自动执行
    fmt.Println("Hello, World!")
}
```

- 依赖安装
```
// GOPATH 是工作目录 1.8版本以下项目必须放到gopath/src/ 下面， 1.11版本后出现go mod，可以不设置gopath, GO111MODULE=on go run mian.go
// go get github.com/hyper-carrot/go_lib/logging
// go get 安装的依赖会放在gopath的src下面
// go项目查找依赖的路径是  
当前包下的vendor目录   
向上级目录查找，直到找到src下的vendor目录   
在 GOPATH 下面查找依赖包    
在 GOROOT 目录下查找    
```

- 执行和打包
```
go run hello.go
go build hello.go
```

- 跨平台打包(谷歌搜索go build 不同的平台)

![](img/1.png)


## 2. 各个类型的声明 [2]

### 2.1 类型 [2.1]
```go
bool  
string   
int、int8、int16、int32、int64  
float32、float64   
interface
struct
func
```


### 2.2 声明变量一般使用var [2.2]
```go
  var name string
  var age int
  var age *int

```


### 2.3 批量声明 [2.3]
```go
  var (
    a int
    b string
    c []float32
    d func() bool
    e struct {
        x int
    }
  )
```

### 2.4 短变量声明并初始化 (go自己会推导类型) [2.4]
```go
  name := "yuanxiaosi"
  age := 18
```


### 2.5 接口 [2.5]
```go
var t interface{}
t = "123"
fmt.Println(t)
t = 1
fmt.Println(t)
```


### 2.6 指针 [2.6]
```go
package main

import "fmt"

func main() {
  var name *string
  name = new(string)
  *name = "yuanxiaosi"
  test(name)
}

func test(name *string) int {
  fmt.Println(*name)
  fmt.Println(name)
  return 1
}

// 指针允许你以更简洁的方式引用大的数据结构
// 指针使程序的不同部分能够共享数据
// 指针可以用来记录数据项之间的关系(链表)
```


### 结构体声明 [2.7]
```go
package main

import "fmt"

type User struct {
  Username string
  Age int
}

func main() {
  user := User{
    Username: "yuanxiaosi",
    Age: 18,
  }

  fmt.Println(user.Username) // yuanxiaosi
  fmt.Println(user.Age) // 18
}
```

### 2.8 函数声明 [2.8]
```go
// name是传入的参数， int 是返回时的参数
func test(name string) int {
  fmt.Println(name)
  return 1
}
```

### 2.9 数组声明 [2.9]
```go
var arr make([]int{}, 0)
```


注意，go里面大写通常表示公有变量，可以被外部访问
