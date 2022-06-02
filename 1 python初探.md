### 1 Python初探

1.1 Python语言来历

1.2 Python的开发环境搭建

1.3 Python语言的基本要素

1.4 初步认识字符串

1.5 字符串和数的转换

1.6 最简单的输入输出

1.7 初步认识列表

1.8 在OpenJudge完成作业和考试必读

1.9 习题边写边说

#### 1.1 Python语言来历

##### 1 常见程序设计语言

1. Java : 使用最广泛的语言.

   互联网服务器端和 Android手机App

2. C/C++: 开发速度要求高的系统软件，以及大型端游

3. C#:    微软的语言，网站，桌面应用

4. PHP:   网站开发

5. JavaScript: 网站前端。在浏览器中运行

6. Swift: 苹果的语言，开发iPhone App和Mac 桌面应用

##### 2 为什么学 Python

1. 简单易学
2. 众多库支持, 功能强大
3. 编程效率高
4. 跨平台: windows, linux, Mac OS

##### 3 Python的历史

###### 1 开发者

1. Guido von Rossum，荷兰人
2. Monty Python的喜剧团体的爱好者

###### 2 版本

1. 目前：Python 3.6.2

   不向后兼容

#### 1.2 Python的开发环境搭建

##### 1 下载Python

###### 1 地址

1. https://www.python.org/downloads/
2. Mac OS, Windows: 64, 32位

##### 2 搭建Python 开发环境

1. 下载, 安装 python3.x

   Add Python 3.6 to PATH.  否则pycharm里面找不
   到python

2. 下载,安装 pycharm - community, 社区版免费

3. 配置 pycharm

4. 在 pycharm 建工程

5. 编写, 运行 python 程序

##### 3 命令行方式 : 运行python程序

1. window: win+R, cmd
2. Mac: launchPad 启动终端
3. python xxx.py  #此处的python是 命令工具 

##### 4 idle 方式 : 运行 python 程序

1. window键, 输入 idle, 
2. File | New | Run

##### 5 pycharm 方式 : 运行 python 程序

1. File|New Project     新建一个工程 

   (Mac电脑上，PyCharm的菜单在屏幕最上方)

2. File|New 新建一个 Python File, 并命名

3. Run 菜单运行程序

##### 6 pycharm为project设置解释器

1. python interpereter
2. File|Settings|Project: XXX |Project interpreter，选解释器
3. 加的办法是选python

##### 7 程序中的符号

1. 英文(半角)字符
2. '', "", ()



#### 1.3 Python语言的基本要素

##### 1 符号和注释

1. 在“字符串”中用中文

2. "#" 开头, 

   a = b   # 让a和b的值相同

3. Pycharm中, Ctrl + '/'

##### 2 变量

###### 1 有名字, 存储数据, 值可变

1. a = 12
   b = a # 让b的值变得和a一样

###### 2 变量的命名

1. 大小写字母、数字和下划线

2. 不能以数字开头, 不能有空格，长度不限，

3. 体现变量的含义

4. 匈牙利写法:

   第一个单词小写，后面单词首字母大写

5. 大小写相关

6. Python预留，不可作变量的名字

##### 3 赋值语句

###### 1 变量 = 表达式

1. 变量的值变得和“表达式”的值一样
2. 变量、数、字符串......都是“表达式”
3. a = b         # a的值变得和b一样
4. a,b = "he",12
5. a = b = c = 10
   print(a,b,c)    #>>10 10 10

#### 1.4 初步认识字符串

##### 1 字符串

1. 单引号、双引号、三单引号

2.  \  换行符

   ```
   print("this \
   is \
   good") #>>this is good    字符串太长时，可以分行写
   ```

3. 字符串里面不会包含变量

4. 字符串必须用引号括起来，用引号括起来的就是字符串！

5. 三双引号字符串中可以包含换行符、制表符以及其他特殊字符。

   ```
   para_str = """多行字符串可以使用制表符
   TAB ( \t )。
   也可以使用换行符 [ \n ]。
   <HTML><HEAD><TITLE>
   Friends CGI Demo</TITLE></HEAD>
   <BODY><H3>ERROR</H3>
   <FORM><INPUT TYPE=button VALUE=Back
   ONCLICK="window.history.back()"></FORM>
   </BODY></HTML>
   """
   ```

   \t  制表符

   \n 换行符

##### 2  字符串的下标

1. 编号就是下标

2. a = "ABCD"

   a[-1], a[0], a[2]

##### 3 字符串不可修改

1. a = "ABCD"
   a[2] = 'k'   #错，字符串中的字符不能修改

##### 4  "+"连接字符串

1. ```
   a = "ABCD"
   b = "1234"
   a = a + b
   print(a) #>>ABCD1234
   ```

##### 5 用 in , not in 判断子串

1. `"el" in a`

#### 1.5 字符串和数的转换

##### 1 字符串和数的转换

###### 1 int(x)

1. 字符串转换成整数
2. x不会变成整数， int(x)这个表达式的值是整数

###### 2 float(x)

1. 字符串x转换成小数

###### 3 str(x)

1. x转换成字符串

###### 4 eval(x)

1. 把字符串x看作一个python表达式，求其值

##### 2 小数到整数的转换

###### 1 int(x)  x是小数，则去尾取整

1. int(3.2)  #3
   int(3.9) #3

##### 3 Python 基本数据类型

1. ```
   int 整数 123456899899
   float 小数 3.2   1.5E6
   complex 复数 1+2j
   str 字符串 "hello"
   list 列表 [1,2,'ok',4.3]
   tuple 元组 (1,2,'ok',4.3)
   bool 布尔 True  False
   dict 字典 {"tom":20,"jack":30}
   set 集合 {"tom",18,71}
   ```



#### 1.6 最简单的输入输出

##### 1 print()

1. print(x,y,z....)          # 也可以只输出一项

   输出多项，以空格分隔

2. print(x,y,z...., end="")   #不换行

##### 2 input()

1. x = input(y)

   x 是变量
   y 是字符串，或 值为字符串的表达式

   回车, 输入的字符串被赋值给 x

2. 注意: 做OpenJudge作业的时候，input里面不要写
   任何东西
   s = input()



#### 1.7 初步认识列表

##### 1 列表

1. 有0到任意多个元素，下标访问元素

   empty = []  #空表

2. 元素类型可以不一样

   list = ['Google', 'Runoob', 1997, 2000]

##### 2 in 判断列表是否包含某个元素

1. ```
   lst = [1,2,3,"4",5]
   print(4 in lst,3 in lst,"4" in lst) #>>False True True
   ```

##### 3 实例：输入两个整数求和

1. s = input()
   numbers = s.split() 

##### 4 字符串分割成列表

###### 1 x.split() 的值是一个列表

1. 字符串x经空格、制表符、换行符分隔得到的所有子串

2. print("34\t\t45\n7".split())  #['34', '45', '7']

   #\t是制表符，\n是换行符号



1.8 在OpenJudge完成作业和考试必读

#### 1.9 习题边写边说

##### 1 程序顶格书写

1. 每行前面不能留空格！