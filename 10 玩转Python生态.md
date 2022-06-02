### 10  玩转Python生态

10.1 Python库的安装和使用

10.2 用datetime库处理日期、时间

10.3 用random库处理随机数相关事务

10.4 用jieba库进行分词和中文词频统计

10.5 用openpyxl库读取excel文档

10.6 用openpyxl库创建excel文档

10.7 用openpyxl库设定excel文档单元格样式

10.8 图像基本常识和用Pillow库缩放图像

10.9 图像的旋转、滤镜和裁剪

10.10 图像的素描化

10.11 为图像添加水印



#### 10.1 Python库的安装和使用

##### 1 python库

###### 1 Python自带的库

1. math, re, datetime, turtle, random .....

###### 2 无数第三方的库

1. Pillow, jieba, request, matplotlib ......

##### 2 安装Python第三方库

###### 1 cmd命令行安装第三库

1. cmd命令行窗口

2. 进入安装Python的文件夹，默认是: `C:\Users\你的用户名\AppData\Local\Programs\Python\Python37`

   不知道: 查找 python.exe 可以找到

3. 再进入 scripts 文件夹

4. pip install 库名

###### 2 Pycharm中安装Python第三方库

1. 菜单： File | Settings
2. Project interpreter > 点击 `+`
3. Availabel Packages中输入 库名, 回车, 点击 `Install Package`

###### 3 import导入库

1. ```
   import turtle #turtle是一个类
   turtle.setup(800,600)
   turtle.fd()
   ```

2. 或

   ```
   import turtle as tt #此后 tt 等价于 turtle
   tt.setup(800,600)
   tt.fd(100)
   ```

###### 4 import 用法1

1. ```
   import PIL.Image   #PIL.Image是库中的类
   img = PIL.Image.open("c:/tmp/pic/grass.jpg") #将图像文件载入对象img
   img.show()
   ```

###### 5 import 用法2

1. ```
   from PIL import Image #从PIL库导入Image类进行图像处理
   img = Image.open("c:/tmp/pic/grass.jpg") #将图像文件载入对象img
   ```

###### 6 import 用法3

1. ```
   import PIL.Image,PIL.ImageDraw,PIL.ImageFont
   img = PIL.Image.open("c:/tmp/pic/grass.jpg") #图像文件载入对象img
   draw = PIL.ImageDraw.Draw(img) #以后通过draw在img上画图、写字
   myFont = PIL.ImageFont.truetype("C:\\Windows\\Fonts\\simhei.ttf", 164)
   ```

###### 7 import 的用法4

1. ```
   from PIL import Image,ImageDraw,ImageFont
   img = Image.open("c:/tmp/pic/grass.jpg") #将图像文件载入对象img
   draw = ImageDraw.Draw(img) #以后通过draw在img上画图、写字
   myFont = ImageFont.truetype("C:\\Windows\\Fonts\\simhei.ttf", 164)
   ```

###### 8 import 用法5

1. ```
   from openpyxl.styles import Font,colors,Alignment
   boldRedFont = Font(size = 18, name='Times New Roman', bold=True, color = colors.RED)
   alignment = Alignment(horizontal='left', vertical='center')
   ```

   

#### 10.2 用datetime库处理日期、时间

##### 1 处理日期

###### 1 datatime对象有许多独特的处理方法

1. ```
   import datetime  #导入datetime模块
   dtBirth = datetime.date(2000,9,27)  #创建日期对象，日期为2000年9月27日
   print(dtBirth.weekday())  #>>2 输出dtBirth代表的日期是星期几。0表示星期一
   dtNow = datetime.date.today()  #取今天日期,假设是 2020年8月15日
   print(dtBirth < dtNow)      #>>True  日期可以比大小
   life = dtNow - dtBirth      #取两个日期的时间差
   print(life.days,life.total_seconds())   #>>7262 627436800.0
   #两个日期相差7262天，即627436800.0秒
   delta = datetime.timedelta(days = -10) #构造时间差对象，时间差为-10天
   newDate = dtNow + delta    #newDate代表的日期是dtNow的日期往前数10天
   print(newDate.year,newDate.month,newDate.day,newDate.weekday())
   #>>2020 8 5 2    2020年8月5日星期三
   print(newDate.strftime(r'%m/%d/%Y'))  #>>08/05/2020
   newDate = datetime.datetime.strptime("2020.08.05", "%Y.%m.%d")
   print(newDate.strftime("%Y%m%d"))  #>>20200805
   print(newDate.strftime("%m%d%y"))  #>>080520
   ```
   

###### 2 日期函数

1. datetime.date()

2. dtBirth.weekday()

3. datetime.date.today()

4. 日期对象的时间差 : life dtNow - dtBirth

5. 日期对象的天数: life.days

6. 日期对象的秒数 : life.total_seconds()

7. 时间差对象 delta = datetime.timedelta(days=-10)

8. 日期对象的时间和: newDate = dtNow + delta

9. 日期对象的年月日属性, 星期函数

   newData.year, newDate.month, newDate.day, newDate.weekday()

10. 日期或时间对象的字符串表示形式: strftime("%Y%m%d"), 

