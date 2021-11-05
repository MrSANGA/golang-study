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
#### 三、类型与变量  
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

		
**`时间：2021.10.25 21:00`**  
**`用时：1小时`**  
**`平台：Windows 10`**  
#### 4.4、运算符  
Go中的运算符均是从左至右结合  
优先级（从高到低）  
```go  
^      !                                               （一元运算符）  
*       /    %    <<    >>    &      &^
+      -     |      ^                                （二元运算符）  
==   !=   <    <=    >=    >
<-                                              （专门用于channel）  
&&  
||  
```

#### 4.5、课堂作业布置  
请尝试结合常量的iota与<<运算符实现计算机储存单位的枚举  
```go  
const (  
    _ = iota  
    KB float64 = 1 << (iota * 10)  
    MB  
    GB  
    TB    
    PB  
    EB  
    ZB  
    YB  
)  
```  
    
		
**`时间：2021.10.27 21:00`**  
**`用时：1小时`**  
**`平台：Windows 10`**
#### 五、控制语句  
#### 5.1、知识回顾  
回顾上堂课的知识要点及课堂作业解答  

#### 5.2、基础知识补充（指针、递增递减语句）  
指针   
Go虽然保留了指针，但与其它编程语言不同的是，在Go当中不支持指针运算以及”->”运算符，而直接采用”.”选择符来操作指针目标对象的成员  
操作符”&”取变量地址，使用”*”通过指针间接访问目标对象  
默认值为 nil 而非 NULL  
递增递减语句  
在Go当中，++ 与 -- 是作为语句而并不是作为表达式  

#### 5.3、if判断语句  
判断语句if  
条件表达式没有括号  
支持一个初始化表达式（可以是并行方式）  
左大括号必须和条件语句或else在同一行  
支持单行模式  
初始化语句中的变量为block级别，同时隐藏外部同名变量  
1.0.3版本中的编译器BUG  
```go  
func main() {  
    a := true  
    if a, b, c := 1, 2, 3; a+b+c > 6 {  
        fmt.Println("大于6")  
    } else {  
        fmt.Println("小于等于6")  
        fmt.Println(a)  
    }  
    fmt.Println(a)  
}  
```  

#### 5.4、for循环语句  
循环语句for  
Go只有for一个循环语句关键字，但支持3种形式  
初始化和步进表达式可以是多个值  
条件语句每次循环都会被重新检查，因此不建议在条件语句中  
使用函数，尽量提前计算好条件并以变量或常量代替  
左大括号必须和条件语句在同一行  
```go  
func main() {  
    a := 1  
    for {  
        a++  
        if a > 3 {  
            break  
        }  
    }  
    fmt.Println(a)  
}  

func main() {  
    a := 1  
    for a <= 3 {  
        a++  
    }  
    fmt.Println(a)  
}  

func main() {  
    a := 1  
    for i := 0; i < 3; i++ {  
        a++  
    }  
    fmt.Println(a)  
}  
```  
		
		
**`时间：2021.10.28 21:00`**  
**`用时：1小时`**  
**`平台：Windows 10`**
#### 5.5、switch选择语句  
选择语句switch  
可以使用任何类型或表达式作为条件语句  
不需要写break，一旦条件符合自动终止  
如希望继续执行下一个case，需使用fallthrough语句  
支持一个初始化表达式（可以是并行方式），右侧需跟分号  
左大括号必须和条件语句在同一行  
```go  
func main() {  
    a := 1  
    switch a {  
        case 0:  
          fmt.Println("a=0")  
        case 1:  
          fmt.Println("a=1")  
    }  
    fmt.Println(a)  
}  

func main() {  
    a := 1  
    switch {  
        case a >= 0:  
          fmt.Println("a=0")  
        case a >= 1:  
          fmt.Println("a=1")  
    }  
    fmt.Println(a)  
}  

func main() {  
    switch a := 1; {  
        case a >= 0:  
           fmt.Println("a=0")  
           fallthrough  
        case a >= 1:  
           fmt.Println("a=1")  
    }  
}  
```  

#### 5.6、跳转语句  
跳转语句goto, break, continue  
三个语法都可以配合标签使用  
标签名区分大小写，若不使用会造成编译错误  
Break与continue配合标签可用于多层循环的跳出  
Goto是调整执行位置，与其它2个语句配合标签的结果并不相同  
```go  
func main() {  
LABEL:  
    for {  
        for i:= 0; i < 10; i++ {  
            if i > 2 {  
                break LABEL  
            } else {  
                fmt.Println(i)  
            }  
        }  
    }  
}  

func main() {  
LABEL:  
     for i := 0; i< 10; i++ {  
        for {  
            fmt.Println(i)  
            continue LABEL  
        }  
     }  
}  
```  

