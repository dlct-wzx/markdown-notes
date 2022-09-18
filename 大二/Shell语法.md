[TOC]

### Shell元字符

| 字符      | 作用                                      |
| --------- | ----------------------------------------- |
| *         | 匹配0或多个字符                           |
| ?         | 匹配1个字符                               |
| [...]     | 匹配指定集合中的一个字母                  |
| #         | 脚本注释                                  |
| $         | 变量引用                                  |
| `` 或 $() | 命令替换                                  |
| ""        | 字符串节点夫，允许进行变量和命令替换      |
| ''        | 字符串节点夫，不允许进行变量和命令替换    |
| &         | 后台执行： 命令 &                         |
| ()        | 成组命令，括号中的命令将在子shell中执行   |
| {}        | 成组命令，括号中的命令将在当前shell中执行 |
| \         | 转义符                                    |

### Bash shell环境配置文件

**全局配置文件**

- /etc/profile

  交互式登录的shell 提供配置，用于定义环境变量或运行命令和脚本

- /etc/bashrc

  非交互式和交互式登录的shell 提供配置，用于定义命令别名和函数或定义本地变量

**用户配置文件**

- ~/.bash_profile

  同全局

- ~/.profile

  同全局，只在登录时运行一次

- ~/.bashrc

  同全局

- ~/.bash_login

  登录时运行的脚本

- ~/.bash_logout

  退出时运行的脚本

### HelloWorld

```bash
#! /bin/bash  # 用于指定运行脚本默认的解释器
echo "Hello World!"
```

### 注释

```bash
# 单行注释
```

```bash
:<<EOF
第一行注释
第二行注释
第三行注释
EOF
```

其中多行注释中的`EOF`可以替换成其他任意的字符串, 例如

```bash
:<<abc
第一行注释
第二行注释
第三行注释
abc

:<<!
第一行注释
第二行注释
第三行注释
!
```

### 变量

#### 定义变量

```bash
name1='abc'	# 单引号定义字符串
name2="abc"	# 双引号定义字符串
name3=abc		# 不加引号也可表示字符串
```

#### 使用变量

使用变量，需要加上`$`符号，或者`${}`符号。花括号是可选的，主要为了帮助解释器识别变量边界。

```bash
name=abc
echo $name				# 输出abc
echo ${name}			# 输出abc
echo ${name}hello	# 输出abchello
# echo $namehello 这种写法就是错误的
```

#### 只读变量

使用`readonly`或者`declare`可以讲变量变为只读。

```bash
name=abc
readonly name
declare -r name  # 两种写法均可
name=cde  # 尝试修改只读变量，报错
```

#### 删除变量

`unset`可以删除变量。

```bash
name=abc
unset name
echo $name  # 输出空行
```

#### 变量类型

1. 自定义变量（局部变量）

   子进程不能访问的变量

2. 环境变量（全局变量）

   子进程可以访问的变量

自定义变量改为环境变量