11. %Y 4位数表示年, %y 后2位表示年

###### 3 datetime与datedelta生成不同的对象

1. 'datetime.datetime' object has no attribute 'total_seconds'
2. datedelta的对象有 total_seconds()

##### 2 处理时刻

###### 1 datetime 有处理时间的函数

1. ```
   import datetime
   tm = datetime.datetime.now()    #取当前时刻，精确到微秒
   print(tm.year,tm.month,tm.day,tm.hour,tm.minute,tm.second,tm.microsecond)
   #>>2020 8 15 20 32 53 899669 假设当前时刻是2020年8月15日20时32分53秒899669微秒
   tm = datetime.datetime(2017, 8, 10, 15, 56, 10,0)
   #构造一个时刻，2017年8月10日15时56分10秒0微秒
   print(tm.strftime("%Y%m%d %H:%M:%S"))    #>>20170810 15:56:10
   print(tm.strftime("%Y%m%d %I:%M:%S %p")) #20170810 03:56:10 PM
   tm2 = datetime.datetime.strptime("2013.08.10 22:31:24",
   "%Y.%m.%d %H:%M:%S")  #由字符串生成一个时间对象
   delta = tm - tm2  #求两个时间的时间差
   print(delta.days,delta.seconds,delta.total_seconds())
   #>>1460 62686 126206686.0 #时间差是1460天零62686秒，总共126206686.0秒
   
   delta = tm2 - tm
   print(delta.days,delta.seconds,delta.total_seconds())
   #>>-1461 23714 -126206686.0
   delta = datetime.timedelta( days = 10, hours= 10,minutes=30,seconds=20)
   #构造一个时间差，10天10小时30分20秒
   tm2 = tm + delta
   print(tm2.strftime("%Y%m%d %H:%M:%S")) #>>20170821 02:26:30
   ```

###### 2 datetime时刻函数

1. 获取当前时刻,精确到微秒  datetime.datetime.now()

2. 时刻对象tm的属性: year, month, day, hour, minute, second, microsecond:

   tm.year, tm.month, tm.day, tm.hour, tm.minute, tm.second, tm.microsecond

3. 时间差对象delta的属性: days, seconds, total_seconds()

   delta.days, delta.seconds, delta.total_seconds()

4. strftime 把时间对象转为时间的字符串格式

   格式控制符: %Y%m%d %H:%M:%S

##### 3 datetime的局限

1. 能处理的时间，年份是公元1年至9999年



#### 10.3 用random库处理随机数相关事务

##### 1 random库中的函数

1. | 函数名                  | 含义                                                        |
   | ----------------------- | ----------------------------------------------------------- |
   | random.random()         | 随机生成一个[0,1]之间的数                                   |
   | random.uniform(x,y)     | 随机生成一个[x,y]之间的数（含两端，下同）。x,y可以是小数    |
   | random.randint(x,y)     | 随机生成一个[x,y]之间的整数。x,y都是整数                    |
   | random.randrange(x,y,z) | 在range(x,y,z)中随机取一个数                                |
   | random.choice(x)        | 从序列x中随机取一个元素。x可以是为列表、元组、字符串        |
   | random.shuffle(x)       | 将列表x的元素顺序随机打乱                                   |
   | random.sample(x,n)      | 从序列x中随机取一个长度为n的子序列。x可以是元组、列表、集合 |
   | random.seed(x)          | 设置随机种子为x。x可以是个数、元组、字符串                  |

##### 2 示例

1. ```
   import random
   print(random.random()) #>>0.5502568034876353
   print(random.uniform(1.2,7.8)) #>>5.147405813383391
   print(random.randint(-20,70)) #>>20
   print(random.randrange(2,20,3)) #>>17 在range(2,20,3)中随机取一个数
   print(random.choice("hello,world"))#>>d
   print(random.choice([1,2,'ok',34.6,'jack'])) #>>ok
   lst = [1,2,3,4,5,6]
   random.shuffle(lst)
   print(lst) #>>[5, 3, 4, 2, 1, 6]
   print(random.sample(lst,3)) #>>[6, 2, 3]
   ```

##### 3 设置随机种子

1. ```
   import random
   random.seed(2)  #或random.seed("ok")....种子可以是随便什么数、字符串...
   #则下面程序每次运行结果都一样
   print(random.random())
   print(random.uniform(1.2,7.8))
   print(random.randint(-20,70))
   print(random.randrange(2,30,3))
   print(random.choice("hello,world"))
   print(random.choice([1,2,'ok',34.6,'jack']))
   lst = [1,2,3,4,5,6]
   random.shuffle(lst)
   print(lst)
   print(random.sample(lst,3))
   ```

##### 4 实现4人玩牌的发牌模拟

1. ```
   import random
   cards = [str(i) for i in range(2,11)]
   cards.extend(list("JQKA"))
   #cards是 ['2', '3', '4', '5', '6', '7', '8', '9', '10', 'J', 'Q', 'K', 'A']
   allCards = [] #一副牌
   
   for s in "♣♦♥♠": #中文输入法下打“梅花”就能出梅花字符......
       for c in cards:
           allCards.append(s+c) #allCards元素形式如： '♠3'
   random.shuffle(allCards) #随机打乱52张牌
   
   for i in range(4):
       onePlayer = allCards[i::4] #每个玩家都是隔三张牌取一张
       onePlayer.sort()  #扑克牌排序规则略复杂，这个排序不太完美
       print(onePlayer)
   ```

   

