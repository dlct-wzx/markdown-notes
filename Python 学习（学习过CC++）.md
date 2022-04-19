[TOC]

# Python 学习（学习过C/C++）

## 一、基本语法

### 1.注释

1. **单行注释**以`#`为开头
2. **多行注释**可以以三引号开头，三引号结尾,"""或‘’‘

```python
# 第一个注释
'''
第二行注释
'''
"""
第三行注释
"""
```

### 2、变量

注：`import`插入模块（包），keyword模块可以输出当前版本的所有关键字：

```python
import keyword  # 导入模块
keyword.kwlist  # 输入

# 输出结果
['False', 'None', 'True', 'and', 'as', 'assert', 'async', 'await', 'break', 'class', 'continue', 'def', 'del', 'elif', 'else', 'except', 'finally', 'for', 'from', 'global', 'if', 'import', 'in', 'is', 'lambda', 'nonlocal', 'not', 'or', 'pass', 'raise', 'return', 'try', 'while', 'with', 'yield']
```

python不像C语言要声明变量而且需要分配数值类型，直接使用即可

变量名 = 数据

变量名1 = 变量名2 = 数据

变量名1，变量名2 = 数据1，数据2

**del语句：**

通过使用del来销毁对象

```python
del 变量1，变量2
```



### 3、函数（function）

不同于C函数需要定义返回值的类型，python不需要，并且python对于函数内语句通过缩进来识别而不是C的大括号

```python
def fundtion_name(形参列表) # 不同与C，无需声明形参类型
	函数语句
	return 返回值  # 无返回值时返回None 
```

 ### 4、Python数据类型

#### **数字型**

1. 数字的三种类型：**整数、浮点数和复数**
   - int（整型）
   - float（浮点型）
   - complex（复数型）

2. **数字类型的转换**

   - **int(x)** 将x转换为一个整数。

   - **float(x)** 将x转换到一个浮点数。

   - **complex(x)** 将x转换到一个复数，实数部分为 x，虚数部分为 0。

   - **complex(x, y)** 将 x 和 y 转换到一个复数，实数部分为 x，虚数部分为 y。x 和 y 是数字表达式。

3. **数学函数**

- *round()函数**

```python
# 四舍五入保留指定精度
# 语法：结果 = round(需要计算的小数,精度)，精度就是保留几位小数的意思
print(round(1.29, 1))  # 1.3
print(round(1.21, 1))  # 1.2
```

- **max()**:最大值

- **min()**:最小值

- **abs()**:绝对值

- **random():**随机生成下一个实数

- **shuffle():**将序列的所有元素随机排序

- **seed():**改变随机数生成器的种子seed

···················

#### **字符串（string）**

使用input读取string，再转换为数字型

```python
x=int(input())
y=float(input())
z=complex(input())
```

并且可以直接加和乘

- 字符串的常见操作

**1. find** 

检测字符串(str) 是否包含在目标字符串中，如果存在返回开始的索引值，否则返回**-1** 

```python
mystr.find(str, start=0, end=len(mystr))

# 例：
mystr = 'hello world kkb'
mystr.find("kkb") 
#运行结果为:12 

mystr.find("kkb",0,10)
#在mstr字符串0-10下标范围查询 运行结果:-1
```

**2. index** 

与 find() 方法一样，只不过如果 str 不在 mystr中会报一个异常. 

```python
mystr.index(str, start=0, end=len(mystr))

# 例：
mystr = 'hello world kkb' 
mystr.index("ab") 
# 运行结果:控制台会直接报错(Vale Error:substring not found)
```

**3. count** 

返回 str 在start和end之间 在 mystr里面出现的次数 

```python
mystr.count(str, start=0, end=len(mystr))

# 例：
mystr = 'hello world kkb and kkb' 
mystr.count('kkb') 
# 运行结果:2
```

**4. replace** 

把 mystr 中的 str1 替换成 str2 ,如果 count 指定，则替换不超过 count 次. 

```python
mystr.replace(str1, str2, mystr.count(str1)) 
```

**5. split** 

以 str 为分隔符切片 mystr ，如果 maxsplit 有指定值，则仅分隔 maxsplit 个子字符串 

```python
mystr.split(str=" ", 2) 
```

**6.capitalize** 

把字符串的第一个字符大写 

```python
mystr.capitalize() 
```

**7. title** 

```python
a = "hello kkb" 
a.title() 

运行结果 
'Hello Kkb' 
```

**8. startswith** 

检查字符串是否是以 str 开头, 是则返回 True ，否则返回 False 

```python
mystr.startswith(str) 
```

**9. endswith** 

检查字符串是否以 str 结束，如果是返回 True ,否则返回 False . 

```python
mystr.endswith(str) 
```

**10. lower** 

转换 mystr 中所有大写字符为小写 

```python
mystr.lower() 
```

**11. upper** 

转换 mystr 中的小写字母为大写 

```python
mystr.upper()
```

**12. ljust** 

返回一个原字符串左对齐,并使用空格填充至长度 width 的新字符串 

```python
mystr.ljust(width) 
```

**13. rjust** 

返回一个原字符串右对齐,并使用空格填充至长度 width 的新字符串 

```python
mystr.rjust(width) 
```

**14. center** 

返回一个原字符串居中,并使用空格填充至长度 width 的新字符串 

```python
mystr.center(width) 
```

**15. lstrip** 

删除 mystr 左边的空白字符 

```python
mystr.lstrip() 
```

**16. rstrip** 

删除 mystr 字符串末尾的空白字符 

```python
mystr.rstrip() 
```

**17. strip** 

删除 mystr 字符串两端的空白字符 

```python
a = "\n\t kkb \t\n" 
a.strip() 

运行结果: 
'kkb' 
```

**18. rfind** 

类似于 find() 函数，不过是从右边开始查找. 

```python
mystr.rfind(str, start=0,end=len(mystr) ) 
```

**19. rindex** 

类似于 index() ，不过是从右边开始. 

```python
mystr.rindex( str, start=0,end=len(mystr)) 
```

**20. partition** 

用来根据指定的分隔符将字符串进行分割。如果字符串包含指定的分隔符，则返回一个3元的元组，第一个为分隔符左边的子串，第二个为分隔符本身，第三个为分隔符右边的子串。

```python
mystr.partition(str)
# str : 指定的分隔符。
```

**21. rpartition** 

类似于 partition()函数,不过是从右边开始. 

**22. split**

通过指定分隔符对字符串进行切片

```python
mystr.split(str="", num=string.count(str))
# str -- 分隔符，默认为所有的空字符，包括空格、换行(\n)、制表符(\t)等。
# num -- 分割次数。默认为 -1, 即分隔所有。

"""
    str -->  list

    列表 = “a-b-c-d”.split(“分隔符”)
