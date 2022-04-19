[TOC]

## Python3 基础语法

### 注释

给人看的，通常是对代码的描述信息，不执行。

1.**单行**注释以# 开头，快捷键：ctrl + /

```python
# 第一个注释
print ("Hello, Python!") # 第二个注释
```

**2.多行**注释可以用三引号开头，三引号结尾。''' '''或""" """

```python
# 第一个注释
# 第二个注释
 
'''
第三注释
第四注释
'''
 
"""
第五注释
第六注释
"""
print ("Hello, Python!")
```



### 行与缩进

python最具特色的就是使用缩进来表示代码块，不需要使用大括号 **{}** 。

缩进的空格数是可变的，但是同一个代码块的语句必须包含相同的缩进空格数。

一个Tab键=四个空格

```python
# 缩进示例：
if True:
    print("True")
else:
    print("False")
    
# 缩进错误时会报错：
if True:
    print("Answer")
    print("True")
else:
    print("Answer")
  print("False")    # 缩进不一致，会导致运行错误
```

```python
# 报错代码：

```



### 多行语句

Python 通常是一行写完一条语句，但如果语句很长，我们可以使用反斜杠\来实现多行语句

```python
total = item_one + \
        item_two + \
        item_three
```



### 变量

1. 定义：关联一个对象的标识符。

2. 命名规则：

   ​	必须是字母或下划线开头，后跟字母、数字、下划线。

      不能使用**关键字**(蓝色)，否则发生语法错误：SyntaxError: invalid syntax。

   ​        **备注：**保留字即关键字，我们不能把它们用作任何标识符名称。

   Python 的标准库提供了一个 keyword 模块，可以输出当前版本的所有关键字：

   ```python
   import keyword # 导入模块
   
   keyword.kwlist # 输入
   
   # 输出结果
   ['False', 'None', 'True', 'and', 'as', 'assert', 'async', 'await', 'break', 'class', 'continue', 'def', 'del', 'elif', 'else', 'except', 'finally', 'for', 'from', 'global', 'if', 'import', 'in', 'is', 'lambda', 'nonlocal', 'not', 'or', 'pass', 'raise', 'return', 'try', 'while', 'with', 'yield']
   ```

3. 建议命名：字母小写，多个单词以下划线隔开。

​          class_name

4. 赋值：创建一个变量或改变一个变量关联的数据。

5. 语法：

   赋值号**“=”**：将右边的结果赋值到左边

​       变量名 = 数据

​       变量名1 = 变量名2 = 数据

​       变量名1, 变量名2, = 数据1, 数据2

```python
# 创建单个变量
person_name01 = "白素贞" # (变量名 = 数据)
print(person_name01)

# 用单个数据，创建多个变量
person_name04 = person_name05 = "法海" # (变量名1 = 变量名2 = 数据)
print(person_name04,person_name05)

# 用多个数据，创建多个变量
person_name02, person_name03 = "许仙", "小青" # (变量名1, 变量名2 = 数据1, 数据2)
print(person_name02)
print(person_name03)

# del语句，删除变量
del person_name04
del person_name01,person_name02
print(person_name04) # 会有什么反映？

# 变量相加
person_name06 = person_name05 + person_name05
print(person_name06) # 字符串拼接
```



### 函数(function)

- 定义：函数是组织好的，可重复使用的，用来实现单一，或相关联功能的代码段。

  ​	   函数能提高应用的模块性，和代码的重复利用率。只要有小括号的就是函数。

  Python提供了许多内建函数：

  ```python
  print() 
  # 作用：将括号中的内容显示在控制台中
  # 字面意思：打印（内容）
  # 适用性：显示结果
  print(“hello world”) #将括号中的内容显示输出到终端中
  
  input()
  # 变量 = input(“需要显示的内容”) 作用：将用户输入的内容赋值给变量
  # 字面意思：结果=输人（内容）
  # 作用：将用户在终端中录入的信息存储到程序中（结果）
  # 适用性：输入内容
  name = input(“请输入姓名：”)
  print(“你好：”+ name)
  ```

  

### del 语句

1. 语法: 

   del 变量名1, 变量名2

2. 作用：

   用于删除变量,同时解除与对象的关联.如果可能则释放对象。

3. 自动化内存管理的引用计数：

   每个对象记录被变量绑定(引用)的数量,当为0时被销毁。



## Python核心数据类型

### 数值(Number)类型

**1、数字的三种类型：整数、浮点数和复数。**

- **int** (整数)

  - 表示整数，包含正数、负数、0。

    如： -5, 100, 0

    ```python
    number01 = 250
    print(number01 +1) # 数字计算251
    ```

- **float** (浮点数), 如 1.23、123e-2

  ```python
  number02 = 1.23
  print(number02)
  print(type(number02)) # type()函数，判断变量所指向的数据类型
  
  # 科学计数法
  number03 = 123e-2
  print(number03)
  number04 = 0.00001
  print(number04) # 1e-05
  ```

- **complex** (复数), 如 1 + 2j、 1.1 + 2.2j

  - 用的极少，知道就可以



**2、数字类型的转换**

- **int(x)** 将x转换为一个整数。
- **float(x)** 将x转换到一个浮点数。
- **complex(x)** 将x转换到一个复数，实数部分为 x，虚数部分为 0。
- **complex(x, y)** 将 x 和 y 转换到一个复数，实数部分为 x，虚数部分为 y。x 和 y 是数字表达式。
- **语法：**结果 = 类型名称函数(待转换数据)

```python
a = 1.0
print(a,type(a))
# 输出
1.0 <class 'float'>

# int()函数将a转换为整型
print(int(a),type(int(a)))
# 输出
1 <class 'int'>
```

```python
# 练习
print(int(8.93)) # 输出什么？
print(float(100)) # 输出什么？
```

**3.数学函数**

**round()函数**