#### 10.4 用jieba库进行分词和中文词频统计

##### 1 中文的分词是个问题

1. “买马上战场”应该分成“买 马 上 战场”，还是“买 马上 战场”？
2. 不容易解决，分词库 jieba 也不是总能解决。

##### 2 jieba分词示例

示例1

1. ```
   import jieba   #导入分词库
   s = "我们热爱中华人民共和国"
   lst = jieba.lcut(s)  #分词的结果是一个列表
   #默认用精确模式分词，分出的结果正好拼成原文
   print(lst)  #>>['我们', '热爱', '中华人民共和国']
   
   print(jieba.lcut(s,cut_all = True))  #全模式分词，输出所有可能的词
   #>>['我们', '热爱', '中华', '中华人民', '中华人民共和国', '华人', '人民', '人民共和国', '共和', '共和国']
   
   print(jieba.lcut_for_search(s))  #搜索引擎模式分词
   #>>['我们', '热爱', '中华', '华人', '人民', '共和', '共和国', '中华人民共和国']
   
   s =  "拼多多是个网站"
   print(jieba.lcut(s)) #>>['拼', '多多', '是', '个', '网站']
   
   jieba.add_word("拼多多") #往词典添加新词
   print(jieba.lcut(s))        #>>['拼多多', '是', '个', '网站']
   ```

###### 1 jieba分词的模式

1. jieba.lcut(s,cut_all = True)  #全模式分词
2. jieba.lcut_for_search(s))  #搜索引擎模式分词

###### 2 往词典添加一个新词

1. jieba.add_word("拼多多") #往词典添加新词 一个

示例2

1. ```
   s = "高克丝马微中"
   print(jieba.lcut(s)) #>>['高克丝', '马微', '中']
   jieba.load_userdict("c:/tmp/tmpdict.txt")
   print(jieba.lcut(s)) #>>['高克', '丝马', '微中']
   print(jieba.lcut("显微中，容不得一丝马虎。")) 
   #>>['显微', '中', '容不得', '一丝', '马虎', '。']
   ```

##### 3 用 jieba 库找出三国演义中出场次数最多的几个人

1. ```
   import jieba
   f = open("c:/tmp/三国演义utf8.txt","r",encoding="utf-8")
   text = f.read() #字符串text就是全部三国演义文本
   f.close()
   words = jieba.lcut(text)   #word是分出来的所有词
   result = {}
   for word in words:
       if len(word) == 1:
           continue
       elif word in ("诸葛亮","孔明曰"):
           word = "孔明"
       elif word in ("关公","云长","关云长"):
           word = "关羽"
       elif word in ("玄德","玄德曰"):
           word = "刘备"
       elif word in ("孟德","操贼","曹阿瞒"):
           word = "曹操"
       result[word] = result.get(word,0) + 1
   
   noneNames  = {'将军','却说','荆州','二人','不可','不能','如此','丞相',"商议","如何","主公","军士","左右","军马","引兵","次日" } #集合比列表、元组快
   for word in noneNames: #删除noneName中的词
       result.pop(word)
   items = list(result.items())
   items.sort(key = lambda x : -x[1])
   for i in range(15):
       print(items[i][0],items[i][1],end=",") #输出 人名 出现次数,
   ```

   

#### 10.5 用openpyxl库读取excel文档

##### 1 excel文档相关库

###### 1 office 2010 前 .xls 文件

1. 用 xlrd 库读取
2. 用 xlwt 库创建和修改

###### 2 office 2010 及之后 .xlsx 文件

