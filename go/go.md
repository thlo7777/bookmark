## Go lang 笔记

#### [golang的win10安装](https://www.jianshu.com/p/164d50dd7c8f)

#### [vs code command 'go.tools.install' not found](https://stackoverflow.com/questions/59806254/command-go-tools-install-not-found)

#### [vs code go Autoimport not working](https://github.com/microsoft/vscode-go/issues/2473)
```
You need to make sure to use this configuration(from https://github.com/golang/go/wiki/gopls#editors-instructions) to get the auto-import feature back:

"go.testEnvFile": "",
"go.useLanguageServer": true,
"go.languageServerExperimentalFeatures": {
        "diagnostics": true // for diagnostics as you type
},
"[go]": {
    "editor.snippetSuggestions": "none",
    "editor.formatOnSave": true,
    "editor.codeActionsOnSave": {
        "source.organizeImports": true
    },
},
"gopls": {
    "usePlaceholders": true,
    "completeUnimported": true
},  
```
#### [golang之package](https://www.ctolib.com/topics-4852.html())

#### [关于go中的package和main关系](https://blog.csdn.net/xinbaobaoer/article/details/76991182)

#### [如何在Go中编写包](https://www.howtoing.com/how-to-write-packages-in-go)

#### [Go开发使用VSCode完全配置指南](https://cloud.tencent.com/developer/article/1590678)

#### [Go module](https://wjp2013.github.io/go/go-module/)

#### 项目不能和GOPATH/并存 Go1.12以上
```
go mod init 生成的package
$GOPATH/go.mod exists but should not
```

#### tabsize 空格
```
永久生效可以：
文件 ——> 首选项
因为vscode默认启用了根据文件类型自动设置tabsize的选项，在设置中搜索detectIndentation，取消勾选。
https://www.tuziang.com/combat/1451.html
```


#### [How to use Go with MongoDB using official mongodb-go-driver!](https://medium.com/dev-howto/how-to-use-go-with-mongodb-using-official-mongodb-go-driver-76c1628dae1e)

#### [Golang－ import 导入包的几种方式：点，别名与下划线](https://blog.csdn.net/iteye_15425/article/details/82726595)
```
1. 点操作   有时候会看到如下的方式导入包     import( . “fmt” ) 

    这个点操作的含义就是这个包导入之后在你调用这个包的函数时，你可以省略前缀的包名，也就是前面你调用的fmt.Println(“hello world”)  可以省略的写成Println(“hello world”)

2. 别名操作   别名操作顾名思义可以把包命名成另一个用起来容易记忆的名字

   import( f “fmt” )   别名操作调用包函数时前缀变成了重命名的前缀，即f.Println(“hello world”)

3.  _操作   这个操作经常是让很多人费解的一个操作符，请看下面这个import

   import ( “database/sql” _ “github.com/ziutek/mymysql/godrv” ) 
```
#### [METHODS THAT SATISFY INTERFACES IN GOLANG](https://suraj.io/post/golang-methods-interfaces/)

#### [Zero value in Golang](https://www.geeksforgeeks.org/zero-value-in-golang/?ref=rp)
```
TYPE	        ZERO VALUE
Integer	        0
Floating point	0.0
Boolean	        false
String	        “”
Pointer	        nil
Interface	    nil
....
```
#### [Methods in Golang](https://www.geeksforgeeks.org/methods-in-golang/)
#### [Methods, Interfaces and Embedded Types in Go](https://www.ardanlabs.com/blog/2014/05/methods-interfaces-and-embedded-types.html)
```
Difference Between Method and Function
--------------------------------------------------------------------------------------------------------
METHOD	                                     |               FUNCTION
--------------------------------------------------------------------------------------------------------
It contain receiver.	                     |           It does not contain receiver.
--------------------------------------------------------------------------------------------------------
It can accept both pointer and value.	     |           It cannot accept both pointer and value.
--------------------------------------------------------------------------------------------------------
                                             |
Methods of the same name but different       |           Functions of the same name but different 
types can be defined in the program.	     |           type are not allowed to define in the program.
--------------------------------------------------------------------------------------------------------
```

#### [When to use a function which receives a pointer to interface](https://forum.golangbridge.org/t/when-to-use-a-function-which-receives-a-pointer-to-interface/14484)
```
func main() {
    s := Student{}
    p := &Student{}

    myfnc(s)         // Not working
    myfnc(p)         // Not working
    myfnc(p.(*Intr)) // Not working
    myfnc(s.(*Intr)) // Not working
}

func myfnc(i *Intr) {       <-----------
}
```

#### [interface定义](https://www.jianshu.com/p/b62adfaaefc3)
* interface(接口)是golang最重要的特性之一，Interface类型可以定义一组方法，但是这些不需要实现。请注意：此处限定是一组方法，
既然是方法，就不能是变量；而且是一组，表明可以有多个方法。再多声明一点，interface本质上是一种类型，确切的说，是指针类型，

* 如果接口没有任何方法声明，那么就是一个空接口（interface{}），它的用途类似面向对象里的根类型Object，可被赋值为任何类型的对象。
接口变量默认值是nil。如果实现接口的类型支持，可做相等运算。

* interface中可以实现 Goroutines

#### [Go recover](https://www.geeksforgeeks.org/recover-in-golang/?ref=rp)

* Recover function is always called inside **the deferred function, not in the normal function**. *If you call recover function inside the normal function or outside the deferred function, then the recover function does not stop the panicking sequence as shown in Example 1.* So, always called recover function inside the deferred function because the deferred function does not stop its execution if the program panic, so the recover function stops the panicking sequence by simply restoring the normal execution of the goroutine and retrieves the error value passed to the call of panic as shown in the Example 2.
* Recover function only work if you call in the **same goroutine** in which panic occurs. If you call it in a different goroutine, then it will not work as shown in Example 3.
* If you want to find the stack trace, then use the **PrintStack function** which is defined under Debug package.

#### [Golang的select/非缓冲的Channel实例详解](https://studygolang.com/articles/5418)

#### [身份验证和OAuth](http://www.topgoer.com/%E5%BC%80%E6%BA%90/%E8%BA%AB%E4%BB%BD%E9%AA%8C%E8%AF%81%E5%92%8COAuth.html)