```python
# 四舍五入保留指定精度
# 语法：结果 = round(需要计算的小数,精度)，精度就是保留几位小数的意思
print(round(1.29, 1))  # 1.3
print(round(1.21, 1))  # 1.2
```

**max()**:最大值

**min()**:最小值

**abs()**:绝对值

以下3个函数先了解，后期机器学习中会用到

**random():**随机生成下一个实数

**shuffle():**将序列的所有元素随机排序

**seed():**改变随机数生成器的种子seed

**其他函数参考菜鸟教程：**https://www.runoob.com/python3/python3-number.html



### 字符串(String)

- 是用来记录文本信息(文字信息)

- 需要加单引号或双引号

  ```python
  # 字符串拼接
  name01 = '250'
  print(name01 + '1') # 运行后返回什么？
  
  name02 = '齐天大圣'
  print(type(name02)) # 运行后返回什么？
  ```

- 字符串转换为整数

  ```python
  # int()函数
  str_number = "250"
  int_number = int(str_number)
  print(int_number,type(int_number))
  
  # 注意：待转换数据必须"长得像"代转类型
  print(int("250+")) # 250+ 不像整数,所以报错
  print(int("1.23")) 
  # ValueError: invalid literal for int() with base 10: '1.23'
  ```

  ```python
  # str()函数
  int_number = 251
  str_number = str(int_number)
  print(str_number,type(str_number))
  # 251 <class 'str'>
  ```

- 字符串运算符

  | **操作符** | **描述**       | **实例**                                     |
  | ---------- | -------------- | -------------------------------------------- |
  | +          | 字符串连接     | a + b 输出结果： HelloPython                 |
  | *          | 重复输出字符串 | a*2 输出结果：HelloHello                     |
  | %          | 格式字符串     | print ("我叫 %s 今年 %d 岁!" % ('小明', 10)) |

  ```python
  # 字符串连接，重复
  a = "Hello"
  b = "Python"
   
  print("a + b 输出结果：", a + b)
  print("a * 2 输出结果：", a * 2)
  
  # 格式字符串(传统方法)
  print ("我叫 %s 今年 %d 岁!" % ('小明', 10))
  
  # %s 格式化字符串
  # %d 格式化整数
  # %f 格式化浮点数字，可指定小数点后的精度(%.2f)精确到两位小数
  
  # .format()格式化输出
  # .format():把传统的%替换为{}来实现格式化输出
  print('数字{}{}和{}'.format("123",456,'789'))
  ```

-  字符串的常见操作

  **1. find** 

  检测字符串(str) 是否包含在目标字符串中，如果存在返回开始的索引值，否则返回**-1** 

  ```python
  mystr.find(str, start=0, end=len(mystr))
  
  # 例题：
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
  
  # 例题：
  mystr = 'hello world kkb' 
  mystr.index("ab") 
  # 运行结果:控制台会直接报错(Vale Error:substring not found)
  ```

  **3. count** 

  返回 str 在start和end之间 在 mystr里面出现的次数 

  ```python
  mystr.count(str, start=0, end=len(mystr))
  
  # 例题：
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

  检查字符串是否是以 hello 开头, 是则返回 True ，否则返回 False 

  ```python
  mystr.startswith(hello) 
  ```

  **9. endswith** 

  检查字符串是否以 obj 结束，如果是返回 True ,否则返回 False . 

  ```python
  mystr.endswith(obj) 
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
  list_result = []  # 可变
  for itme in range(10):
      # 像列表中添加当前字符串的地址
      list_result.append(str(itme))
  str_result = "".join(list_result)
  print(str_result)
  print(type(str_result))
  ```
  
  

### bool(布尔)

-  True(真)，False(假)

- 1(真)，0(假)

  ```python
  a = 1
  b = 2
  c = a + b
  
  print(c) # 3
  print(c == 3) # True
  print(int(c == 3)) # 1
  
  d = c == 4
  print(d, type(d)) # False <class 'bool'>
  print(int(d)) # 0
  ```

  **转换为布尔:bool(数据)**

  ```python
  bool(0) 
  bool(0.0)  
  bool(None)
  # 结果为False
  
  ```

  

### 空值对象 (None)

1. 表示不存在的特殊对象。

2. 作用：占位和解除与对象的关联。

   ```python
   age =
   age = ''
   age = None
   print(age) # 分别输出什么？
   
   # 解除与变量的绑定关系
   person_name = '小青'
   print(person_name)
   
   person_name = None
   print(person_name) #输出什么？
   ```



### 常⽤的数据类型转换

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



## Python运算符

### 比较运算符

| 比较运算符 | 含义     |
| :--------- | :------- |
| <          | 小于     |
| <=         | 小于等于 |
| >          | 大于     |
| >=         | 大于等于 |
| ==         | 等于     |
| !=         | 不等于   |

返回值为布尔类型的值

比较运算的数学表示方式:0 <= x <= 100

### 算术运算符

（优先级从高到低排列）

| 算术运算符 | 含义   |
| ---------- | ------ |
| ()         | 小括号 |
| **         | 幂运算 |
| *          | 乘法   |
| /          | 除法   |
| %          | 求余   |
| //         | 整除   |
| +          | 加法   |
| -          | 减法   |

**语法：**

- 数字 + 数字 --> 数学运算
- 字符串 + 字符串 --> 字符拼接
- 字符串 + 数字 --> 报错

```python
# 数值型练习：
number01 = 10
number02 = 4