1. 用 openpyxl 库读写 ( 官网 : openpyxl.readthedocs.io ）
2. pip install openpyxl ( 不支持 Python 3.5 及以前版本 )
3. Python 3.5 及以前 :  pip install openpyxl==2.6.4

##### 2 openpyxl读取excel文件内容

###### 1 示例

1. ```
   import openpyxl as pxl
   book = pxl.load_workbook("test2.xlsx") #book就是整个excel文件
   sheet = book.worksheets[0]   #取第0张工作表
   print(sheet.title)       #输出工作表名字(显示于工作表下方标签)
   print(sheet.min_row, sheet.max_row)  #输出最小有效行号、最大有效行号
   print(sheet.min_column, sheet.max_column)  #输出最小有效列号、最大有效列号
   for row in sheet.rows:  #按行遍历整个工作表，从第1行到sheet.max_row行（含）
       for cell in row:     #遍历一行的每个单元格。cell是一个单元格
           print(cell.value)  #cell.value是单元格的值，空单元格值是None
   for cell in sheet['G']: #遍历名为'G'的那一列
       print(cell.value)
   for cell in sheet[3]:    #遍历第3行
       print(cell.value, type(cell.value),cell.coordinate,cell.col_idx,cell.number_format)
   
   print(pxl.utils.get_column_letter(5))   #>>E 根据列号求列名
   print(pxl.utils.column_index_from_string('D'))  #>>4 根据列名求列号
   print(pxl.utils.column_index_from_string('AC')) #>>29
   colRange = sheet['C:F']   #colRange代表从第C列到第F列(含F列)
   for col in colRange:   #按列遍历第C列到第F列,col代表一列
       for cell in col: #cell是一个单元格
           print(cell.value)
   rowRange = sheet[5:10]   #rowRange代表第5行到第10行(含第10行)
   for row in sheet['A1':'D2']:  #按行遍历左上角是A1右下角是D2的子表
       for cell in row: #row[i]也可以表示第i个单元格
           print(cell.value)
   print(sheet['C9'].value) #输出 C9单元格的值
   print(sheet.cell(row=8,column=4).value)  #输出第8行第4列单元格的值
   ```

###### 2 xlsx 操作总结

excel文件, sheet表

1. pxl.load_workbook  #加载整个excel文件
2. book.worksheet[0]  #读第0张工作表

sheet 表属性

1. sheet.title  #表名

2. sheet.min_row, sheet.max_row  #最小有效行号, 最大有效行号

3. sheet.min_column, sheet.max_column  #最小有效列号, 最大有效列号

4. sheet.rows   #生成器,<generator object Worksheet._cells_by_row at 0x0000000003F26970>

5. sheet['G']  #G列, <class 'tuple'>

   其中 `type(sheet['G'][0])`   是 <class 'openpyxl.cell.cell.Cell'>

6. sheet['C:F']   #从第C列到第F列(含F列)

7. sheet[5:10]   #第5行到第10行(含第10行)

8. sheet['A1':'D2']:  #按行遍历左上角是A1右下角是D2的子表

9. sheet[3]  #第3行

openpyxl 操作 sheet表:

1. pxl.utils.get_column_letter(5) #>>E 根据列号求列名
2. pxl.utils.column_index_from_string('D') #>>4 根据列名求列号
3. pxl.utils.column_index_from_string('AC') #>>29

cell 属性操作

1. cell.value  #单元格的值
2. sheet['C9'].value) #输出 C9单元格的值
3. sheet.cell(row=8,column=4).value

##### 3 读取公式的计算结果

1. ```
   import openpyxl
   wb = openpyxl.load_workbook("c:/tmp/style.xlsx",data_only=True)
   ws = wb.worksheets[1]
   print(ws['A3'].value)
   ```

##### 4 openpyxl读取excel文件内容

###### 1 获取工作表

1. sheet = book.active #取活跃的工作表（缺省是第0张工作表)
2. sheet = book["price"] #取名为" price "的工作表

###### 2 遍历所有工作表，并打出其名字

1. ```
   for sheet in book.worksheets:  #worksheets是工作表构成的列表
   	print(sheet.title)
   ```

###### 3 单元格属性

1. type(cell.value) :  int, float ,str, datetime.datetime
2. cell.coordinate :  'A2', 'E3'
3. cell.col_idx :  单元格列号
4. cell.number_format :  数的显示格式，"General", "0.00%", "0.00E+00"等

#### 10.6 用openpyxl库创建excel文档

##### 1 openpyxl创建excel文件

1. ```
   import openpyxl
   import datetime
   book = openpyxl.Workbook()  #在内存创建一个excel文档，注意W是大写
   sheet = book.active      #取第0个工作表
   sheet.title = "sample1" #工作表取名为sample1
   dataRows = ((10, 20, 30,40.5),
   (100, 200, '=sum(A1:B2)'),
   [],
   ['1000',datetime.datetime.now(), 'ok'])
   for row in dataRows:
       sheet.append(row)  #在工作表中添加一行
   
   sheet.column_dimensions['B'].width = len(str(sheet['B4'].value)) #设置B列宽度，使其能完整显示B4单元格里的时间
   sheet['E1'].value = "=sum(A1:D1)"  #单元格值为公式
   sheet['E2'].value = 12.5             #单元格值为小数
   sheet["E2"].number_format = "0.00%"   #单元格显示格式是百分比形式
   sheet['F1'].value = 3500         #单元格值类型为int
   sheet['F2'].value = "35.00"      #单元格值类型为str
   sheet['F3'].value = datetime.datetime.today().date()
   sheet.column_dimensions['F'].width = len(str(sheet['F3'].value))
   sheet.row_dimensions[2].height = 48 #设置第2行高度为48 points
   sheet2 = book.create_sheet("Sample2")  #添加名为Sample2的工作表
   sheet2["A1"] = 50
   sheet2 = book.create_sheet("Sample0",0) #添加名为Sample0的工作表
   sheet3 = book.copy_worksheet(sheet)  #添加一张新工作表，其为sheet的拷贝
   book.remove_sheet(book["Sample2"]) #删除名为Sample2的工作表
   book.save('sample.xlsx')  #保存文件
   ```


##### 2 openpyxl操作excel总结

###### 1 excel文档创建存储

