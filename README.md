# Golang-Study
《Go语言的学习历程全记录》

**`时间：2021-10-08 21:00`**  
**`用时：1小时`**  
**`平台：Windows 10`**  

### 一、Go开发环境搭建  
#### 1、Go基本介绍  
1.1、什么是Go？  
Go是一门并发支持、垃圾回收的编译型系统编程语言，旨在创造一门具有在静态编译语言的高性能和动态语言的高效开发之间拥有良好平衡点的一门编程语言。  
1.2、Go的主要特点有哪些？  
类型安全和内存安全；  
以非常直观和极低代价的方案实现高并发；  
高效的垃圾回收机制；  
快速编译（同时解决C语言中头文件太多的问题）；  
为多核计算机提供性能提升的方案；  
UTF-8编码支持；  
1.3、Go存在的价值是什么？  
Go在谷歌：以软件工程为目的的语言设计：https://www.oschina.net/translate/go-at-google-language-design-in-the-service-of-software-engineering  
1.4、Go是记事本编程吗？  
包括VIM、IDEA、Sublime Text、Eclipse等众多知名IDE均已支持  
1.5、Go目前有多少实际应用和资源？  
全球最大的视频网站YouTube；  
七牛云存储以及旗下网盘服务；  
爱好者开发的Go论坛及博客系统；  
已用Go开发服务端的著名企业：谷歌、盛大、七牛、360等  
其他海量开源项目：go-wiki、Go Walker、Go Language Resources  
1.6、Go发展成熟了吗？  
作为一门2009年才正式发布的编程语言，Go是非常年轻的，因此不能称之为一门成熟的编程语言，但开发者社区每天都在不断更新其核心代码，给我们这些爱好者给予了很大的学习和开发动力。  

#### 2、安装Go语言  
2.1、Go源码安装  
2.2、Go标准包安装  
Go下载，选择对应系统平台下载安装包并安装好：https://golang.org/dl/  
2.3、第三方工具安装  

#### 3、Go环境变量与工作目录  
根据约定，GOPATH下需要建立3个目录：  
bin（存放编译后生成的可执行文件）  
pkg（存放编译后生成的包文件）  
src（存放项目源码）  

#### 4、Go命令简介  
在命令行或终端输入go即可查看所有支持的命令  
go get 获取远程包（需提前安装git或svn）  
go run 直接运行程序  
go build 测试编译  
go fmt 格式化源码  
go install  编译包文件并编译整个程序  
go test 运行测试文件  
go doc 查看文档   

**`时间：2021-10-11 21:00`**  
**`用时：1小时`**  
**`平台：Windows 10`** 

godoc建立本地文档：godoc -http=:8080 建立本地官网，新版本貌似已废弃，Go 1.5是一个重要的版本，包括主要实现结构调整。尽管这样，我们期待绝大多数程序可以像之前一样编译、运行（因该版本仍遵守Go 1兼容性承诺），新的go doc命令（不同于godoc）只为命令行使用。

#### 5、IDE编辑器/Sublime Text安装与配置：  
使用Sublime Text   
下载Sublime Text：官方网站：http://www.sublimetext.com/  
安装gosublime及指令（破解版可能无法安装）：  
《Ubuntu配置Go语言开发环境（Sublime Text+GoSublime）》：https://my.oschina.net/Obahua/blog/110767  
《Win10下sublime text3搭建go语言开发环境--工具篇》：https://www.jianshu.com/p/90d76d129929  
解决编辑器报错：actions: RunCmd, error: margo has not started after 0.200s，参考：《Sublime Text 3 安装Go语言相关插件gosublime时 搜不到gosublime》https://www.cnblogs.com/chengxuyuan326260/p/10095914.html  
`到这里已经安装完成，如果想进阶使用，在ctrl + B 调出的控制台运行代码，还需要配置一下margo文件：`  
`1·在 Browse Package打开的路径下，找到GoSublime/src目录，之中新建margo目录`  
`2·把 GoSublime/src/margo.sh/extension-example/extension/extension-example.go这个文件，复制到刚刚新建的目录margo下，并改名为margo.go`  
`如果不做这两步，用gosublime执行go build等命令会如上错误。`  

#### 6、创建hello.go文件，写Go的第一个Hello world文件：  
```go  
package main  
import (  
    "fmt"  
)  
func main() {  
    fmt.Println("Hello World")  
}  
```

**`时间：2021-10-12 21:00`**  
**`用时：1小时`**  
**`平台：Windows 10`** 

### 二、Go基础知识  
#### 2.1、课堂笔记的使用方法  
https://github.com/Unknwon/go-fundamental-programming  
具体定位到课时：https://github.com/unknwon/go-fundamental-programming/blob/master/lectures/lecture1.md  
课程大纲给出了知识点讲解的时间点，方便快速定位  
补充说明在教程录制完成后根据反馈进行修正或补充  
相关链接给出了课件中所有用到的链接，方便在看视频的同时打开  

#### 2.2、Go内置关键字和注释方法  
Go内置关键字（25个均为小写）  
`break        default           func        interface        select`  
`case          defer              go           map               struct`  
`chan          else                goto       package        switch`  
`const         fallthrough    if             range             type`  
`continue   for                  import    return             var`  
Go注释方法  
// ：单行注释  
/* */：多行注释  

#### 2.3、Go程序的一般结构  
basic_structure.go  
Go程序是通过package来组织的（与python类似）  
只有package名称为main的包可以包含main函数  
一个可执行程序 有且仅有 一个main包  
通过import关键字来导入其它非main包  
通过const关键字来进行常量的定义  
通过在函数体外部使用 var 关键字来进行全局变量的声明与赋值  
通过type关键字来进行结构(struct)或接口(interface)的声明  
通过func关键字来进行函数的声明  

```go 
//当前程序的包名
package main

//导入其他的包
import (
    "fmt"
)

//全局变量的声明与赋值
var name = "gopher"

//一般类型的声明
type newType int

//结构的声明
type gopher struct{}

//接口的声明
type golang interface{}

//由main函数作为程序的入口点启动
func main(){
    fmt.Println("Hello world!你好，世界！")
}
``` 

#### 2.4、包的导入
导入包之后，就可以使用格式<PackageName>.<FuncName>
来对包中的函数进行调用
如果导入包之后 未调用 其中的函数或者类型将会报出编译错误：
imported and not used:"io"