![image-20220122011112724](https://img-blog.csdnimg.cn/img_convert/3d34c81eba580bdd4b86483fe39f4b1d.png)

环境变量改为自定义变量

![image-20220122011315350](https://img-blog.csdnimg.cn/img_convert/31b494eedcd41136523c848bfa5b5732.png)

#### 变量声明

```shell
declare  [选项] 变量名
-a		声明变量为数组
-i		声明为整型
-x		声明为环境变量
-r		声明为只读变量
```



#### 变量替换

| **操作符**  | **描述**                                                 |
| ----------- | -------------------------------------------------------- |
| ${var}      | 返回var的值，若没初始化则返回空                          |
| ${var:-str} | 若var存在且不为空则返回var的值，否则返回str              |
| ${var:=str} | 若var存在且不为空则返回var的值，否则将str赋给var然后返回 |
| ${var:?str} | 若var存在且不为空则返回var的值，否则显示：var:str        |
| ${var:+str} | 若var存在且不为空则返回str，否则返回空                   |
| ${#var}     | 返回var的值的长度                                        |
| ${var%str}  | 从var的尾部开始删除匹配str的最小部分                     |
| ${var%%str} | 从var的尾部开始删除匹配str的最大部分                     |
| ${var#str}  | 从var的头部开始删除匹配str的最小部分                     |
| ${var##str} | 从var的头部开始删除匹配str的最大部分                     |

#### 常用环境变量

|            |                                              |
| ---------- | -------------------------------------------- |
| **$HOME**  | **用户的注册目录（用户主目录）；同～**       |
| **$SHELL** | **设置用户的shell类型**                      |
| **$USER**  | **保存当前的用户名**                         |
| **$PATH**  | **定义查找命令的目录列表，目录名用冒号隔开** |
| **$PWD**   | **保存用户当前在文件系统的位置**             |
| **$PS1**   | **定义shell的主提示符**                      |
| **$PS2**   | **定义shell的副提示符**                      |
| **$IFS**   | **域内分隔符**                               |

### 字符串

字符串可以用单引号，可以用双引号，也可以不用引号

##### 单引号与双引号的区别:

- 单引号中的内容会原样输出，不会执行、不会取变量
- 双引号中的内容可以执行、可以取变量

```bash
name=abc
echo 'hello, $name \"hh\"'
echo "hello, $name \"hh\""
```

运行结果如下图:

![image-20220122011737849](https://img-blog.csdnimg.cn/img_convert/a5482461648bfd4645f6803ad4542b71.png)

##### 获取字符串长度

```bash
name=abc
echo ${#name}  # 输出3
```

##### 提取子串

```bash
name="hello, abc"
echo ${name:0:5}  # 提取从0开始的5个字符
```

### 默认变量

在执行shell脚本时，可以向脚本传递参数。`$1`是第一个参数，`$2`是第二个参数，以此类推。特别的是`$0`是该脚本的文件名（包括路径）。

```bash
#! /bin/zsh

echo "文件名: "$0
echo "第一个参数: "$1
echo "第二个参数: "$2
```

其他特殊变量

| 参数         | 说明                                                         |
| ------------ | ------------------------------------------------------------ |
| `$#`         | 代表传入的参数个数                                           |
| `$*`         | 由所有参数构成的用空格分开的字符串，如上例给出的`$1 $2`，各个参数合并成了一个不可分割的整体 |
| `$@`         | 每个参数分别用双引号扩起来的字符串，如上例给出的`"$1" "$2"`，各个参数仍然保持其独立性 |
| `$$`         | 脚本当前的运行ID                                             |
| `$?`         | 上一条命令的退出状态。0表示正常退出，其他值表示错误。        |
| `$(command)` | 返回`command`这条命令的stdout（可嵌套）                      |
| \`command\`  | 返回`command`这条命令的stdout（不可嵌套）                    |
| `#!`         | 最近一次后台进程的ID号                                       |

### 数组

数组中可以存放多个不同类型的数据，只支持一维数组，初始化时不需要指明数组大小。

数组下标从0开始。

#### 定义

数组用小括号表示，元素之间用空格隔开。例如

```bash
array=(1 abc "def" aaa)
```

也可以直接定义数组中某个元素的值

```bash
array[0]=1
array[1]=abc
array[2]="def"
array[3]=aaa
```

#### 使用

格式:

```bash
${array[index]}
```

例如:

```bash
array=(1 abc "def")
echo ${array[0]}
echo ${array[1]}
echo ${array[2]}
```

若要直接使用整个数组：

```bash
${array[@]}  # 第一种写法
${array[*]}  # 第二种写法
```

例如:

```bash
array=(1 abc "def")

echo ${array[@]}  # 第一种写法
echo ${array[*]}  # 第二种写法
```

#### 获取长度

```bash
${#array[@]}
${#array[*]}
```

例如

```bash
array=(1 abc "def")

echo ${#array[@]}  # 第一种写法
echo ${#array[*]}  # 第二种写法
```

### `expr`命令

`expr`命令用于求表达式的值，格式为:

```bash
expr 表达式
```

表达式说明:

- 用空格隔开每一项
- 用转义符放在shell特定的字符前面
- 对包含空格和其他特殊字符的字符串要用引号括起来
- expr会在`stdout`中输出结果。如果为逻辑关系表达式，结果为真`stdout`为1，否则为0。
- expr的`exit code`：如果为逻辑关系表达式，则结果为真，`exit code`为0，否则为1。

#### 字符串表达式

- `length STRING`

  返回`STRING`的长度

- `index STRING CHARSET`

  `CHARSET`中任意单个字符在`STRING`中最前面的字符位置，**下标从1开始**。如果在`STRING`中完全不存在`CHARSET`中的字符，则返回0.

- `substr STRING POSITION LENGTH`

  返回`STRING`字符串中从`POSTION`开始，长度最大为`LENGTH`的子串。如果`POSITION`或`LENGTH`为负数，0或者非数值，则返回空字符串。

示例：

```bash
str="Hello World!"

echo `expr length "$str"`  # 输出12
echo `expr index "$str" awd`  # 输出7，下标从1开始
echo `expr substr "$str" 2 3`  # 输出 ell
```

#### 整数表达式

`expr`支持普通的算术操作，算术表达式优先级低于字符串表达式，高于逻辑关系表达式。

- `+ -`

  加减运算。两端参数会转换为整数，如果转换失败则报错。

- `* / %`

  乘，除，取模运算。两端参数会转换为整数，如果转换失败则报错。

- `()`可以改变优先级，但是需要用反斜杠转义。

示例:

```bash
a=3
b=4

echo `expr $a + $b`  # 输出7
echo `expr $a - $b`  # 输出-1
echo `expr $a \* $b`  # 输出12，*需要转义
echo `expr $a / $b`  # 输出0，整除
echo `expr $a % $b`  # 输出3
echo `expr \( $a + 1 \) \* \( $b + 1 \)`  # 输出20，值为(a + 1) * (b + 1)
```

#### 逻辑关系表达式

- `|`

  如果第一个参数非空且非0，则返回第一个参数的值，否则返回第二个参数的值，但要求第二个参数的值也是非空或非0，否则返回0。如果第一个参数是非空或非0时，存在逻辑短路现象（第二个参数不会被计算）。

- `&`

  如果两个参数都非空且非0，则返回第一个参数，否则返回0。如果第一个参数为0或为空，则不会计算第二个参数。

- `< <= = == != >= >`

  比较两端的参数，如果为`true`，则返回1，否则返回0。"=="是"="的同义词。"expr"首先尝试将两端参数转换为整数，并做算术比较，如果转换失败，则按字典序进行比较。

- `()`可以改变优先级，需要用反斜杠转义

示例：

```bash
a=3
b=4

echo `expr $a \> $b`  # 输出0，>需要转义
echo `expr $a '<' $b`  # 输出1，也可以将特殊字符用引号引起来
echo `expr $a '>=' $b`  # 输出0
echo `expr $a \<\= $b`  # 输出1

c=0
d=5

echo `expr $c \& $d`  # 输出0
echo `expr $a \& $b`  # 输出3
echo `expr $c \| $d`  # 输出5
echo `expr $a \| $b`  # 输出3
```

### read命令

`read`命令用于从标准输入中读入单行数据。当读到文件结束符时，`exit code`为1，否则为0。

参数说明

- `-p`: 后面可以跟提示信息
- `-t`: 后面跟秒数，定义输入字符的等待时间，超过等待时间后会自动忽略此命令

![image-20220124105302895](https://img-blog.csdnimg.cn/img_convert/bc046c44e90f30891f2247daffc46a45.png)

这里`zsh`和`bash`的语法有一点差别，`zsh`想要输出提示语句时不需要`-p`参数:

![image-20220124111419807](https://img-blog.csdnimg.cn/img_convert/c25710e4581d3d0b112c9768d2dab93a.png)

?之后的所有内容都是提示字符，?前面的字符可以用于指定输入的变量名称。

### echo命令

echo用于输出字符串。命令格式:

```bash
echo STRING
```

#### 显示普通字符串

```bash
echo "Hello World"
echo Hello World  # 引号可以省略
```

#### 显示转义字符

```bash
echo "\"Hello World \""  # 注意只能用双引号，因为单引号不转义
echo \"Hello World\"  # 也可以省略双引号
```

#### 显示变量

```bash
name=abc
echo "My name is $name"
```

#### 显示换行

```bash
#! /bin/bash
echo -e "Hello\n"  # -e 开启转义
echo "World"
```

输出结果:

![image-20220124113306819](https://img-blog.csdnimg.cn/img_convert/205d87e42c075930f1ed22262495d6f1.png)

#### 使echo输出后不换行

```bash
#! /bin/bash
echo -e "Hello \c"
echo "World"
```

输出结果:

![image-20220124113158101](https://img-blog.csdnimg.cn/img_convert/8670f6e65e70d721dec9abe63bda2419.png)

如果没有-c:

```bash
#! /bin/bash
echo -e "Hello "
echo "World"
```

输出结果:

![image-20220124113306819](https://img-blog.csdnimg.cn/img_convert/205d87e42c075930f1ed22262495d6f1.png)

#### 原样输出字符串

```bash
name=abc
echo '$name\"'
```

输出结果

```bash
$name\"
```

#### 显示命令的执行结果

```bash
echo `date`
```

输出结果:

![image-20220124113535301](https://img-blog.csdnimg.cn/img_convert/92799ef57bfd04814779b08e0e49b914.png)

### `printf`命令

用于格式化输出，和`C/C++`中的`printf`函数相当类似。

默认**不会在字符串结尾添加换行符**。

命令格式:

```bash
printf format-string [arguments...]
```

#### 示例:

```bash
printf "%10d\n" 123
printf "%.2f\n" 123.123  # 浮点数作为参数
printf "%d\n" `expr 2 \* 3`  # 表达式的值作为参数
```

输出结果:

```bash
       123
123.12
6
```

### `test`命令

#### 逻辑运算符`&&`和`||`

- `&&`为逻辑与，`||`为逻辑或

- 两者具有短路规则:

  `expr1 && expr2`: 当`expr1`为假时，不判断`expr2`

  `expr1 || expr2`: 当`expr1`为真时，不判断`expr2`

- 表达式的`exit code` 为0时，表示真；为非0，表示假。**==（与`C/C++`中定义正好相反）==**

#### `test`命令

`test`命令用于判断文件类型，以及对变量做比较

`test`命令用`exit code`返回结果，而不是`stdout`。0表示真，非0表示假。

例如:

```shell
test 2 -lt 3  # 为真，返回值为0
echo $?  # 输出上个命令的返回值，输出0
```

![image-20220201203126222](https://img-blog.csdnimg.cn/img_convert/f4644abcada3b7d72f7271a0b8a556d6.png)

`-lt`选项如图片中给出的一样。

更多选项可以在man手册中查到。

##### 文件类型判断

命令格式:

```shell
test -e filename  # 判断文件是否存在
```

| 测试参数 | 代表意义     |
| -------- | ------------ |
| -e       | 文件是否存在 |
| -f       | 是否为文件   |
| -d       | 是否为目录   |
| -L/h     | 符号连接文件 |

##### 文件权限判断

命令格式:

```shell
test -r filename  # 判断文件是否可读
```

| 测试参数 | 代表意义       |
| -------- | -------------- |
| -r       | 文件是否可读   |
| -w       | 文件是否可写   |
| -x       | 文件是否可执行 |
| -s       | 是否为空文件   |

##### 整数间的比较

命令格式:

```shell
test $a -eq $b  # a是否等于b
```

| 测试参数 | 代表意义       |
| -------- | -------------- |
| -eq      | a是否等于b     |
| -ne      | a是否不等于b   |
| -gt      | a是否大于b     |
| -lt      | a是否小于b     |
| -ge      | a是否大于等于b |
| -le      | a是否小于等于b |

##### 字符串比较

| 测试参数          | 代表意义               |
| ----------------- | ---------------------- |
| test -z STRING    | 判断STRING是否为空     |
| test -n STRING    | 判断STRING是否为非空   |
| test str1 == str2 | 判断str1是否等于str2   |
| test str1 != str2 | 判断str1是否不等于str2 |

##### 多重条件判定

命令格式:

```shell
test -r filename -a -x filename
```

| 测试参数 | 代表意义                                            |
| -------- | --------------------------------------------------- |
| -a       | 两个条件是否同时成立                                |
| -o       | 两条件是否至少一个成立                              |
| !        | 取反。如 test ! -x file, 当file不可执行时，返回true |

这个语句可以通过`-a`以及`-o`来连接多个选项，实际测试中这两个选项的作用就相当于逻辑表达式中的"与"和"或"，test的返回值就是对用户给出的逻辑表达式进行求值。

![image-20220201212804605](https://img-blog.csdnimg.cn/img_convert/dff3894bd8a50a498acc0de366a704c7.png)

#### 判断符号`[]`

`[]`与`test`用法几乎一模一样，更常用于`if`语句中。另外`[[]]`是`[]`的加强版，支持的特性更多。

例如:

```shell
[ 2 -lt 3 ]  # 为真，返回值为0
echo $?  # 输出上个命令的返回值，输出0
```

![image-20220201214330583](https://img-blog.csdnimg.cn/img_convert/d347741e6e7c2844106b4f71f2ce48e1.png)

这里用到了`&&`短路的特性，才能使正确的`echo`语句得到执行

注意:

- `[]`内的每一项都要用空格隔开
- 中括号内的变量，最好用双引号括起来
- 中括号内的常数，最好用单或双引号括起来

例如:

![image-20220201215645896](https://img-blog.csdnimg.cn/img_convert/3f2717ce9a8e29ed7fbb83e798ae44a7.png)

实测在`zsh`上判等需要用`=`, 而在`bash`上`==`和`=`都能实现判等的效果。

### 判断语句

#### `if...then`形式

类似于`C/C++`中的`if-else`语句。

#### 单层if

```bash
if condition
then
	语句1
	语句2
	...
fi
```

示例:

```bash
a=3
b=4

if [ "$a" -lt "$b" ] && [ "a" -gt 2 ]
then
	echo ${a}在范围内
fi
```

输出结果:

```bash
3在范围内
```

#### 单层`if-else`

命令格式

```bash
if condition
then
	语句1
	语句2
	...
else
	语句1
	语句2
	...
fi
```

示例:

```bash
a=3
b=4

if ! [ "a" -lt "b" ]
then
	echo ${a}不小于${b}
else
	echo ${a}小于${b}
fi
```

#### 多层`if-elif-elif-else`

命令格式

```bash
if condition
then
	语句1
	语句2
	...
elif condition
then
	语句1
	语句2
	...
elif condition
then
	语句1
	语句2
	...
else
	语句1
	语句2
	...
fi
```

#### `case...esac`形式

类似于`C/C++`中的`switch`语句。

命令格式

```bash
case $变量名称 in
	值1)
		语句1
		语句2
		...
		;;  # 类似于C/C++中的break
	值2)
		语句1
		语句2
		...
		;;
	*)  # 类似于C/C++中的default
		语句1
		语句2
		...
		;;
esac
```

### 循环语句

#### `for...in...do...done`

命令格式

```bash
for var in val1 val2 val3
do
	...
done
```

示例1

```bash
for i in a 2 cc
do
	echo $i
done
```

示例2，输出当前路径下的所有文件名

```bash
for file in `ls`
do
	echo $file
done
```

示例3

```bash
for i in $(seq 1 10)
do
	echo $i
done
```

示例4，使用 {1..10} 或者 {a..z}

```bash
for i in {a..z}
do
	echo $i
done
```

实列5，不添加in。默认输出$1 - $$(\$#)

```shell
for var
do 
	echo $var
done
```



#### `for((...;...;...))do...done`

命令格式

```bash
for ((expression; condition; expression))
do
	...
done
```

示例

```bash
for ((i=1; i<=10; i++))
do
	echo $i
done
```

#### `while...do...done`

命令格式

```bash
while condition
do
  语句1
 	语句2
 	...
done
```

示例

```bash
while read name
do
	echo $name
done
```

#### `until...do...done`

当条件为真时结束。

命令格式

```bash
until condition
do
	语句1
	语句2
	...
done
```

示例，当用户输出`yes`或者`YES`时结束，否则一直等待输入。

```bash
until [ "${word}" == "yes" ] || [ "${word}" == "YES" ]
do
	read -p "Please input yes/YES to stop this program: " word
done
```

#### break命令

跳出当前一层循环，但是与`C/C++`不同的是: `break`不能跳出`case`语句。

示例

```bash
while read name
do
	for ((i=1; i<=10; i++))
	do
		case $i in
			8)
				break
				;;
			*)
				echo $i
				;;
		esac
	done
done
```

这个程序每读入非EOF的字符串，会输出一遍1-7。

#### `continue`命令

跳出当前循环。

示例:

```bash
for ((i=1; i<=10; i++))
do
	if [ `expr $i % 2` -eq 0 ]
	then
		continue
	fi
	echo $i
done
```

这个程序输出1-10中所有的奇数。

### 函数

`bash`中函数类似于`C/C++`中的函数，但`return`的值是`exit code`，取值为0-255，0表示正常结束。

如果想获取函数的输出结果，可以通过`echo`输出到`stdout`中，然后通过`$(function_name)`来获取`stdout`中的结果。

函数的`return`值可以通过`$?`来获取。

命令格式:

```bash
[function] func_name() {
	语句1
	语句2
	...
}
```

#### 不获取`return` 值和`stdout`值

示例

```bash
func() {
	name=abc
	echo "Hello $name"
}
func  # 执行函数
```

输出结果:

![image-20220209173726561](https://img-blog.csdnimg.cn/img_convert/a1014b79ce84eba93298a1505e7f34a2.png)

#### 获取`return`值和`stdout`值

不写`return`时，默认`return 0`

示例

```bash
func() {
	name=abc
	echo "Hello $name"
	
	return 123
}

output=$(func)
ret=$?

echo "output = $output"
echo "return = $ret"
```

输出结果

![image-20220209173904366](https://img-blog.csdnimg.cn/img_convert/ad5ce18be4da4067ab59212e1fe7f8a7.png)

#### 函数的输入参数

在函数内，`$1`表示第一个输入参数，`$2`表示第二个输入参数，依次类推。

需要注意的是，函数中的`$0`依然是文件名，而不是函数名。

示例:

```bash
func() {
	word=""
	while [ "${word}" != 'y' ] && [ "${word}" != 'n' ]
	do
		read -p "要进入func($1)函数吗？(y/n):" word
	done
	
	if [ "$word" == 'n' ]
	then
		echo 0
		return 0
	fi
	
	if [ $1 -le 0 ]
	then
		echo 0
		return 0
	fi
	
	sum=$(func $(expr $1 - 1))
	echo $(expr $sum + $1)
}
echo $(func 10)
```

实际测试这个程序在zsh上还是有点问题的，所以还是用bash吧...

下面是输出结果，需要输入11个y。。。

![image-20220209182256507](https://img-blog.csdnimg.cn/img_convert/27cbd9ecd4fa5864faecd809f7eb95b0.png)

代码我把网课的改了一下，把``word=""``这一句挪到了func外面，于是得到了下面这个结果:

![image-20220209182700360](https://img-blog.csdnimg.cn/img_convert/6835c3aa0b761b93a9ef3fa8a7e047df.png)

~~这看起来就正常多了哈哈~~

#### 函数内部局部变量

可以在函数内定义局部变量，作用范围仅在当前函数内。

可以在递归函数中定义局部变量

命令格式：

```bash
local 变量名=变量值
```

例如:

```bash
#! /bin/bash
func() {
	local name=abc
	echo $name
}
func

echo $name
```

上面这个代码里函数内部调用的是局部变量，函数外面调用的是全局变量，所以第二个调用的时候会发现这个输出没结果。

### 文件重定向

每个进程默认打开三个文件描述符:

- `stdin`标准输入，从命令行读取数据，文件描述符为0
- `stdout`标准输出，向命令行输出数据，文件描述符为1
- `stderr`标准错误输出，向命令行输出数据，文件描述符为2

可以用文件重定向将这三个文件重定向到其他文件上。

#### 重定向命令列表

| 命令               | 说明                                        |
| ------------------ | ------------------------------------------- |
| `command > file`   | 将`stdout`重定向到`file`中                  |
| `command < file`   | 将`stdin`重定向到`file`中                   |
| `command >> file`  | 将`stdout`以追加的方式定位到`file`中        |
| `command n> file`  | 将文件描述符`n`重定向到`file`中             |
| `command n>> file` | 将文件描述符`n`以追加的方式重定向到`file`中 |

#### 输入和输出重定向

```bash
echo -e "hello \c" > output.txt  # 将stdout重定向到output.txt
echo "World" >> ouput.txt  # 以追加的形式将stdout重定向到output.txt

read str < output.txt  # 从ouput.txt中读取字符串
echo $str  # 输出结果: Hello World
```

### 引入外部脚本

类似于`C/C++`中的`include`操作，`bash`也可以引入其他文件中的代码。

语法格式:

```bash
. filename  # 文件名和点之间有一个空格
或者
source filename
```

示例

```bash
# test1.sh

#! /bin/bash
name=abc
```

```bash
# test2.sh

#! /bin/bash
source test1.sh
echo $name  # 使用test1.sh中的变量
```

运行结果如下图

![image-20220209195405590](https://img-blog.csdnimg.cn/img_convert/54cb15797c94f87accbcfc5ed9da204e.png)