1. book =openpyxl.Workbook()  #在内存创建一个excel文档，注意W是大写
2. book.save('sample.xlsx')  #保存文件

###### 2 sheet 操作

1. sheet = book.active      #取第0个工作表
2. sheet.title = "sample1" #工作表命名为sample1

###### 3 sheet 列宽行宽

1. sheet.column_dimensions['B'].width = len(str(sheet['B4'].value)) #设置B列宽度，使其能完整显示B4单元格里的时间
2. sheet.column_dimensions['F'].width = len(str(sheet['F3'].value))
   sheet.row_dimensions[2].height = 48 #设置第2行高度为48 points

###### 4 sheet 单元格值

1. sheet['E1'].value = "=sum(A1:D1)"  #单元格值为公式
2. sheet2["A1"] = 50

###### 5 sheet 表创建

1. heet2 = book.create_sheet("Sample2")  #添加名为Sample2的工作表
2. sheet2 = book.create_sheet("Sample0",0) #添加名为Sample0的工作表
3. sheet3 = book.copy_worksheet(sheet)  #添加一张新工作表，其为sheet的拷贝

###### 6 sheet 删除

1. book.remove_sheet(book["Sample2"]) #删除名为Sample2的工作表

##### 3 将文本形式的 数 转换为真正的数

1. ```
   import openpyxl as pxl
   book = pxl.load_workbook("test2.xlsx")
   for sheet in book.worksheets:
       for row in sheet.rows:
           for cell in row:
               v = cell.value
               if type(v) == str:
                   if v.isdigit(): #如果v全部由数字组成
                       cell.value = int(v)
                   else:
                       try:
                           cell.value = float(v)#如果不是小数格式，转换会引发异常
                       except: pass
   book.save("test3.xlsx")
   ```

##### 4 将真正的 数 转换为文本形式

1. ```
   import openpyxl as pxl
   book = pxl.load_workbook("test2.xlsx")
   for sheet in book.worksheets:
       for row in sheet.rows:
           for cell in row:
               if type(cell.value) == int or type(cell.value) == float:
                   cell.value = str(cell.value)
   book.save("test3.xlsx")
   ```

   

#### 10.7 用openpyxl库设定excel文档单元格样式

##### 1 openpyxl指定单元格的样式

###### 1 openpyxl 指定单元格格式

1. ```
   import openpyxl
   from openpyxl.styles import Font,colors,PatternFill,Alignment,Side,Border
   book = openpyxl.Workbook()  #在内存创建一个excel文档，注意W是大写
   sheet = book.active   #取第0个工作表
   
   for i in range(4):   #添加4行5列数据
       sheet.append([i*5 + j for j in range(5)])
   
   side = Side(style="thin") #边线类型, 还可以是 "thick","medium","dotted"等
   border = Border(left=side,right=side,top=side,bottom=side) #边框类型
   
   for row in sheet.rows:
       for cell in row:
           cell.border = border    #为单元格设置边框类型
   sheet['A1'].fill = PatternFill(patternType='solid', fgColor="00ff00") #单元格底色设置为绿色,00ff00表示红色分量0，绿色分量255,蓝色分量0
   
   a1 = sheet['A1']
   italicRedFont = Font(size = 18, name='Times New Roman', bold=True,color = colors.RED)
   a1.font = italicRedFont #设置单元格字体
   sheet['A2'].font = sheet['A1'].font.copy(italic = True) #A2的字体和A1的字体一样，但是是斜体
   
   sheet.merge_cells('C2:D3')      #从C2到D3合并为一个单元格，此后名为 C2
   sheet['C2'].alignment = Alignment(horizontal='left', vertical='center') #C2文字水平左对齐，垂直居中
   book.save("style.xlsx")
   ```

###### 2 openpyxl 指定单元格格式函数

导入格式类

1. openpyxl.styles 格式包中导入类Font, colors, PatternFill, Alignment, Side,Border

边线,边框,字体

1. Side(style="thin") #边线类型, "thick","medium","dotted"等
2. Border(left=side,right=side,top=side,bottom=side) #边框类型
3. italicRedFont = Font(size = 18, name='Times New Roman',  bold=True, color = colors.RED)

单元格格式属性: 边框, 填充色, 字体, 对齐方式

1. cell.border = border    #为单元格设置边框类型
2. sheet['A1'].fill = PatternFill(patternType='solid', fgColor="00ff00") #单元格底色设置为绿色,00ff00表示红色分量0，绿色分量255,蓝色分量0
3. a1.font = italicRedFont #设置单元格字体
4. sheet['A2'].font = sheet['A1'].font.copy(italic = True) #A2的字体和A1的字体一样，但是是斜体
5. sheet['C2'].alignment = Alignment(horizontal='left', vertical='center') #C2文字水平左对齐，垂直居中

sheet表中单元格合并

1. sheet.merge_cells('C2:D3')      #从C2到D3合并为一个单元格，此后名为 C2

##### 2 xlrd读取 excel文件内容