print(number01 + number02)
print(number01 - number02)
print(number01 * number02)
print(number01 / number02)
print(number01 ** number02)
print(number01 // number02)
print(number01 % number02)
```

```python
# 字符串拼接练习：
number01 = '10'
number02 = '4'

print(number01 + number02)
print(number01 - number02) # TypeError: unsupported operand type(s) for -: 'str' and 'str'
```

```python
# 字符串+数字拼接：
number01 = '10'
number02 = 4

print(number01 + number02) # ？
```



### 增强运算符

| 增强运算符 | 含义              |
| ---------- | ----------------- |
| y += x     | y = y + x（累加） |
| y -= x     | y = y - x         |
| y *= x     | y = y * x         |
| y /= x     | y = y / x         |
| y //= x    | y = y // x        |
| y %= x     | y = y % x         |
| y **= x    | y = y ** x        |

```python
# 累加
number03 = 5
number03 += 5
print(number03) # 10

# 其他运算符自己尝试
```

### 逻辑运算符

判断两个命题之间的关系

**1.与(and)**

​	表示并且的关系，一假俱假。表达：必须都得满足。

​	示例:

```python
print(True and True)  # True
print(False and True)  # False
print(True and False)  # False
print(False and False)  # False
```

**2.或or**

​	表示或者的关系，一真俱真。表达：有一个满足就行。

​	示例:

```python
print(True or True)  # True
print(False or True)  # True
print(True or False)  # True
print(False or False)  # False
```

**3.非 not **

​	表示取反

​	示例:

```python
print(not True)
print(not False)
```

 **4.短路运算**(if条件语句讲完后再讲)

​	短路逻辑：一但结果确定，后面的语句将不再执行。

​	False and  ?-->false   

​	True  or ? -->true

​	价值：尽量把耗时的判断放在后面，因为很有可能不执行。优化内存和cpu节约资源



### 成员运算符

成员运算符：测试实例中包含了一系列的成员，包括字符串，列表或元组。

| **运算符** | **描述**                                                | **实例**                                          |
| ---------- | ------------------------------------------------------- | ------------------------------------------------- |
| in         | 如果在指定的序列中找到值返回 True，否则返回 False。     | x 在 y 序列中 , 如果 x 在 y 序列中返回 True。     |
| not in     | 如果在指定的序列中没有找到值返回 True，否则返回 False。 | x 不在 y 序列中 , 如果 x 不在 y 序列中返回 True。 |

### 身份运算符

身份运算符用于比较两个对象的存储单元

| 运算符 | 描述                                        | 实例                                                         |
| ------ | ------------------------------------------- | ------------------------------------------------------------ |
| is     | is 是判断两个标识符是不是引用自一个对象     | **x is y**, 类似 **id(x) == id(y)** , 如果引用的是同一个对象则返回 True，否则返回 False |
| is not | is not 是判断两个标识符是不是引用自不同对象 | **x is not y** ， 类似 **id(a) != id(b)**。如果引用的不是同一个对象则返回结果 True，否则返回 False。 |

### **优先级**

高到低：

1. 算数运算符
2. 比较运算
3. 增强运算符
4. 身份运算符
5. 逻辑运算符



### 索引(index)

1. 作用：定位单个容器元素

2. 语法：容器[整数]

3. 说明：

   ​	正向索引从0开始，第二个索引为1，最后一个为len(s)-1。

   ​	反向索引从-1开始,-1代表最后一个,-2代表倒数第二个,以此类推,第一个是-len(s)。

```python
message = "我是齐天大圣孙悟空"
print(message[1]) # 打印第二个字符
print(message[-3]) # 打印倒数第三个字符

print(message[99]) # IndexError: string index out of range
print(message[-99]) # IndexError: string index out of range
```

### 切片(slice)

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
message = "我是齐天大圣孙悟空"
print(message[2:5:1])  # ?
print(message[:5]) # ?
print(message[:]) # ?
print(message[::2]) # ?
print(message[1:-3])  # ?
print(message[::-1])  # ?
print(message[-4:1:-1])  # ?
print(message[:99])  # ?
print(message[:-99:-1])  # ?
print(message[3:1:])  # ?
print(message[1:1])  # ?
```



## Python语句

### **行**

1. 物理行：程序员编写代码的行。

2. 逻辑行：python解释器需要执行的指令。

3. 建议一个逻辑行在一个物理行上。

   ```python
   # 3个物理行对应3个逻辑行(建议)
   a = 10
   b = 20
   c = a + b
   ```

4. 如果一个物理行中使用多个逻辑行，需要使用分号；隔开。

   ```python
   # 1个物理行对应3个逻辑行(不建议)
   a = 10;b = 20;c = a + b
   ```

5.  如果逻辑行过长，可以使用隐式换行或显式换行。

    隐式换行：所有括号的内容换行,称为隐式换行,括号包括:  ()  []   {} 三种  是天然的换行符

    显式换行：通过折行符 \ (反斜杠)换行，必须放在一行的末尾，目的是告诉解释器,下一行也是本行的语句。 

   ```python
   # 隐式换行
   b = (1 + 2 +
        3 + 4 +
        5 + 6)
   
   # 显式换行
   a = 1 + 2 + \                              
       3 + 4 + \
       5 + 6
   ```



### 选择语句

**If elif else 语句**

1. **作用:**

​    	运行时,根据某些条件决定是否执行语句

2. **语法:**

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
- 如果 "condition_2" 为False，将执行"statement_block_3"块语句

3. **说明:**

   elif 子句可以有0个或多个。

   else 子句可以有0个或1个，且只能放在if语句的最后。

   缩进：4个空格（在专业开发工具中，使用1个tab快捷键=4个空格）

4. **注意：**

   - 每个条件后面要使用冒号 **:**，表示接下来是满足条件后要执行的语句块。

   - 使用缩进来划分语句块，相同缩进数的语句在一起组成一个语句块。

5. **实例：**

   ```python
   sex = input("请输入性别：")
   if sex == "男":
       print("您好,先生！")
   # 否则如果
   elif sex == "女":
       print("您好,女士！")
   # 否则
   else:
       print("性别未知")
   ```

6. **比较：**

   全部用if判断的需要逐一判断，用if-elif 的判断符合条件后后面的elif就不执行了

   ```python
   """
   练习：
       智商IQ = 心理年龄MA / 实际年龄CA * 100
       天才：140以上（包含）# >=
       超常：120-139之间（包含）
       聪慧：110-119之间（包含）
       正常：90-109之间（包含）
       迟钝：80-89之间（包含）
       低能：80以下
       根据心理年龄与实际年龄，打印智商等级
   """
   MA = int(input("请输入您的心理年龄:"))
   CA = int(input("请输入您的实际年龄:"))
   IQ = round(MA / CA * 100)
   if IQ >= 140:
       print("恭喜您，您是个天才！")
   elif IQ >= 120:   # 因为有elif,其中el表达以上条件不满足(IQ >=140),所以不用区间判断(IQ <=139)
       print("您的智商超过常人")
   elif IQ >= 110:
       print("您很聪明")
   elif IQ >= 90:
       print("您是个正常人")
   elif IQ >= 80:
       print("抱歉的告诉您，您反映有点迟钝")
   else:
       print("抱歉的告诉您，您是个傻雕")
   ```

#### 条件表达式：

​	语法：变量 = 结果1 if 条件 else 结果2

​	作用：根据条件(True/False) 来决定返回结果1还是结果2。

   if 100:

​        print("真值")

等同于

if bool(100):

​      print("真值")

```python
#练习：
if input("请输入性别：") == "男":
    sex_value = 1
else:
    sex_value = 0

# 条件表达式写法：
sex_value = 1 if input("请输入性别：") == "男" else 0

#练习：在终端中录入一个整数,如果奇数为变量state赋值"奇数"
      #否则赋值"偶数"
number = "奇数" if int(input("请输入一个整数:")) % 2  else "偶数"
print(number)

#练习：在终端中录入一个年份,如果闰年为变量day赋值29
      #否则赋值"28
year = int(input("请输入一个年份："))
day = 29 if year % 4 == 0 and year % 100 != 0 or year % 400 ==0 else 28
print(day)

#练习：
    #北京一日游的收费标准：
        #5人以内按照散客标准，300元/人
        #超过5人按照团体标准，280元/人
    #根据人数,计算旅游费用:
money = people_number * 300 if people_number <= 5 else people_number * 280
if money > 0:
     print(money)
else:
     print("捣乱呢?")

```



### 循环语句

#### while循环

1. **作用: **

   可以让一段代码满足条件，重复执行。

2. **语法:**

   while 条件:

   ​        循环体或满足条件执行的语句

   else:

   ​        不满足条件执行的语句

   **备注：**while 循环的else语句作用：判断while循环退出原因,是在循环条件还是在循环体

3. **说明:**

   else子句可以省略

   在循环体内用break终止循环时,else子句不执行

4. **循环计数三大要素：**开始值、结束值、增减量

   ```python
   # 在循环以前定义计数器（开始值）
   count = 0
   # 根据计数器判断循环条件（结束值）
   while count < 5:
       print("您已经跑了{}圈".format(count))
   # 在循环以内更新计数器(增减量)
       count += 1
   print("您总共跑了{}圈".format(count))
   ```

5. **无限循环**

   可以通过设置条件表达式永远不为 False 来实现无限循环

   ```python
   count = 1
   while count == 1:  # 表达式永远为 true
       num = int(input("输入一个数字:"))
       print("您输入的数字是:", num)
      
   # 可以使用 CTRL+C 来退出当前的无限循环
   ```

6. **练习**

   ```python
   """
       猜数字
           程序产生1个,1--100之间的随机数.
           让玩家重复猜测,直到猜对为止
           每次提示：大了，小了，恭喜猜对了,总共猜了?次.
   
   # 准备随机数工具
   import random
   
   # 产生随机数
   print(random.randint(1,100))
   print(random.randint(1,100))
   print(random.randint(1,100))
   """
   
   # 准备随机数工具
   import random
   
   # 产生随机数
   random_number = random.randint(1, 100)
   
   count = 0
   while True:
       count += 1
       input_number = int(input("请输入要猜的数字（1-100）："))
       if input_number > random_number:
           print("猜大了！")
       elif input_number < random_number:
           print("猜小了！")
       else:
           print("猜对了猜了" + str(count) + "！")
           break
   
   ```

#### for循环

1. **作用:**

   ​    用来遍历可迭代对象的数据元素。可迭代对象是指能依次获取数据元素的对象，例如：容器类型。

2. **语法:**

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

3. **说明:**

   ​    else子句可以省略

   ​    在循环体内用break终止循环时,else子句不执行

4. **range()函数：**

   需要遍历数字序列，可以使用内置range()函数，它会生成数列

   1. 作用:

      ​	用来创建一个生成一系列整数的可迭代对象(也叫整数序列生成器)。

   2. 语法:

      ​	range(开始值，结束值，间隔)   range(1 , 10 , 1）

   3. 说明:

      ​	函数返回的可迭代对象可以用for取出其中的元素

      ​	返回的数字不包含结束点（左闭右开）

      ​	开始点默认为0

      ​	间隔默认值为1 

   ```python
   # 生成0~4的整数
   for i in range(5):
   	print(i)
       
   # 生成1~15（不包含15）间隔为3
   for i in range(1，15，3):
   	print(i)
   ```

5. ### For for循环嵌套

   ```python
   # 3行5列的表格
   for r in range(3):  # 外层循环做一次   ----- 控制行    0    1   2
       for c in range(5):  # 内层循环做多次 -----控制列01234/01234/01234
           print("*", end=" ")  # 在一行打印
       print()  # 换行
   ```

   

### 跳转语句

都只能用在循环之内

#### break 语句

1. 跳出循环体，后面的代码不再执行。

2. 可以让while语句的else部分不执行。

#### continue 语句

​	跳过本次，继续下次循环，跳到循环开始的地方

```python
# 需求：累加1--100之间所有能被3整除的数字的整数

# 如果满足条件则累加
sum_value = 0
for number in range(1, 101):
   if number % 3 == 0:
      print(number)
      sum_value += number
print(sum_value)

# 或者：如果不满足条件则继续
sum_value = 0
for number in range(1, 101):
    if number % 3 != 0:
        continue
    sum_value += number
print(sum_value)
```

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

## Python基本数据结构

序列中的每个元素都分配一个数字--它的位置，或索引，第一个索引是0，第二个索引是1，依此类推。

序列都可以进行的操作包括索引，切片，加，乘，检查成员。

Python有6个序列的内置类型，最常见的是列表和元组。

### 列表[list]

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

      列表名.append(元素) 

      列表.insert(索引，元素)

      ```python
      # 追加元素，追加后元素的位置？
      list01.append("沙僧")
      print(list01)
      ```

      ```python
      # 插入元素(需要存储数据的索引,元素)
      list01.insert(1, "小白龙")
      print(list01)
      ```

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
        print(list01)
        
        # 左侧定位0个元素    右侧存储3个数据
        list01[-2:-2] = ["白素贞", "许仙", "小青"]
        print(list01)
        
        # 左侧定位3个元素    右侧存储0个数据
        list01[:3] = []
        print(list01)
        
        # 左侧定位3个元素    右侧存储1个数据
        list01[1:4] = ["法海"]
        print(list01)
        
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

      

### 元组 (tuple)

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
      
      tuple03 = (10,) 
      print(type(tuple03))
      
      tuple03 = ("a") # str
      print(type(tuple03))
      
      tuple03 = ("a",)
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

### 字典{dict}

1. 定义：

   - 由一系列键值对组成的**可变散列**容器。

   - 散列：对键进行哈希运算，确定在内存中的存储位置，每条数据存储无先后顺序。

   - 键必须惟一且不可变(字符串/数字/元组)，值没有限制。

2. 基础操作：

   1. 创建字典：

      ​	字典名 = {键1：值1，键2：值2}

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

   5.  删除元素：

      ​	del 字典名[键]

      ```python
      # 删除元素
      del dict01[10002]
      ```

### 集合(set)

1. 定义：

   - 由一系列**不重复的不可变**类型变量(元组/数/字符串)组成的**可变散列**容器

   - 相当于只有键没有值的字典(键则是集合的数据)

2. 作用：

   1. 去重复值
   2. 数学运算

### 比较

#### 列表VS字符串

1. 列表和字符串都是**序列**,元素之间有先后顺序关系。

2. 字符串是**不可变**的序列,列表是**可变**的序列。

3. 字符串中每个元素**只能**存储**字符**,而列表可以存储**任意**类型。

4. 列表和字符串都是**可迭代**对象。

5. 函数：将多个字符串拼接为一个。result = "连接符".join(列表)

```python
"""
    list  -->  str

    字符串 = "连接符".join(列表)
"""

list_result = []  # 可变
for itme in range(10):
    # 像列表中添加当前字符串的地址
    list_result.append(str(itme))
str_result = "".join(list_result)
print(str_result)
```

```python
"""
    str -->  list

    列表 = “a-b-c-d”.split(“分隔符”)
"""

names = "齐天大圣-猪八戒-唐僧"
list_names = names.split("-")
print(list_names)

# 将一个字符串描述的多个信息分别提取出来(列表)
for item in list_names:
    print(item)
```

#### 字典 VS 列表

1. 都是**可变**容器。

2. 获取元素方式不同,列表用**索引**,字典用**键**。

3. 字典的插入,删除,修改的**速度**快于列表。

4. 列表的存储是**有序**的,字典的存储是**无序**的。
5. 总结：
       列表：
           优点：因为根据索引获取元素,所以查找更为灵活(第一个、最后一个...)
           缺点：查找速度不如字典快,根据索引查找代码可读性不高
           适用性：存储单一维度的数据(疫情信息)
       字典：
           优点：因为根据键获取元素,所以查找速度快、代码可读性高.
           缺点：获取元素不如列表灵活
           适用性：存储多个维度的数据(地区、新增、确诊、治愈)





## 自定义函数

你可以定义一个由自己想要功能的函数，以下是简单的规则：

- 函数代码块以 **def** 关键词开头，后接函数标识符名称和圆括号 **()**。

- 任何传入参数和自变量必须放在圆括号中间，圆括号之间可以用于定义参数。

- 函数的第一行语句可以选择性地使用文档字符串—用于存放函数说明。

- 函数内容以冒号起始，并且缩进。

- **return [表达式]** 结束函数，选择性地返回一个值给调用方。不带表达式的return相当于返回 None。

- 语法：Python 定义函数使用 def 关键字，一般格式如下：

  ```python
  # 函数制作
  def 函数名称(参数):
  	函数体
  	return 数据
  
  # 函数调用
  变量 = 函数名称(数据)
  ```

- 调用函数:

  1. 语法：函数名(实际参数) 
  2. 说明：根据形参传递内容

- 返回值:

  1. 定义：

     ​	函数执行后返回的结果。

  2. 语法：

     ​	return 数据 

  3. 说明：

     ​	return后没有语句，相当于返回 None

     ​	函数体没有return，相当于返回None

- 实例：

  ```python
  # 定义函数
  def hello() :
     print("Hello World!")
     
  # 调用函数
  hello()
  ```

  ```python
  # 定义一个带参数的函数
  # 函数功能：计算矩形面积函数
  def area(width, height):
      return width * height
  
  # 调用area()函数
  w = 4
  h = 5
  print("width =", w, " height =", h, " area =", area(w, h))
  ```

### lambda表达式

1. 定义：是一种匿名方法。

2. 作用：作为参数传递时语法简洁，优雅，代码可读性强。

   ​			随时创建和销毁，减少程序耦合度。

3. 语法

   定义：

   ​	变量 = lambda 形参: 方法体

   调用：

   ​      变量(实参)

4. 说明：

   形参没有可以不填

   方法体只能有一条语句，且不支持赋值语句。

   ```python
   # 有参数有返回值
   # 原始写法：
   def func01(p1, p2):
   	return p1 + p2
   print(func01(1, 2))
   # Lambda 表达式：
   func01 = lambda p1, p2: p1 + p2
   print(func01(1, 2))
   
   # 无参数有返回值
   # 原始写法：
   def func02():
   	return 1000
   print(func02())
   # Lambda 表达式：
   func02 = lambda: 1000
   print(func02())
   
   # 有参数无返回值
   # 原始写法：
   def func03(p1, p2):
   	print(p1 + p2)
   func03(1, 2)
   # Lambda 表达式：
   func03 = lambda p1, p2: print(p1 + p2)
   func03(1, 2)
   
   # 无参数无返回值
   # 原始写法：
   def func04():
   	print("中国加油,武汉加油")
   func04()
   # Lambda 表达式：
   func04 = lambda : print("中国加油,武汉加油")
   func04()
   
   # lambda 表达式不能赋值
   #原始写法：
   def func05(list_target):
       list_target[0] = 10
   list01 = [1]
   func05(list01)
   print(list01[0])  # 10
   # Lambda 表达式：
   func05 = lambda list_target : list_target[0] = 10
   
   # lambda 表达式只能有一句话
   #原始写法：
   def func06( ):
       for item in range(3):
           print(item)
   func06()
   # Lambda 表达式：
   func06 = lambda : for item in range(3):
   print(item)
   
   ```

### return语句

return语句[表达式]退出函数，选择性地向调用方返回一个表达式。

return后没有语句，相当于返回 None。

函数体没有return，相当于返回None。

return的两个作用

```python
#函数中return有两个作用
#1.返回函数执行的结果
def test1(a,b):
    print('......')
    return a+b
rs = test1(100,200)
print(rs)

#2.结束函数的执行
def test2(a):
    print('-----')
    if a == 10:
        return
    #return下方的代码就不会在执行了
    print('************')
test2(10)

#3.在函数中，返回多个值,返回的多个值，放在一个元组里
def test3():
    return 1,2,3,4,5,6,7,8,9
rs = test3()
print(rs)

```



## 函数参数

形式参数：自定义函数中的形参全称为"形式参数" 由于它不是实际存在变量，所以又称虚拟变量

​		   在定义函数名和函数体的时候使用的参数,目的是用来接收调用该函数时传入的参数

实际参数：在调用有参函数时，主调函数和被调函数之间有数据传递关系。

​		   在主调函数中调用一个函数时，函数名后面括号中的参数称为“实际参数”（简称“实参”）



### 实参传递方式argument

- 位置传参

  ​	定义：实参与形参的位置依次对应，根据位置(顺序)传递

  ​	作用：函数调用者给函数定义者

  传递信息的最常用方式

  ​	适用性：需要传递全部参数 

  ```python
  def func01(p1=0, p2=None, p3=0):
      print(p1) 
      print(p2)  
      print(p3)  
      
  func01(1, 2, 3)
  ```

- 序列传参

  ​	定义：实参用*将序列拆解后与形参的位置依次对应

  ​	序列实参：将序列拆分后按位置传递

  ​	作用： 使用容器思想封装参数

  ```python
  def func01(p1=0, p2=None, p3=0):
      print(p1)  
      print(p2)  
      print(p3)  
  
  list01 = [1, 2, 3]
  func01(*list01)
  ```

- 关键字传参

  ​	定义：实参根据形参的名字进行对应

  ​	关键字实参: 根据关键字(形参名称)传递

  ​	作用： 通过名称指定形参(可以更有针对性传递,不用全部传递)

  ​	适用性：需要传递部分参数

  ```python
  def func01(p1=0, p2=None, p3=0):
      print(p1)  
      print(p2)  
      print(p3)  
  
  func01(p2=2, p3=3, p1=1)
  # func01(p3=3) 
  ```

- 字典关键字传参

  ​	定义：实参用**将字典拆解后与形参的名字进行对应

  ​	作用：配合形参的缺省参数，可以使调用者随意传参

  ```python
  def func01(p1=0, p2=None, p3=0):
      print(p1)  
      print(p2)  
      print(p3)  
  
  dict01 = {"p3": 3, "p1": 1, "p2": 2}
  func01(**dict01)
  ```

### 形参定义方式parameter

- 缺省参数(默认形参）

  - 语法：

  ​	def 函数名(形参名1=默认实参1, 形参名2=默认实参2, ...):

  ​      		函数体

  - 说明：

  ​	缺省参数必须自右至左依次存在，如果一个参数有缺省参数，则其右侧的所有参数都必须有缺省参数。缺省参数可以有0个或多个，甚至全部都有缺省参数。

  ```python
  # 默认参数：可选
  def func02(p1=0, p2="", p3=0.0):
      print(p1)
      print(p2)
      print(p3)
  
  # 必须从右向左依次存在
  def func03(p1, p2="", p3=0.0):
      print(p1)
      print(p2)
      print(p3)
  ```

  

- 位置形参

  - 语法：

    ​	def 函数名(形参名1, 形参名2, ...):

    ​		函数体

  ```python
  # 位置形参：必填
  def func01(p1, p2, p3):
      pass
  
  # 位置实参:按顺序对应
  func01(1, 2, 3)
  ```

  

- 星号元组形参

  - 语法：

    ​	def 函数名(*元组形参名):

    ​			函数体

  - 作用：

    ​	收集多余的位置传参。

  - 说明：

    ​	一般命名为'args'

    ​	形参列表中最多只能有一个

  ```python
  # 星号元组形参
  def func04(*args):
      print(args)
  
  func04()  # 没有实参,形参得到的是空元组()
  func04(1, 2, 3)  # 有3个实参,形参得到的是1个元组(1, 2, 3)
  list01 = ["a", "b"]
  func04(*list01)  # 相当于 func04("a","b")  有2个实参,形参得到的是1个元组('a', 'b')
  func04(p1 = 1,p2 =2) # 星号元组形参只负责合并位置实参(不管关键字实参)
  ```

  

- 命名关键字形参

  - 语法：

    ​	def 函数名(*, 命名关键字形参1, 命名关键字形参2, ...):

    ​			函数体

    ​	def 函数名(*args, 命名关键字形参1, 命名关键字形参2, ...):
    ​            	函数体

    ```python
    # 命名关键字形参：强制要求使用关键字实参
    def func05(*args, p1, p2):
        print(args)
    
    func05(1,2,3,4)  语法错误
    func05(1, 2, p1=3, p2=4)
    
    def func06(p1, *, p2=0):
        print(p1)
        print(p2)
    # p1 是常用的必填项,p2 是特殊场景可选项
    func06(1, p2=2)  # 为了提高代码可读性
    ```

### 参数自左至右的顺序

​	位置形参 --> 星号元组形参 --> 命名关键字形参 --> 双星号字典形参



## 作用域(LEGB)

### 定义

​	**作用域：**变量起作用的范围

​	**局部变量：**

​		定义在函数内部的变量(形参也是局部变量)

​		只能在函数内部使用

​		调用函数时才被创建，函数结束后自动销毁

​	**全局变量：**

​		定义在函数外部,模块内部的变量

​		在整个模块(py文件)范围内访问（但函数内不能将其直接赋值）

​	**global 语句：**

​		作用：在函数内部修改全局变量。在函数内部定义全局变量(全局声明)。

​		语法：global 变量1, 变量2, …

​		说明：在函数内直接为全局变量赋值，视为创建新的局部变量。

​			   不能先声明局部的变量，再用global声明为全局变量。

### 作用域分类

- Local局部作用域：函数内部。

  ```python
  # 小功能(一个局部小范围使用),使用局部变量
  
  def func01():           # 局部作用域：函数内部 局部变量
      a = 10
      a_b = func02()      # 一个函数希望使用另外一个函数的局部变量通过参数、返回值传递
      print(a_b)
  
  def func02():
      b = 20
      return b
  ```



- Enclosing  外部嵌套作用域 ：函数嵌套。

  

- Global全局作用域：模块(.py文件)内部。

  ```python
  # 大功能(好多个局部都要使用),使用全局变量
  
  # 全局作用域：.py文件
  g01 = 100
  def func03():
      # 可以在局部作用域中读取全局变量
      print(g01)
  
  # 调用func03()
  func03()  #100
  
  # 练习：
  g02 = 200
  def func04():
      # g02 = 2000  # 局部作用域不能修改全局变量
  		    #创建新的局部变量,没有修改全局
      global g02  # 声明全局变量，后在局部作用域中才可以修改
      g02 = 2000
  
  # 调用func04()
  func04()
  print(g02)  #2000
  ```

  

- Builtin内置模块作用域：builtins.py文件。

### 变量名的查找规则

1. 由内到外：L -> E -> G -> B

2. 在访问变量时，先查找本地变量，然后是包裹此函数外部的函数内部的变量，之后是全局变量，最后是内置变量。



## 程序结构  

Python程序完整结构:     包(文件夹)     模块(文件)             类                 函数                     语句   

### 模块Module

#### 定义

​	包含一系列数据、函数、类的文件，通常以.py结尾

#### 作用

​	让一些相关的数据，函数，类有逻辑的组织在一起，使逻辑结构更加清晰。有利于多人合作开发

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

## 文件操作

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

## 异常处理

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



## 类

### 面向过程

1. 分析出解决问题的步骤，然后逐步实现。

例如：婚礼筹办

-- 发请柬（选照片、措词、制作）

-- 宴席（场地、找厨师、准备桌椅餐具、计划菜品、购买食材）

-- 婚礼仪式（定婚礼仪式流程、请主持人）

2. 公式：程序 = 算法 + 数据结构

3. 优点：所有环节、细节自己掌控。

4. 缺点：考虑所有细节，工作量大。

### 面向对象

#### 面向对象技术简介

·     **类(Class):** 用来描述具有相同的属性和方法的对象的集合。它定义了该集合中每个对象所共有的属性和方法。对象是类的实例。

·     **类方法：**类中定义的函数。

·     **类变量：**类变量在整个实例化的对象中是公用的。类变量定义在类中且在函数体之外。类变量通常不作为实例变量使用。

·     **数据成员：**类变量或者实例变量用于处理类及其实例对象的相关的数据。

·     **方法重写：**如果从父类继承的方法不能满足子类的需求，可以对其进行改写，这个过程叫方法的覆盖（override），也称为方法的重写。

·     **局部变量：**定义在方法中的变量，只作用于当前实例的类。

·     **实例变量：**在类的声明中，属性是用变量来表示的，这种变量就称为实例变量，实例变量就是一个用 self 修饰的变量。

·     **继承：**即一个派生类（derived class）继承基类（base class）的字段和方法。继承也允许把一个派生类的对象作为一个基类对象对待。例如，有这样一个设计：一个Dog类型的对象派生自Animal类，这是模拟"是一个（is-a）"关系（例图，Dog是一个Animal）。

·     **实例化：**创建一个类的实例，类的具体对象。

·     **对象：**通过类定义的数据结构实例。对象包括两个数据成员（类变量和实例变量）和方法。

和其它编程语言相比，Python 在尽可能不增加新的语法和语义的情况下加入了类机制。

Python中的类提供了面向对象编程的所有基本功能：类的继承机制允许多个基类，派生类可以覆盖基类中的任何方法，方法中可以调用基类中的同名方法。

对象可以包含任意数量和类型的数据。

 

1. 公式：程序 = 对象 + 交互

2. 优点

   (1) 思想层面：

   ​	-- 可模拟现实情景，更接近于人类思维。

   ​	-- 有利于梳理归纳、分析解决问题。

   (2) 技术层面：

   ​	-- 高复用：对重复的代码进行封装，提高开发效率。

   ​	-- 高扩展：增加新的功能，不修改以前的代码。

   ​	-- 高维护：代码可读性好，逻辑清晰，结构规整。

3. 缺点：学习曲线陡峭。

## 类和对象

1. 类：一个抽象的概念，即生活中的”类别”。

```
类和对象
    现实事物  -抽象化->  类  -实例化->  对象
```

2. 对象：类的具体实例，即归属于某个类别的”个体”。

3. 类是创建对象的”模板”。

-- 数据成员：名词类型的状态。

-- 方法成员：动词类型的行为。

4. 类与类行为不同，对象与对象数据不同。

### 语法

#### 定义类

1. 代码

class 类名:

  “””文档说明”””

 def _init_(self,参数列表):

   self.实例变量 = 参数

方法成员

 

类有一个名为 __init__() 的特殊方法（**构造方法**），该方法在类实例化时会自动调用，像下面这样：

def __init__(self): 

self.data = []

#### self代表类的实例，而非类

 

2. 说明

-- 类名所有单词首字母大写.

-- _init_ 也叫构造函数，创建对象时被调用，也可以省略。

-- self 变量绑定的是被创建的对象，名称可以随意。

 

```python
class Wife:
    # 数据：姓名 身高  颜值
    def __init__(self, name, height, face_score=30):
        # print(id(self))
        self.name = name
        self.height = height
        self.face_score = face_score
```

 

#### 创建对象(实例化)

变量 = 构造函数 (参数列表)

### 实例成员

#### 实例变量

1. 语法

(1) 定义：对象.变量名

(2) 调用：对象.变量名 

 

2. 说明

   (1) 首次通过对象赋值为创建，再次赋值为修改.

   ​	w01 = Wife()

   ​	w01.name = “丽丽”

   ​	w01.name = “莉莉”

   (2) 通常在构造函数(_init_)中创建。

   ​	w01 = Wife(“丽丽”,24)

   ​	print(w01.name)

   (3) 每个对象存储一份，通过对象地址访问。

 

3. 作用：描述某个对象的数据。

4. __dict__：对象的属性，用于存储自身实例变量的字典。

```python
# 实例化
tc = Wife("铁锤", 180, 25)  # 自动调用构造函数__init__
# print(id(tc))
tc.work()# 通过对象地址,调用方法,会自动传递对象地址 work(tc)
ch = Wife("翠花", 160, 26)  # 自动调用构造函数__init__
ch.work()
```

 

#### 实例方法

1. 语法

   (1) 定义： def 方法名称(self, 参数列表):

   ​    						方法体

​		(2) 调用： 对象地址.实例方法名(参数列表)

​     					不建议通过类名访问实例方法

2. 说明

   (1) 至少有一个形参，第一个参数绑定调用这个方法的对象,一般命名为"self"。

   (2) 无论创建多少对象，方法只有一份，并且被所有对象共享。

3. 作用：表示对象行为。

```python
# 行为(函数 = 方法)：工作
def work(self):
    print(self.name, "工作")
```

 

### 类成员

#### 类变量

1. 语法

   (1) 定义：在类中，方法外定义变量。

   ​	class 类名:

   ​      	变量名 = 表达式

   ​	(2) 调用：类名.变量名

     		 不建议通过对象访问类变量

```python
# 全局变量
a = 10

def func01():
    # 局部变量
    b = 20
```

 

2. 说明:

   (1) 存储在类中。

   (2) 只有一份，被所有对象共享。

3. 作用：描述所有对象的共有数据。

#### 类方法

1. 语法

   (1) 定义：

     @classmethod

     	def 方法名称(cls,参数列表):

   ​    	 方法体

   (2) 调用：类名.方法名(参数列表) 

      	不建议通过对象访问类方法

2. 说明

   (1) 至少有一个形参，第一个形参用于绑定类，一般命名为'cls'

   (2) 使用@classmethod修饰的目的是调用类方法时可以隐式传递类。

   (3) 类方法中不能访问实例成员，实例方法中可以访问类成员。

3. 作用：操作类变量。

### 静态方法

1. 语法

   (1) 定义：

     @staticmethod

     def 方法名称(参数列表):

   ​      方法体

   (2) 调用：类名.方法名(参数列表) 

      不建议通过对象访问静态方法

2. 说明

   (1) 使用@ staticmethod修饰的目的是该方法不需要隐式传参数。

   (2) 静态方法不能访问实例成员和类成员

3. 作用：定义常用的工具函数。

4. 示例：

```python
class ICBC:
    """
        工商银行
    """
    # 类变量：总行的钱
    total_money = 1000000

    # 类方法：对类变量的操作
    @classmethod
    def print_total_money(cls):
        # print("工商银行的钱:", ICBC.total_money)
        print("工商银行的钱:", cls.total_money)

    def __init__(self, name, money=0):
        # 实例变量：每个银行的信息
        self.name = name
        self.money = money
        ICBC.total_money -= money

xd = ICBC("西单支行", 500000)
trt = ICBC("陶然亭支行", 400000)
# print("总行的钱,还有:", ICBC.total_money)  # 建议通过类访问
ICBC.print_total_money()# print_total_money(ICBC)
# print("总行的钱,还有:",xd.total_money) # 不建议通过对象访问
# print("总行的钱,还有:",trt.total_money)
```