"""
# 需求：将一个字符串描述的多个信息分别提取出来(列表)
names = "齐天大圣-猪八戒-唐僧"
list_names = names.split("-")
for item in list_names:
    print(item)
print(list_names)

```

**23. join** 

连接字符串数组。将字符串、元组、列表中的元素以指定的字符(分隔符)连接生成一个新的字符串

```python
'sep'.join(seq)
# sep：分隔符。可以为空
# seq：要连接的元素序列、字符串、元组、字典

"""
    list  -->  str

    字符串 = "连接符".join(列表)
"""
将列表转化为字符串以'sep'连接
```

#### bool（布尔值）

同C/C++

#### 空值对象（None）

1. 表示不存在的特殊对象 （类似于NULL）

2. 作用：占位和解除与对象的关联

#### 常⽤的数据类型转换

| 函数                   | 说明                                                |
| ---------------------- | --------------------------------------------------- |
| int(x [,base ])        | 将x转换为⼀个整数                                   |
| float(x )              | 将x转换为⼀个浮点数                                 |
| complex(real [,imag ]) | 创建⼀个复数，real为实部，imag为虚部                |
| str(x )                | 将对象 x 转换为字符串                               |
| repr(x )               | 将对象 x 转换为表达式字符串                         |
| eval(str )             | ⽤来计算在字符串中的有效Python表达式,并返回⼀个对象 |
| tuple(s )              | 将序列 s 转换为⼀个元组                             |
| list(s )               | 将序列 s 转换为⼀个列表                             |
| chr(x )                | 将⼀个整数转换为⼀个Unicode字符                     |
| ord(x )                | 将⼀个字符转换为它的ASCII整数值                     |
| hex(x )                | 将⼀个整数转换为⼀个⼗六进制字符串                  |
| oct(x )                | 将⼀个整数转换为⼀个⼋进制字符串                    |
| bin(x )                | 将⼀个整数转换为⼀个⼆进制字符串                    |

### 5、运算符

#### 算数运算符

（优先级从高到低排列）

| 算术运算符  | 含义   |
| ----------- | ------ |
| ()          | 小括号 |
| ** （新增） | 幂运算 |
| *           | 乘法   |
| /           | 除法   |
| %           | 求余   |
| // （新增） | 整除   |
| +           | 加法   |
| -           | 减法   |

#### 逻辑运算符

1. 与(and)
2. 或(or)
3. 非(not)     #上面三种同C/C++
4. 短路运算

#### 成员运算符

成员运算符：测试实例中包含了一系列的成员，包括字符串，列表或元组。

| **运算符** | **描述**                                                | **实例**                                          |
| ---------- | ------------------------------------------------------- | ------------------------------------------------- |
| in         | 如果在指定的序列中找到值返回 True，否则返回 False。     | x 在 y 序列中 , 如果 x 在 y 序列中返回 True。     |
| not in     | 如果在指定的序列中没有找到值返回 True，否则返回 False。 | x 不在 y 序列中 , 如果 x 不在 y 序列中返回 True。 |

#### 身份运算符

身份运算符用于比较两个对象的存储单元

| 运算符 | 描述                                        | 实例                                                         |
| ------ | ------------------------------------------- | ------------------------------------------------------------ |
| is     | is 是判断两个标识符是不是引用自一个对象     | **x is y**, 类似 **id(x) == id(y)** , 如果引用的是同一个对象则返回 True，否则返回 False |
| is not | is not 是判断两个标识符是不是引用自不同对象 | **x is not y** ， 类似 **id(a) != id(b)**。如果引用的不是同一个对象则返回结果 True，否则返回 False。 |

### 5、切片（slice）

1. 作用：

   ​	定位多个容器元素。

2. 语法：

   ​	容器[开始索引:结束索引:步长]

3. 说明：

   ​	结束索引不包含该位置元素

   ​	步长是切片每次获取完当前元素后移动的偏移量

   ​	开始、结束和步长都可以省略

   ​	切片要生成新的列表

```python
message = "123456789"
print(message[2:5:1])  # 345
print(message[:5]) # 12345
print(message[:]) # 123456789
print(message[::2]) # 13579
print(message[1:-3])  # 23456
print(message[::-1])  # 987654321
print(message[-4:1:-1])  # 6543
print(message[:99])  # 123456789
print(message[:-99:-1])  # 987654321
print(message[3:1:])  # 无
print(message[1:1])  # 无
```

### 6、选择语句

#### if elif else 语句（C/C++中if-else if-else语句）

**语法**:

```python
if condition_1:
    statement_block_1
elif condition_2:
    statement_block_2
else:
    statement_block_3
```

- 如果 "condition_1" 为 True 将执行 "statement_block_1" 块语句

- 如果 "condition_1" 为False，将判断 "condition_2"
- 如果"condition_2" 为 True 将执行 "statement_block_2" 块语句
- 如果 "condition_2" 为False，将执行"statement_block_3"块语

### 7、循环语句

#### while循环

1. **语法:**

   while 条件:

   ​        循环体或满足条件执行的语句

   else:

   ​        不满足条件执行的语句

   **备注：**while 循环的else语句作用：判断while循环退出原因,是在循环条件还是在循环体

2. **说明:**

   else子句可以省略

   在循环体内用break终止循环时,else子句不执行

#### for循环

1. **语法:**

   ​    for 变量列表 in 可迭代对象：

   ​        	语句块1

   ​    else:

   ​        	语句块2

   ```python
   message = "我是齐天大圣孙悟空"
   for item in message:
   	print(item)
       
   # 使用for...in...这类语法从list、tuple、dict、set、str中依次取出数据进行使用的过程称为遍历，也叫迭代
   # 把可以通过for...in...这类语句迭代读取一条数据供我们使用的对象称之为可迭代对象（Iterable）
   ```

2. **说明:**

   ​    else子句可以省略

   ​    在循环体内用break终止循环时,else子句不执行

### 8、跳转语句

都只能用在循环之内

#### break 语句 # 同C/C++

#### continue 语句 # 同C/C++

#### pass 语句

pass是空语句，是为了保持程序结构的完整性。不做任何事情，一般用做占位语句，填充语法空白

```python
for letter in 'Runoob': 
   if letter == 'o':
      pass
      print ('执行 pass 块')
   print ('当前字母 :', letter)
 
print ("Good bye!")
```

## 二、Python基本数据结构

### 1、列表[list]

1. **定义：**由一系列变量组成的**可变**序列容器。

2. **基本操作：**

   1. 创建列表： 

      列表名 = []   

      列表名 = list(可迭代对象)

      ```python
      list01 = [] # 创建空列表
      print(list01)
      
      list02 = [ "八戒","悟空","唐僧"]
      print(list02)
      
      list03 = list("我是齐天大圣孙悟空.")
      print(list03)
      ```

   2. 添加元素：

      列表名.append(元素)  # 加在最后

      列表.insert(索引，元素)

   3. 定位元素：

      - 获取元素

        变量 = 列表名[索引]

        变量 = 列表名[切片] # 赋值给变量的是切片所创建的新列表 

      ```python
      # 获取元素
      print(list01[1])  # 打印第二个元素
      
      item01 = list01[-2]  # 将倒数第二个元素赋值给变量item01
      print(list01[:4])  # 获取前四个元素 [通过切片获取列表元素,会创建新列表]
      ```

      - 修改元素

        列表名[索引] = 元素

        列表名[切片] = 容器 # 右侧必须是可迭代对象，左侧切片没有创建新列表。

        ```python
        # 修改
        list01[1] = "猪八戒"  # 修改列表第二个元素
        print(list01)
        
        # 左侧定位2个元素    右侧存储2个数据
        list01[-2:] = ["师傅", "老沙"]  # 修改列表最后两个元素 [遍历右侧数据,依次存入左侧定位的区域]
        ```

   4. 删除元素：

      列表名.remove(元素) 

      ```python
      # 根据元素
      if "法海" in list01:
      	list01.remove("法海")  # 内部会从头到尾搜索第一个满足条件的元素,有则删除没则抛出异常
      ```

      del 列表名[索引或切片]

      ```python
      # 根据索引/切片
      del list01[-1]
      del list01[:]
      ```

   5. 正向获取列表所有元素

      ```python
      for item in list02:
      	print(item)
      ```

   6. 反向获取列表所有元素

      ```python
      for i in range(len(list02)-1,-1,-1):
          print(list02[i])
      ```

   7. 二维列表

      ```python
      # 二维列表
      list01 = [
          [1, 2, 3, 4],
          [5, 6, 7, 8],
          [9, 10, 11, 12],
      ]
      
      # 1. 通过二维列表打印7/10/12
      print(list01[1][2])
      print(list01[2][1])
      print(list01[2][3])
      
      # 2. 循环打印第一行数据(一行一个)
      for item in list01[0]:
          print(item)
          
      # 3. 循环打印第三列数据(一行一个)
      for r in range(len(list01)):
          print(list01[r][2])
          
      # 4. 从右到左打印第二行数据(一行一个)
      for c in range(len(list01[1]) - 1, -1, -1):  # 3210
          print(list01[1][c])
          
      # 5. 从下到上打印第四列数据(一行一个)
      for r in range(len(list01) - 1, - 1, - 1):
          print(list01[r][3])
          
      # 6. 将二维列表以表格形状打印到终端中
      for line in list01:
          for element in line:
              print(element, end=" ")
          print()
      ```

      

### 2、元组 (tuple)

1. 定义

   由一系列变量组成的**不可变**序列容器

   不可变是指一但创建，不可以再添加/删除/修改元素

2. 基础操作

   1. 创建空元组：

      ​	元组名 = ()

      ​	元组名 = tuple()

      ```python
      # 创建
      tuple01 = ()
      tuple01 = ("悟空", "唐僧")
      
      tuple02 = tuple()
      list02 = ["北京", "上海"]
      tuple02 = tuple(list02)  # list预留空间 --> tuple按需分配
      
      # 如果元组中只有一个元素,必须最后加逗号
      tuple03 = (10) # int
      print(type(tuple03))
      
      tuple03 = (10,) # tuple
      print(type(tuple03))
      
      tuple03 = ("a") # str
      print(type(tuple03))
      
      tuple03 = ("a",) # tuple
      print(type(tuple03))  
      ```

   2. 获取元素：定位

      ​	变量 = 元组名[索引]

      ​	变量 = 元组名[切片] # 赋值给变量的是切片所创建的新列表  

      ```python
      print(tuple01[0])
      print(tuple01[:])  # 通过切片获取元素,会创建新元组
      ```

   3. 遍历元组：

      ​	正向：

      ​		for 变量名 in 列表名:

      ​			变量名就是元素

      ​	反向：

      ​		for 索引名 in range(len(列表名)-1,-1,-1):

      ​			元组名[索引名]就是元素

      ```python
      # 正向获取元组所有元素
      for item in tuple01:
          print(item)
          
      # 反向获取元组所有元素
      for i in range(len(tuple01) - 1, -1, -1):
          print(tuple01[i])
      ```

### 3、字典{dict}

1. 定义：

   - 由一系列键值对组成的**可变散列**容器。

   - 散列：对键进行哈希运算，确定在内存中的存储位置，每条数据存储无先后顺序。

   - 键必须惟一且不可变(字符串/数字/元组)，值没有限制。

2. 基础操作：

   1. 创建字典：

      ​	字典名 = {键1（key）：值（value）1，键2：值2}

      ​	字典名 = dict (可迭代对象) 

      ```python
      # 字典名 = {键1：值1，键2：值2}
      dict01 = {10001: "美队", 10002: "钢铁侠", 10003: "绿巨人"}
      print(dict01)
      
      # 字典名 = dict(可迭代对象) 
      list02 = [(10010, "灭霸"), (10011, "星云"), (10012, "乌木喉")]
      dict02 = dict(list02)
      print(dict02)
      ```

   2. 添加/修改元素：

      语法:

      ​	字典名[键] = 数据

      说明:

      ​	键不存在，创建记录。键存在，修改值。

      ```python
      # 字典不存在该key，则创建键值对
      if 10004 not in dict01:
          dict01[10004] = "雷神"
      print(dict01)
      
      # 字典存在该key，则修改该键的值
      if 10003 in dict01:
          dict01[10003] = "奇异博士"
      print(dict01)
      ```

   3. 获取元素：

      ​	变量 = 字典名[键]  

      ​	键不存在，则报错

      ```python
      # 变量 = 字典名[键]
      item01 = dict01[10004]
      print(item01)
      
      # 键不存在，则报错
      print(dict01(10005))
      ```

   4. 遍历字典：

      - for 键名 in 字典名:

      ​		字典名[键名]

      ```python
      # 遍历所有键
      for key in dict01:
          print(key)
          print(dict01[key])
          
      # 遍历所有值
      for value in dict01.values():
          print(value)
      ```

      - for 键名,值名 in 字典名.items():

      ​		语句

      ```python
      # 遍历所有key,value（两种方法）
      for item in dict01.items():
      	print(item[0])
      	print(item[1])
      	
      for k,v in dict01.items():
          print(k)
          print(v)
      ```

   5. 删除元素：

      ​	del 字典名[键]

      ```python
      # 删除元素
      del dict01[10002]
      ```

### 4、集合(set)

1. 定义：

   - 由一系列**不重复的不可变**类型变量(元组/数/字符串)组成的**可变散列**容器

   - 相当于只有键没有值的字典(键则是集合的数据)

2. 作用：

   1. 去重复值
   2. 数学运算

## 三、模块Module

- 包含一系列数据、函数、类的文件，通常以.py结尾

- 让一些相关的数据，函数，类有逻辑的组织在一起，使逻辑结构更加清晰。有利于多人合作开发

#### 导入

**导入方式一：**import

1. 语法： 

   ​	import 模块名

   ​	import 模块名 as 别名

2. 作用：将某模块整体导入到当前模块中

3. 使用：模块名.成员

4. 适用性：面向过程（全局变量，函数）

**导入方式二：**from ... import...

1. 语法：from 模块名 import 成员名[ as 别名1]
2. 作用：将模块内的一个或多个成员导入到当前模块的作用域中

3. 使用：直接使用成员名

4. 适用性：面向对象（类）导入一个

**导入方式三：**from... import ...

1. 语法：from 模块名 import  *

2. 作用：将某模块的所有成员导入到当前模块

3. 模块中以下划线(_)开头的属性，不会被导入，通常称这些成员为隐藏成员

4. 适用性：面向对象（类）导入多个，导入的多个模块成员容易发生冲突

#### 加载过程

​	在模块导入时，模块的所有语句会执行。

​	如果一个模块已经导入，则再次导入时不会重新执行模块内的语句

#### 分类

1. 内置模块(builtins)，在解析器的内部可以直接使用

2. 标准库模块，安装Python时已安装且可直接使用

3. 第三方模块（通常为开源），需要自己安装

4. 用户自己编写的模块（可以作为其他人的第三方模块）

## 四、文件操作

### open() 方法

open() 方法用于打开一个文件，并返回文件对象，在对文件进行处理过程都需要使用到这个函数，如果该文件无法被打开，会抛出 OSError。

**注意：**使用 open() 方法一定要保证关闭文件对象，即调用 close() 方法。

open() 函数常用形式是接收两个参数：文件名(file)和模式(mode)。

```python
open(file, mode='r', buffering=-1, encoding=None, errors=None, newline=None, closefd=True, opener=None)
```

```python
with open() as 别名:
```

参数说明:

| 参数      | 说明                                                       |
| --------- | ---------------------------------------------------------- |
| file      | 必需，文件路径（相对或者绝对路径）                         |
| mode      | 文件打开模式                                               |
| buffering | 设置缓冲                                                   |
| encoding  | 编码方式，一般使用utf8                                     |
| errors    | 报错级别                                                   |
| newline   | 区分换行符                                                 |
| closefd   | 传入的file参数类型                                         |
| opener    | 设置自定义开启器，开启器的返回值必须是一个打开的文件描述符 |

mode 参数有:

| 模式 | 描述                                                         |
| :--- | :----------------------------------------------------------- |
| t    | 文本模式 (默认)。                                            |
| x    | 写模式，新建一个文件，如果该文件已存在则会报错。             |
| b    | 二进制模式。                                                 |
| +    | 打开一个文件进行更新(可读可写)。                             |
| U    | 通用换行模式（不推荐）。                                     |
| r    | 以只读方式打开文件。文件的指针将会放在文件的开头。这是默认模式。 |
| rb   | 以二进制格式打开一个文件用于只读。文件指针将会放在文件的开头。这是默认模式。一般用于非文本文件如图片等。 |
| r+   | 打开一个文件用于读写。文件指针将会放在文件的开头。           |
| rb+  | 以二进制格式打开一个文件用于读写。文件指针将会放在文件的开头。一般用于非文本文件如图片等。 |
| w    | 打开一个文件只用于写入。如果该文件已存在则打开文件，并从开头开始编辑，即原有内容会被删除。如果该文件不存在，创建新文件。 |
| wb   | 以二进制格式打开一个文件只用于写入。如果该文件已存在则打开文件，并从开头开始编辑，即原有内容会被删除。如果该文件不存在，创建新文件。一般用于非文本文件如图片等。 |
| w+   | 打开一个文件用于读写。如果该文件已存在则打开文件，并从开头开始编辑，即原有内容会被删除。如果该文件不存在，创建新文件。 |
| wb+  | 以二进制格式打开一个文件用于读写。如果该文件已存在则打开文件，并从开头开始编辑，即原有内容会被删除。如果该文件不存在，创建新文件。一般用于非文本文件如图片等。 |
| a    | 打开一个文件用于追加。如果该文件已存在，文件指针将会放在文件的结尾。也就是说，新的内容将会被写入到已有内容之后。如果该文件不存在，创建新文件进行写入。 |
| ab   | 以二进制格式打开一个文件用于追加。如果该文件已存在，文件指针将会放在文件的结尾。也就是说，新的内容将会被写入到已有内容之后。如果该文件不存在，创建新文件进行写入。 |
| a+   | 打开一个文件用于读写。如果该文件已存在，文件指针将会放在文件的结尾。文件打开时会是追加模式。如果该文件不存在，创建新文件用于读写。 |
| ab+  | 以二进制格式打开一个文件用于追加。如果该文件已存在，文件指针将会放在文件的结尾。如果该文件不存在，创建新文件用于读写。 |

默认为文本模式，如果要以二进制模式打开，加上 **b**

### file 对象

| 方法                      | 描述                                                         |
| :------------------------ | :----------------------------------------------------------- |
| file.close()              | 关闭文件。关闭后文件不能再进行读写操作。                     |
| file.flush()              | 刷新文件内部缓冲，直接把内部缓冲区的数据立刻写入文件, 而不是被动的等待输出缓冲区写入。 |
| file.fileno()             | 返回一个整型的文件描述符(file descriptor FD 整型), 可以用在如os模块的read方法等一些底层操作上。 |
| file.isatty()             | 如果文件连接到一个终端设备返回 True，否则返回 False。        |
| file.next()               | 返回文件下一行。                                             |
| file.read(size)           | 从文件读取指定的字节数，如果未给定或为负则读取所有。         |
| file.readline(size)       | 读取整行，包括 "\n" 字符。                                   |
| file.readlines            | 读取所有行并返回列表，若给定sizeint>0，则是设置一次读多少字节，这是为了减轻读取压力。 |
| file.seek(offset,whser)   | 设置文件当前位置                                             |
| file.tell()               | 返回文件当前位置。                                           |
| file.truncate(sieze)      | 截取文件，截取的字节通过size指定，默认为当前文件位置。       |
| file.write(str)           | 将字符串写入文件，返回的是写入的字符长度。                   |
| file.writelines(sequence) | 向文件写入一个序列字符串列表，如果需要换行则要自己加入每行的换行符。 |

## 五、异常处理

### 异常

1. 定义：运行时检测到的错误。

2. 现象：当异常发生时，程序不会再向下执行，而转到函数的调用语句。

3. 常见异常类型：

-- 名称异常(NameError)：变量未定义。

``` python
print(qtx) # NameError
```

-- 类型异常(TypeError)：不同类型数据进行运算。

```python
print("成绩："+ 100) # TypeError
```

 

-- 索引异常(IndexError)：超出索引范围。

```python
list01 = [1,2,3]
print(list01[5])# IndexError
```

-- 属性异常(AttributeError)：对象没有对应名称的属性。

```python
class Wife:
	pass
	w01  = Wife()
	print(w01.name)# AttributeError
```

 

-- 键异常(KeyError)：没有对应名称的键。

 

-- 为实现异常(NotImplementedError)：尚未实现的方法。

 

-- 异常基类Exception。

 

### 处理

1. 语法：

try:

  可能触发异常的语句

except 错误类型1 [as 变量1]：

  处理语句1

except 错误类型2 [as 变量2]：

  处理语句2

except Exception [as 变量3]：

  不是以上错误类型的处理语句

else:

  未发生异常的语句

finally:

无论是否发生异常的语句

 

2. 作用：将程序由异常状态转为正常流程。

3. 说明：

   as 子句是用于绑定错误对象的变量，可以省略

   except子句可以有一个或多个，用来捕获某种类型的错误。

   else子句最多只能有一个。

   finally子句最多只能有一个，如果没有except子句，必须存在。

   如果异常没有被捕获到，会向上层(调用处)继续传递，直到程序终止运行。

```python
# 写法1：官方建议
def div_apple(apple_count):
    try:
        person_count = int(input("请输入人数："))  # ValueError
        result = apple_count // person_count  # ZeroDivisionError
        print("每人分%d个苹果" % result)
    except ValueError as  e:  # 通过as获取异常对象ValueError
        print("应该输入整数")
        print(e.args)  # 获取异常对象实例变量
    except ZeroDivisionError:
        print("不能输入0")
 
# 写法2：江湖习惯
def div_apple(apple_count):
    try:
        person_count = int(input("请输入人数："))# ValueError
        result = apple_count // person_count # ZeroDivisionError
        print("每人分%d个苹果" % result)
    # except Exception:
    except:
        print("出错啦")

# 写法3：except .. else
def div_apple(apple_count):
    try:
        person_count = int(input("请输入人数："))# ValueError
        result = apple_count // person_count # ZeroDivisionError
        print("每人分%d个苹果" % result)
    # except Exception:
    except:
        print("出错啦")
    else:
        print("顺利分完了苹果")

# 写法4：try .. finally
def div_apple(apple_count):
    try:
        person_count = int(input("请输入人数："))# ValueError
        result = apple_count // person_count # ZeroDivisionError
        print("每人分%d个苹果" % result)
    # except Exception:
    except:
        print("出错啦")
    finally:# 经常处理收尾工作(一定要做的)
        print("分苹果结束")
div_apple(10)
print("后续逻辑..")
```