1. ```
   import xlrd
   book = xlrd.open_workbook("sample.xlsx" ) #打开指定文件
   for s in book.sheets(): #遍历所有的工作表
       print(s.name)  #打出工作表名字
   sheet1 = book.sheet_by_index(0) #通过sheet索引获得sheet对象
   sheet1_name = book.sheet_names()[0] # 获得指定索引的sheet名称
   print(sheet1_name) #>>富豪记录
   
   sheet1 = book.sheet_by_name(sheet1_name) #通过名字获得sheet对象
   nrows = sheet1.nrows  #总行数
   ncols = sheet1.ncols  #总列数
   for i in range(nrows):   #打印表中的内容
       for j in range(ncols):
           cell_value = sheet1.cell_value(i, j)
           print(cell_value, end = "\t")
       print("")
   ```

###### xlrd 操作excel

打开文件

1. book = xlrd.open_workbook("sample.xlsx" ) #打开指定文件

excel文档 操作 表

1. sheet1 = book.sheet_by_index(0) #通过sheet索引获得sheet对象
2. sheet1_name = book.sheet_names()[0] # 获得指定索引的sheet名称
3. sheet1 = book.sheet_by_name(sheet1_name) #通过名字获得sheet对象

表属性

1. sheet1.nrows  #表的行
2. sheet1.ncols  #表的列

单元格的值

1. sheet1.cell_value(i, j)

##### 3 xlwt创建excel 文件

1. ```
   import xlwt
   #创建一个Wordbook对象，即创建一个Excel文件
   book = xlwt.Workbook(encoding = "utf-8", style_compression = 0)
   #创建一个工作表
   sheet = book.add_sheet("成绩单", cell_overwrite_ok = True)
   #向表sheet中添加数据
   sheet.write(0, 0, "姓名") #在第0行0列的单元格写入 "姓名"
   sheet.write(0, 1, "绩点")
   sheet.write(1, 0, "王二")
   sheet.write(1, 1, "3.4")
   sheet.write(2, 0, "赵二")
   sheet.write(2, 1, "3.9")
   
   sheet = book.add_sheet("名单", cell_overwrite_ok = True)
   sheet.write(0, 0, "学号")
   sheet.write(0, 1, "姓名")
   sheet.write(1, 0, "1234")
   sheet.write(1, 1, "Jack")
   sheet.write(2, 0, "6656")
   sheet.write(2, 1, "Jone")
   book.save("sample2.xls") #sample2.xls如果本来存在，会被覆盖
   ```

###### xlwt 操作excel

1. 创建一个Wordbook对象，即创建一个Excel文件
book = xlwt.Workbook(encoding = "utf-8", style_compression = 0)
2. 创建一个工作表
    sheet = book.add_sheet("成绩单", cell_overwrite_ok = True)
3. sheet.write(0, 0, "姓名") #在第0行0列的单元格写入 "姓名"

##### 4 xlwt向单元格添加公式

1. ```
   import xlwt
   workbook = xlwt.Workbook()
   worksheet = workbook.add_sheet('My Sheet')
   worksheet.write(0, 0, 5) # Outputs 5
   worksheet.write(0, 1, 2) # Outputs 2
   worksheet.write(1, 0, xlwt.Formula('A1*B1')) #Should output "10" (A1[5] * A2[2])
   
   worksheet.write(1, 1, xlwt.Formula('SUM(A1,B1)')) #Should output "7" (A1[5] + A2[2])
   
   workbook.save('Excel_Workbook.xls')
   ```

###### xlwt向单元格添加公式

1. xlwt.Formula('A1*B1')  #公式
2. worksheet.write(1, 0, xlwt.Formula('A1*B1'))  #单元格第1行第0列输入公式`=A1*B1`

##### 5 xlwt向单元格添加日期

1. ```
   import xlwt
   import datetime
   workbook = xlwt.Workbook()
   worksheet = workbook.add_sheet('My Sheet')
   style = xlwt.XFStyle()
   style.num_format_str = 'M/D/YY'
   
   # Other options:
   #D-MMM-YY, D-MMM, MMM-YY, h:mm, h:mm:ss,
   #h:mm, h:mm:ss, M/D/YY h:mm, mm:ss, [h]:mm:ss, mm:ss.0
   
   worksheet.write(0, 0, datetime.datetime.now(), style)
   workbook.save('Excel_Workbook.xls')
   ```

###### 1 日期格式

1. style = xlwt.XFStyle()

   style.num_format_str = 'M/D/YY'

   worksheet.write(0, 0, datetime.datetime.now(), style)

###### 2 xls文档必须关闭后才能保存成功



##### 6 xlwt向单元格添加一个超链接

1. ```
   import xlwt
   workbook = xlwt.Workbook()
   worksheet = workbook.add_sheet('My Sheet')
   worksheet.write(0, 0, xlwt.Formula('HYPERLINK("http://www.pku.edu.cn";"PKU")'))
   
   # Outputs the text "Google" linking to http://www.google.com
   
   workbook.save('Excel_Workbook.xls')
   ```

###### 1 sheet中link

1. `=HYPERLINK("http://www.pky.edu.cn";"PKU")`
2. `worksheet.write(0, 0, xlwt.Formula('HYPERLINK("http://www.pku.edu.cn";"PKU")'))`

##### 7 xlwt合并单元格

