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
通过在函数体外部使用var关键字来进行全局变量的声明与赋值  
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

**`时间：2021-10-14 21:00`**  
**`用时：40分钟`**  
**`平台：Windows 10`** 
    
#### 2.5、package别名与省略调用  
当使用第三方包时，包名可能会非常接近或者相同，此时就可以使用别名来进行区别和调用  
```go  
import (  
    io "fmt"  
)  
```
    
//使用别名调用包  
```go  
io.Println("Hello world!")  
```
    
省略调用  
不建议使用，易混淆  
不可以和别名同时使用  
```go  
import (  
    . "fmt"  
)  
fun main() {  
    //使用省略调用  
    Println("Hello world!")  
}  
```
    
#### 2.6、可见性规则  
Go语言中，使用 大小写 来决定该 常量、变量、类型、接口、结构或函数 是否可以被外部包所调用：根据约定，函数名首字母 小写 即为private  
```go  
func getField()  
```
    
函数名首字母 大写 即为public  
```go  
func Printf()  
```
    
#### 2.7、课堂作业布置  
既然导入多个包时可以进行简写，那么声明多个 常量、全局变量或一般类型（非接口、非结构）是否也可以用同样的方法呢？  
请动手验证。  
试验结果证明可以运行  
```go  
//常量的定义  
const (  
    PI  = 3.14  
    const1 = "1"  
    const2 = 2  
    const3 = 3  
)  
//全局变量的声明与赋值  
var (  
    name = "gopher"  
    name1 = "1"  
    name2 = 2  
    name3 = 3  
)  
//一般类型声明  
type (  
    newType int  
    type1 float32  
    type2 string  
    type3 byte  
)  
```
    

**`时间：2021-10-12 21:00`**  
**`用时：1小时`**  
**`平台：Windows 10`**  
#### 二、类型与变量  
#### 3.1、知识回顾  
回顾第二章节学习的知识点  

#### 3.2、基本类型  
布尔型：bool  
	- 长度：1字节  
	- 取值范围：true, false  
	- 注意事项：不可以用数字代表true或false  
整型：int/uint  
	- 根据运行平台可能为32或64位  
8位整型：int8/uint8  
	- 长度：1字节  
	- 取值范围：-128~127/0~255  
字节型：byte（uint8别名）  

16位整型：int16/uint16  
	- 长度：2字节  
	- 取值范围：-32768~32767/0~65535  
32位整型：int32（rune）/uint32  
	- 长度：4字节  
	- 取值范围：-2^32/2~2^32/2-1/0~2^32-1  
64位整型：int64/uint64  
	- 长度：8字节  
	- 取值范围：-2^64/2~2^64/2-1/0~2^64-1  
浮点型：float32/float64  
	- 长度：4/8字节  
	- 小数位：精确到7/15小数位  

复数：complex64/complex128  
	- 长度：8/16字节  
足够保存指针的 32 位或 64 位整数型：uintptr  
其它值类型：  
	- array、struct、string  
引用类型：  
	- slice、map、chan  
接口类型：inteface  
函数类型：func  

#### 3.3、类型零值  
零值并不等于空值，而是当变量被声明为某种类型后的默认值，  
通常情况下值类型的默认值为0，bool为false，string为空字符串  
 

**`时间：2021-10-19 21:00`**  
**`用时：1小时`**  
**`平台：Windows 10`**
#### 3.4、类型别名
```go 
type (
    byte int8
    rune int32
    文本 string
)
var b 文本
b = "中文类型名"
fmt.Println(b)
```

#### 3.5、变量的声明与赋值
变量的声明格式：var <变量名称> <变量类型>
变量的赋值格式：<变量名称> = <表达式>
声明的同时赋值：var <变量名称> [变量类型] = <表达式>
```go  
var a int //变量的声明
a = 123 //变量的赋值
//变量声明的同时赋值
var b int = 321
//上行的格式可省略变量类型，由系统推断
var c = 321
//变量声明与赋值的最简写法
d := 456
```  

全局变量的声明可使用 var() 的方式进行简写
全局变量的声明不可以省略 var，但可使用并行方式
所有变量都可以使用类型推断
局部变量不可以使用 var() 的方式简写，只能使用并行方式
```go  
var (
    //使用常规方式
    aaa = "hello"
    //使用并行方式以及类型推断
    sss, bbb = 1, 2
    //ccc := 3 //不可以省略var
)
//多个变量的声明
var a, b, c, b int
//多个变量的赋值
a, b, c, d = 1, 2, 3, 4
//多个变量声明的同时赋值
var e, f, g, h int = 5, 6, 7, 8
//省略变量类型，由系统推断
var i, j, k, l = 9, 10, 11, 12
//多个变量声明与赋值的最简写法
i, m, n, 0 := 13, 14, 1, 16
```

#### 3.6、类型转换
Go中不存在隐式转换，所有类型转换必须显式声明
转换只能发生在两种相互兼容的类型之间
类型转换的格式：
	<ValueA> [:]= <TypeOfValueA>(<ValueB>)
```go  
//在相互兼容的两种类型之间进行转换
var a float32 = 1.1
b := int(a)
//以下表达式无法通过编译
var c bool = true
d := int(c)
```

#### 3.7、课堂作业布置
请尝试运行以下代码，看会发生什么，并思考为什么。
```go  
func main(){
    var a int = 65
    b := string(a)
    fmt.Println(b)
}
```
string() 表示将数据转换成文本格式，因为计算机中存储的任何东西本质上都是数字，因此此函数自然地认为我们需要的是用数字65表示的文本 A。
	
		
**`时间：2021.10.21 21:00`**  
**`用时：1小时`**  
**`平台：Windows 10`**  
#### 四、常量与运算符  
#### 4.1、知识回顾  
回顾上一章节课的知识要点  

#### 4.2、常量的定义  
常量的值在编译时就已经确定  
常量的定义格式与变量基本相同  
等号右侧必须是常量或者常量表达式  
常量表达式中的函数必须是内置函数  
```go 
//定义单个常量  
const a int = 1  
const b = 'A'  
const (  
    text = "123"  
    length = len(text)  
    num = b * 20  
)  
//同时定义多个常量  
const i, j, k = 1, "2", '3'  
const (  
    text2, length2, num2 = "456", len(text2), k * 10      
)  
```
		
#### 4.3、常量的枚举  
常量的初始化规则与枚举  
在定义常量组时，如果不提供初始值，则表示将使用上行的表达式  
使用相同的表达式不代表具有相同的值  
iota是常量的计数器，从0开始，组中每定义1个常量自动递增1  
通过初始化规则与iota可以达到枚举的效果  
每遇到一个const关键字，iota就会重置为0  
```go 
const (  
    //a与b都为“A”  
    a = "A"  
    b  
    c = iota  
    d //d的值为3  
)  
const (  
    e = iota  
    f //f的只为1  
)  
//星期枚举  
const (  
    //第一个常量不可省略表达式  
    Monday = iota  
    Tuesday  
    Wednesday  
    Thursday  
    Friday  
    Saturday  
    Sunday  
)  
```		
    