5.7、课堂作业布置  
将下图中的continue替换成goto，程序运行的结果还一样吗？  
请尝试并思考为什么。  
```go  
func main() {  
LABEL:  
    for i := 0; i < 10; i++ {  
        for {  
            fmt.Println(i)  
            continue LABEL  
        }  
    }  
}  
```  
		
		
**`时间：2021-11-01 21:00`**  
**`用时：1小时`**  
**`平台：Windows 10`** 
#### 六、数组array  
#### 6.1、知识回顾  
回顾上堂课的知识要点及课堂作业解答  

#### 6.2、array的定义  
数组Array  
定义数组的格式：var <varName> [n]<type>，n>=0  
数组长度也是类型的一部分，因此具有不同长度的数组为不同类型  
注意区分指向数组的指针和指针数组  
数组在Go中为值类型  
数组之间可以使用==或!=进行比较，但不可以使用<或>  
可以使用new来创建数组，此方法返回一个指向数组的指针  
Go支持多维数组  
```go  
func main() {  
    var a [2]int{1, 2}  
    var b [2]int{0: 3, 1: 4}  
    b = a  
    fmt.Println(b)  
}  
```  
		
#### 6.3、指向数组的指针和指针数组  
```go  
func main() {  
    a := [...]int{99: 1}  
    var p *[100]int = &a  
    fmt.Println(p)  
}  
		
func main() {  
    x, y := 1, 2  
    a := [...]*int{&x, &y}  
    fmt.Println(a)  
}  
```  
		
		
**`时间：2021-11-02 21:00`**  
**`用时：1小时`**  
**`平台：Windows 10`** 
#### 6.4、数组之间的比较  
```go  
func main() {  
    a := [2]int{1, 2}  
    b := [2]int{1, 3}  
    fmt.Println(a == b)  
}  
```  

#### 6.5、使用new创建数组  
```go  
func main() {  
    a := [10]int{}  
    b[1] = 2  
    fmt.Println(a)  
    p := new([10]int)  
    p[1] = 2  
    fmt.Println(p)  
}  
```  

#### 6.6、多维数组  
```go  
func main() {  
    a := [2][3]int{  
        {1, 1, 1}  
        {2, 2, 2}  
    }  
    fmt.Println(a)  
}  
```  
		
#### 6.7、冒泡排序  
```go  
func main() {  
    a := [...]int{5, 2, 6, 3, 9}  
    fmt.Println(a)  

    num := len(a)  
    for i := 0; i < num; i++ {  
        for j := i + 1; j < num; j++ {  
            if a[i] < a[j] {  
                temp := a[i]  
                a[i] = a[j]  
                a[j] = temp  
            }  
        }  
    }  
}  
```  
		

**`时间：2021-11-04 21:00`**  
**`用时：1小时`**  
**`平台：Windows 10`** 
#### 七、切片slice  
#### 7.1、知识回顾  
回顾上堂课的知识要点及课堂作业解答  

#### 7.2、slice概述  
切片Slice  
其本身并不是数组，它指向底层的数组  
作为变长数组的替代方案，可以关联底层数组的局部或全部  
为引用类型  
可以直接创建或从底层数组获取生成  
使用len()获取元素个数，cap()获取容量  
一般使用make()创建  
如果多个slice指向相同底层数组，其中一个的值改变会影响全部  
make([]T, len, cap)  
其中cap可以省略，则和len的值相同  
len表示存数的元素个数，cap表示容量  
```go  
func main() {  
    var s1 []int  
    fmt.Println(s1)  
}  
func main() {  
    a := [10]int  
    fmt.Println(a)  
    s1 := a[9]  
    fmt.Println(s1)  
}  
func main() {  
    a := [10]int  
    fmt.Println(a)  
    s1 := a[5:10]  
    s2 := a[5:len(a)]  
    s3 := a[5:]  
    s4 := a[:5]  
    fmt.Println(s1)  
    fmt.Println(s2)  
    fmt.Println(s3)  
    fmt.Println(s4)  
}  
```  

#### 7.3、创建slice  
```go  
func main() {  
    s1 := make([]int, 3, 10)  
    fmt.Println(len(s1), cap(s1))  
}  
func main() {  
    a := []byte{'a', 'b', 'c', 'd', 'e', 'f', 'g', 'h', 'i', 'j', 'k'}  
    sb := a[2:5]  
    sc := a[3:5]  
    fmt.Println(string(sa))  
    fmt.Println(string(sc))  
}  
```  
	
			  
			  