1. ```
   import xlwt
   workbook = xlwt.Workbook()
   worksheet = workbook.add_sheet('My Sheet')
   worksheet.write_merge(0, 0, 0, 3, 'First Merge')
   worksheet.write(0,4,"ok1")
   
   # Merges row 0's columns 0 through 3.
   
   font = xlwt.Font() # Create Font
   font.bold = True # Set font to Bold
   style = xlwt.XFStyle() # Create Style
   style.font = font # Add Bold Font to Style
   worksheet.write_merge(1, 2, 0, 3, 'Second Merge', style)  #(行1, 行2, 列1, 列2,'内容', style)
   
   # Merges row 1 through 2's columns 0 through 3.
   
   worksheet.write(2,4,"ok2")
   workbook.save('Excel_Workbook.xls')
   
   ```

###### 1 worksheet.write_merge()

1. 参数:  (行1, 行2, 列1, 列2,'内容', style)





#### 10.8 图像基本常识和用Pillow库缩放图像

pip install pillow

##### 1 图像处理方法

1. 图像缩放和旋转
2. 图像加滤镜
3. 图像切割
4. 图像加水印
5. 图像素描化
6. 图像加文字

##### 2 图像的常识

###### 1 图像由像素构成

1. 屏幕上每个像素由3个距离非常近的点构成，分别显示红、绿、蓝三种颜色
2. 每个像素由一个元组(r,g,b)表示，r,g,b通常是不超过255的整数

###### 2 图像模式

1. RGB: 一个像素有 红、绿、蓝三个分量

2. RGBA: 一个像素有 红、绿、蓝三个分量，以及透明度分量

3. CYMK: 一个像素有 青色（Cyan）、黄色（Yellow）、洋红色（Magenta）、黑色(K代表黑) 四个分量，

   即每个像素用元组(c,y,m,k)表示，对应于彩色打印机或印刷机的4种颜色的墨水。

4. L: 黑白图像。每个像素是一个整数，代表灰度。

##### 3 图像的缩放

1. ```
   from PIL import Image   #导入Image类进行图像处理
   img = Image.open("grass.jpg") #将图像文件载入对象img
   w,h = img.size   #获取图像的宽和高（单位:像素),img.size是个元组
   newSize = (w//2,h//2) #生成一个新的图像尺寸
   newImg = img.resize(newSize) #得到一张原图像一半大小的新图像
   newImg.save("grass_half.jpg")  #保存新图像文件
   newImg.thumbnail((128,128))  #变成宽高各128像素的缩略图
   newImg.save("grass_thumb.png", "PNG") #保存新图像文件为png文件
   newImg.show()  #显示图像文件
   ```

###### 1 图像对象的属性, 方法

1. img.size #图像的宽, 高
2. img.resize((w, h))  #改变图像的w, h
3. `img.save('路径\名.格式', '格式')`  #保存图像
4. img.show()  #显示图像

##### 4 旋转、翻转、滤镜

1. ```
   from PIL import Image
   from PIL import ImageFilter #实现滤镜效果需要
   img = Image.open("grass_half.jpg")
   print(img.format,img.mode)   #>>JPEG RGB
   newImg = img.rotate(90,expand = True)  #图像逆时针旋转90度
   newImg.show()
   newImg = img.transpose(Image.FLIP_LEFT_RIGHT)   #左右翻转
   newImg = img.transpose(Image.FLIP_TOP_BOTTOM)  #上下翻转(颠倒)
   newImg = img.filter(ImageFilter.BLUR)   #模糊效果
   ```

###### 1 img.rotate()

1. 参数: 90, expand=True
2. 旋转

###### 2 img.transpose()

1. 参数: 

   Image.FLIP_LEFT_RIGHT : 左右翻转, 

   Image.FLIP_TOP_BOTTOM  :  上下翻转

2. 翻转

###### 3 img.filter()

1. 参数:

   ImageFilter.CONTOUR  轮廓效果

   ImageFilter.EDGE_ENHANCE   边缘增强

   ImageFilter.EMBOSS   浮雕

   ImageFilter.SMOOTH   平滑

   ImageFilter.SHARPEN   锐化

   ImageFilter.BLUR   #模糊

2. 滤镜

###### 4 img.format,  img.mode

1. img.format  #编码格式, jgp等
2. img.mode  #模式, RGB, CYMB等

#### 10.9 图像的裁剪

1. ```
   from PIL import Image
   img = Image.open("grass.jpg")
   w,h = img.size[0]//3,img.size[1]//3
   gap = 10 #九宫图中相邻两幅子图间的空白宽10像素
   newImg =  Image.new("RGB",(w * 3 + gap * 2,
   h * 3 + gap * 2),"white")
   newImg.show()
   for i in range(0,3):
       for j in range(0,3):
           clipImg = img.crop((j*w,i*h,(j+1)*w,(i+1)*h))
           clipImg.save("grass%d%d.jpg" % (i,j))
           newImg.paste(clipImg,(j*(w + gap), i * ( h + gap)))
   newImg.save("grass9.jpg")  #保存九宫图
   newImg.show()
   ```


