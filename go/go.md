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