###### 1 Image.new()

1. 参数: ("图片格式", (w,h), "填充色")
2. 生成一个新图像 img

###### 2 img.crop((w1,h1, w2, h2)) 

1. 裁剪图片
2. 返回截取的图片

###### 3 newImg.paste(clipImg, (w,h))

1. 参数:

   clipImg 要粘贴的图片

   (w,h)  #做上角坐标

2. 返回粘贴了图片的新图像

###### 4 clipImg.save() 

1. 图片clipImg 保存到硬盘中

#### 10.10 图像的素描化

##### 1 Image.open(), load() 与 imread()

1. Image.open()  #保持了图像被读取的状态, 真实数据未被读取

   得到的img数据类型是 Image 对象, 不是普通的数组

2. img.load()  #读取数据

3. cv2.imread()  #读取图像的真实数据

   得到的 img 数据类型是 np.array() 类型

###### 1 导入库

1. 导入包不同
2. img = cv2.imread(path)，是opencv中的处理图片的函数， import cv2
3. img = Image.open(path)，是PIL中的一个处理图片的函数，需 from PIL import Image

###### 2 图像读取

1. cv2.imread()读取的是图像的真实数据。
2. Image.open()函数只是保持了图像被读取的状态，但是图像的真实数据并未被读取，因此如果对需要操作图像每个元素，如输出某个像素的RGB值等，需要执行对象的load()方法读取数据。

###### 3 读入图片类型 

1. Image.open(）得到的img数据类型是Image对象，不是普通的数组。
2. cv2.imread()得到的img数据类型是np.array()类型。

###### 4 通道

1. 对于Image.open()函数默认彩色图像读取通道的顺序为RGB
2. 而cv2.imread()读取通道的顺序为BGR。 

###### 5 显示方式

1. 图像显示常见方法有两种，

   一种是matplotlib的plt.imshow()方法,一种是opencv的cv2.imshow()。两个函数的输入都要求是数组。

   因此Image读取的图片要先转化为数组，再进行图片的显示。

   plt函数读入的顺序为RGB, cv2.imshow()读入的顺序是BGR。因此image与plt.imshow()配合使用，opencv的方法配套使用。

###### 6 相互转换

1. ```
   #1.Image对象->cv2(np.adarray)
    
   img = Image.open(path)
    
   img_array = np.array(img)
    
    
   #2.cv2(np.adarray)->Image对象
    
   img = cv2.imread(path)
    
   img_Image = Image.fromarray(np.uint8(img))
   ```

##### 2 图像的素描化

1. ```
   from PIL import Image
   def makeSketch(img, threshold):
       w, h = img.size
       img = img.convert('L')  #图像转换成灰度模式
       pix = img.load()        #获取像素矩阵
       
       for x in range(w-1):
           for y in range(h-1):
               if abs(pix[x,y] - pix[x+1,y+1]) >= threshold:
                   pix[x,y] = 0  #黑色
               else:
                   pix[x,y] = 255  #白色
       return img
   img = Image.open("grass.jpg")
   img = makeSketch(img, 15)  #阈值threshold为15
   img.show()
   ```

###### 1 原理

1. 像素点(i,j) 与点 (i+1, j+1)的像素值的差, 大于15, 置(i, j)为黑色, 否则(i, j)置为白色

###### 2 img.convert('L')

1. 图像模式转换, 

   L 灰度模式

   

#### 10.11 为图像添加水印

##### 1 给图像添加水印

###### 1 原理

1. imgSrc.paste(img,(x,y),mask = msk) 

2. 原理：paste时用“掩膜”指定 img 的每个像素粘贴过去的透明度。

   如果透明度为0，则完全透明，

   如果透明度为255,则完全遮盖imgSrc原来的像素。

3. mask参数即为掩膜，是个模式为"L"的图片(Image对象)

###### 2 代码

1. ```
   from PIL import Image
   def getMask(img,isTransparent,alpha):
   #返回由img变出来的掩膜
       if img.mode != "RGBA":
           img = img.convert('RGBA')  #转换成RGBA模式的图像
       w, h = img.size
       pixels = img.load()        #获取像素矩阵
       for x in range(w):
           for y in range(h):
               p = pixels[x,y]    #p是一个四元素元组(r,g,b,a)
               if isTransparent(p[0],p[1],p[2]): #判断p是否应该变成透明像素
                   #p[0],p[1],p[2] 分别是红、绿、蓝分量
                   pixels[x,y] = (p[0],p[1],p[2],0)
               else:
                   pixels[x,y] = (p[0],p[1],p[2],alpha)
       r, g, b, a = img.split()  # 分离出img中的四个分量,a就是掩膜
       return a
   
   img = Image.open("pku.png")
   msk = getMask(img, lambda r,g,b: r >245 and g > 245 and b > 245, 180)
   imgSrc = Image.open("iceland1.png ")
   imgSrc.paste(img,(imgSrc.size[0] - img.size[0] - 30 ,imgSrc.size[1] - img.size[1] - 30),mask = msk) #粘贴透明图像img到imgSrc的右下角，用a做掩膜
   imgSrc.show()
   ```

   

