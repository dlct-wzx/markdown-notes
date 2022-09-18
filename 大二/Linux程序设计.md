# Linux程序设计

[TOC]

## Linux概述

**什么是Linux**

- Linux是一个类UNIX的操作系统
- 多用户、多任务
- 可以运行在PC（个人电脑）上
- 开源软件，按GPL协议发行
- Linux主要应用于网站服务器、科学计算、嵌入设备
- Linux由Linus Torvakds（林纳斯·托瓦兹）开发

**Linux核心及发行版**

- 核心
  - 由Linus等核心小组成员开发
  - 最新稳定Linux核心版本号3.5.4
  - 版本格式：主版本号.次版本号.补丁包版本号
- 发行版本
  - 组织、商业公司集成Linux核心、GNU软件、自主开发软件
  - 商业发行版 RedHat、SUSE、Slackware
  - 社区发行版 Ubuntu、CentOS、RedFlag

**主机和终端**

- 主机：提供计算、存储功能
- 终端：仅输入/输出功能
  - 控制台终端：PC键盘、显示器和鼠标，可虚拟6个终端；可按Alt+F1-6切换
  - 远程终端：在连接到因特网PC上运行终端仿真软件登录主机；如Windows上客户端软件PieTTy.exe，Linux上ssh命令
  - 字符终端：终端仅输入/输出字符
  - 图形终端：终端运行X-Window服务，可使用鼠标操作

**用户接口**

- 命令行（CLI）

  字符终端，bash提示符下执行命令

- 图形（GUI）

  图形终端，X-Window下使用鼠标，

  或在终端窗口中执行命令

- 应用程序接口（API）

  系统函数，C语言程序调用

**登录、注销、进程、服务**

- **登录**
  - 输入用户名、口令
  - 用户验证->运行bash->设置bash环境，显示shell提示符

- **注销**
  - 终止bash
  - 在$符号后输入命令字exit，按Enter键执行命令 
- **命令**
  - shell命令、可执行文件
- **进程**
  - 正在执行的命令或程序

- **服务**
  - 提供服务功能的进程，如终端服务、Web服务

**用户**

- **root用户**

  提示符#，具有所有操作权限，用于系统管理

- **普通用户**

  提示符$，受系统安全性限制，用于应用开发



## Linux常用命令

**命令格式**

```shell
命令名 [选项][参数1][参数2]
```

- **命令名**

  一般是一串小写字母，Linux中命令名及参数大小写敏感

- **选项/开关**

  一般以“-”开始

- **参数**

  为命令行运行提供数据

- **命令返回一个整数值表示命令是否执行成功**



**帮助命令**

<img src="https://i0.hdslb.com/bfs/album/3e23c8ab5a4797b7939853887255bc3e400dff58.png" alt="image-20220528111648982" style="zoom:50%;" /><img src="https://i0.hdslb.com/bfs/album/202380e2fc33fc3a954eb1672fcdfb94203c7cf5.png" alt="image-20220528111659547" style="zoom:50%;" />



**Linux文件系统**

- Linux 的文件系统目录结构是**单根**的分层树形结构Linux把不同文件系统挂载（mount）在根文件系统下不同的子目录（挂载点）上

  <img src="https://i0.hdslb.com/bfs/album/41677c0010d49e4a98e4dddcc83eb481b80dc6ca.png" alt="image-20220528111813195" style="zoom:80%;" />

  - **/ 根目录 包含所有目录和文件**
  - **/bin  存放重要的Linux命令的可执行文件**
  - **/boot  存放用于启动Linux操作系统的所有文件**
  - **/dev  存放连接到计算机上的设备所对应的文件**
  - **/etc  存放和特定主机相关的文件和目录，包括系统 配置文件；**
  - **/home  一般用户的主目录所在位置**
  - **/proc   当前进程和系统的信息，仅存在内存**
  - **/tmp  临时目录，所有人都可读写**
  - **/user** **综合目录，存放用户使用的命令及应用程序**
  - **/sbin 存放用于系统管理的命令**
  - **/var  可变目录，用于存放变动比较频繁的文件；如：日志；**
  - **/root  root用户主目录**
  - **/lib  共享库**
  - **/lost+found  存放文件系统检测产生的碎片文件**

- **用户主目录**

  普通用户的主目录默认为`/home/用户名`,可用`~`代表主目录

- **当前目录**

  当前工作目录，用户在某时刻所在的目录，用`.`或`./`表示。`../`表示父目录

**文件名通配符**

- `*`	匹配任意长度的字符串，包括空字符
- `?`    匹配任意一个单字，不包括空字符
- `[]`  匹配括号内任意一个字符
- `!`  在`[`之后，表示除`!`以后的字符
- **注：**当通配符被包含在引号重视，shell不再对其进行展开



**文件操作命令**

```shell
ls [参数] [路径列表]
-a     # 列出所有文件，包括以 "." 开头的隐含文件
-l 		 # 列出文件的详细信息
-F     # 在文件名后显示文件类型说明符。/：目录，*：可执行，@：符号链接，|：管道，=：socket文件
-d		 # 列出当前工作目录
-R     # 列出当前目录下所有子目录的文件
```

- **文件详细信息**

  - **文件类型**

    | -    | 普通文件             |
    | ---- | -------------------- |
    | b    | 块设备文件           |
    | c    | 字符设备文件         |
    | d    | 目录                 |
    | l    | 符号连接文件         |
    | p    | 命名管道（FIFO）文件 |
    | s    | socket文件           |

  - **第一行** `total` 总用量=第5列之和 kB
  - **第一列**共10位，第1位表示文档类型后9位，依次对应三种身份所拥有的权限，身份顺序为：owner、group、others，权限顺序为：readable、writable、excutable。如：`-r-xr-x---`的含义为**当前文档是一个文件，拥有者可读、可执行，同一个群组下的用户，可读、可执行，其他人没有任何权限**。
  - **第二列**表示**链接数**（硬链接），表示有多少个文件链接到inode号码。
  - **第三列**表示**拥有者**
  - **第四列**表示所**属群组**
  - **第五列**表示**文档容量大小**，单位字节
  - **第六列**表示**文档最后修改时间**，注意不是文档的创建时间哦
  - **第七列**表示**文档名称**。以点(.)开头的是隐藏文档
  - **注：**对于目录而言`r`：查询该目录下文件名的权限；`w`：在目录下删除、创建、更新文件名的权限;`x`：进入目录的权限

```shell
root@iZ0jlhofuw1hh9sgin8g3xZ:~/6# ls -l
total 136
-rw-r--r-- 1 root root   534 May 27 21:39 1.c
-rw-r--r-- 1 root root  1136 May 27 21:41 2.c
-rw-r--r-- 1 root root   926 May 27 21:42 3.c
-rw-r--r-- 1 root root   613 May 27 21:44 4_get.c
-rw-r--r-- 1 root root   694 May 27 21:43 4_put.c
-rw-r--r-- 1 root root  1514 May 27 21:47 6.c
-rwxr-xr-x 1 root root 17264 May 26 10:34 6_1
-rwxr-xr-x 1 root root 17264 May 26 10:34 6_2
-rw-r--r-- 1 root root  1489 May 26 10:34 6_2.c
-rwxr-xr-x 1 root root 17352 May 26 10:03 a.out
prw-r--r-- 1 root root     0 May 20 16:47 fifo
-rw-r--r-- 1 root root   126 May 20 16:47 g.txt
-rwxr-xr-x 1 root root 17008 May 20 16:02 get
-rw-r--r-- 1 root root   126 May 20 15:44 p.txt
-rwxr-xr-x 1 root root 17008 May 20 16:03 put
root@iZ0jlhofuw1hh9sgin8g3xZ:~/6# 
```

- 常用命令

```shell
pwd 		# 显示当前工作目录

mkdir [-p][-m mode]	# 创建目录
# -p 创建多级目录
# -m 创建目录时指定权限，以nnn方式指定

rmdir [-p]	# 删除目录
# -p 级联删除目录，目录必须为空

cd [目录]		# 切换工作目录
# 不加目录名，返回用户主目录

mv 源文件 目标文件(目录)	# 移动或文件更名

rm [-rf] # 删除文件
# -r 允许删除目录
# -f忽略不存在的文件，不给于提示 

cp 源文件 目标目录  # 文件复制
# -r 递归复制子目录
# -a 复制时保留源文件属性（时间戳、文件属主、符号链接）

find [目录][选项][动作]	# 查找文件
# -name  按名称查找，可以使用通配符，但必须使用引号括起来
# -type 按类型查找
# -exec 将查找到的目标进行进一步处理，exec后跟随处理命令，命令中通过 {} 引用被找的文件，而且命令必须以 “ \;”结束

#####文件内容显示#####
cat 

head [-N]
# -N 显示文件前N行，默认显示10行

tail [-N][+N]
# -N 显示文件后N行
# +N 从文件第N行开始显示

more
# 显示一屏文件信息
# 按 Space 键：显示文本的下一屏内容。
# 按 Enter 键：只显示文本的下一行内容

less
# 与more类似，但是允许用户回看
# 用PageUp键向上翻页
# 用PageDown键向下翻页
# 按Q键, 退出less程序
#####################

wc [-lcmw]# 统计
# -l：统计行数
# -c：统计字节数
# -m：统计字符数
# -w：统计单词数

grep [-vn] 模式 [文件] # 内容筛选
# -v  显示不匹配的行
# -n  显示行号
# 模式：正则表达式
# 不指定文件，从管道获取输入

tar -[cx][zj][v]f 归档文件名 [filelsit] # 文件的压缩与归档
# c: 创建归档	
# x：展开归档
# z：调用gzip对归档压缩/解压	
# j：调用bzip2对归档压缩/解压	
# v：显示冗余信息
# f：使用归档文件必选
eg:
tar -cf archive.tar foo bar  # 从文件 foo 和 bar 创建归档文件 archive.tar
tar -xf archive.tar          # 展开归档文件 archive.tar 中的所有文件
```

- **grep正在表达式元字符**

  | 元字符     | 功能                           | 实例           | 与什么相匹配                                       |
  | ---------- | ------------------------------ | -------------- | -------------------------------------------------- |
  | **^**      | **行开头定位**                 | **^love**      | **与以love开头的行匹配**                           |
  | **$**      | **行末尾定位**                |**love$**|**与以love结尾的行匹配**|
  | **.**      | **任意一个字符**               | **l..e**       | **与包含一个  l  后跟两字符，再跟一个e  的行匹配** |
  | *****      | **跟0或多个前驱字符相匹配**    | **/L*ove/**    | **跟  ove 前有0个或多个L 的行匹配**                |
  | **[ ]**    | **与其中的一个字符匹配**       | **/[Ll]ove/**  | **与包含love  或  Love  的行匹配**                 |
  | **[x-z]**  | **与一个范围内的一个字符匹配** | **/[a-z]ove/** | **与后跟ove的从a-z  的字母相匹配**                 |
  | **[^x-z]** | **与不在范围内的一个字符匹配** | **/[^A-Z\]/**  | **与不包含任何大写字母的行匹配**                   |
  | \          | **用来给一个元字符转义**       | **/love\./**   | **匹配包含love  后跟一个句点的行**                 |



**磁盘操作**

```shell
fdisk [-l] 设备文件 # 磁盘分区
# -l：打印磁盘分区

mount 分区设备文件 安装点 # 分区装载

umount  安装点 # 卸载分区
```



**用户管理**

```shell
useradd 用户名 # 添加用户

passwd [用户名] # 改变用户口令，默认改变自己，只用root可任意指定用户名

userdel 用户名 # 删除用户

su [-][用户名] # 切换用户
# 默认切换root
# - 同时切换shell

who # 显示当前在线用户
who am i # 只显示自己
eg：
[s2020014322@centos ~]$ who
s2020014322 pts/61       2022-05-28 15:39 (113.140.84.101)
s2019012973 pts/64       2022-05-28 15:16 (113.140.84.105)
s2020011360 pts/65       2022-05-28 15:24 (61.185.211.55)
用户名				终端					登录时间					IP地址

# 相关配置文件
/etc/passwd		# 用户信息文件
#文件内容
s2020014322:x:1150:1002:王泽玺,软件2001:/home/s2020014322:/bin/bash
1.用户名:2.用户密码(x表示加密):3.用户ID(UID):4.用户组ID(GID):5.用户说明:6.用户主目录:7.shell

/etc/shadow		# 加密口令
#文件内容
root:!:18004:0:99999:7:::
1.用户名:2.密码(!：未设置，设置后加密显示):3.上次设置时间据1970.1.1多少天:4.密码最短有效天数（0无限）无限:5.密码最长有效天数(99999无限):6.密码过期后宽限天数

/etc/group		# 组信息文件
#文件内容
bin:x:1:root,bin,daemon
1.组名:2.密码(x无密码):3.GID:4.用户
```



**进程管理**

```shell
ps [-lauxwm] # 查看进程
# l：以长列表形式显示
# w：以加宽格式显示
# a：显示所有用户进程
# u：按用户名和启动时间的顺序显示进程
# x：显示无控制台进程
# 常用组合：-aux 显示所有进程			

top # 动态显示进程信息

kill -9 PID	# 强制杀死进程

命令 & # 将命令放到后台执行，释放shell提示符 
```

- **ps -l命令输出字段含义**
  - **USER ：进程的属主；**
  - PID ：进程的ID；
  - PPID ：父进程；
  - %CPU： 进程占用的CPU百分比；
  - %MEM ：占用内存的百分比；
  - NI ：进程的NICE值，数值大，表示较少占用CPU时间；
  - VSZ： 进程使用的虚拟內存量（KB）；
  - RSS ：该进程占用的固定內存量（KB）（驻留中页的数量）；
  - TTY ：该进程在那個終端上運行（登陸者的終端位置），若與終端無關，則顯示（？）。
    若为pts/0等，则表示由网络连接主机进程
  - WCHAN ：当前进程是否正在進行，若为-表示正在進行；
  - START ：該進程被觸發启动时间；
  - TIME： 該进程實際使用CPU運行的时间；
- **STAT字段为进程状态**
  - D ：无法中断的休眠状态（通常 IO 的进程）；
  - R ：正在运行可中在队列中可过行的；
  - S ：处于休眠状态；
  - T ：停止或被追踪；
  - W ：进入内存交换 （从内核2.6开始无效）；
  - **Z ：僵尸进程**
  - N ： 优先级较低的进程



**文件权限**

```shell
ls -l # 查看文件权限

chmod #改变文件权限
chmod nnn [-R] 文件列表
chmod [augo][+-=][rwx] 文件列表
# -R 目录递归

# 当前用户具有所有权限，组用户有读写权限，其他用户只有读权限。
chmod u=rwx, g=rw, o=r ./test.log
# 等价的八进制数表示：
chmod 754 ./test.log

chown #改变文件所有者
chown user[.group][-R] 文件列表
# 将目录/usr/meng及其下面的所有文件、子目录的文件主改成 liu：
chown -R liu /usr/meng
```



**网络命令**

```shell
ifconfig # 查看设置网络接口设置

ping 网址 # 检查网络接口状态

netstat –[anr] # 查看网络监听/连接状态
# -a：显示所有连接
# -r：显示路由表
# -n：以数字显示连接端口
```



**软件安装/卸载**

```shell
rpm –[iU]vh 包列文件名表		安装
rpm –e 软件包名					卸载
#在线安装
yum install/remove  包名
```



## vim 编辑器

**工作模式**

<img src="https://i0.hdslb.com/bfs/album/56c456138e53e629cf13656db0bc4d92835e6f14.png" alt="image-20220528183415867" style="zoom:80%;" />

**常用语法**

| **语法**                      | **说明**                                   |
| :---------------------------- | ------------------------------------------ |
| **i**                         | **在光标所在字母之前插入，进入输入模式**   |
| **a**                         | **在光标所在字母之后插入，进入输入模式**   |
| **o**                         | **在当前行之下插入一个新行，进入输入模式** |
| **O**                         | **在当前行之上插入一个新行，进入输入模式** |
| **x**                         | **剪切**                                   |
| **y**                         | **复制**                                   |
| **dd**                        | **删除当前行**                             |
| **p**                         | **粘贴**                                   |
| **n + Enter**                 | **向后n行**                                |
| **n + [x dd yy]**             | **剪切n个字，删除n行，复制n行**            |
| **v**                         | **选中一个字**                             |
| **V**                         | **选中一行**                               |
| **gg**                        | **到文件开头**                             |
| **G**                         | **到文件结尾**                             |
| **^**                         | **到行首**                                 |
| **$**                         | **到行末**                                 |
| **u**                         | **撤销**                                   |
| **ctrl+r**                    | **取消撤销**                               |
| **`:l1,l2y`**                 | **复制l1行到l2行的内容**                   |
| **`s/string1/string2/`**      | **在本行使用string2替换第一个string1**     |
| **`s/string1/string2/g`**     | **在本行使用string2替换所有string1**       |
| **`1,10s/string1/string2/g`** | **在1到10行使用string2替换所有string1**    |
| **`1,$s/string1/string2/g`**  | **在全文使用string2替换所有string1**       |
| **`:set nu[mber]`**           | **显示行号**                               |
| **`:set nonu[mber]`**         | **不显示行号**                             |
| **`:set ts=4`**               | **设置tab=4个空格**                        |
| **`:set sm`**                 | **设置括号匹配**                           |



## Shell及Shell编程

**Shell是用户和系统（内核）之间的接口，是一个交互的命令解释器，它提供一组公用程序，利用Kernel（内核）功能完成用户提出的任务**

- **分析命令**
- **处理通配符、重定向、管道和作业控制**
- **搜索命令并执行**

**Shell种类**

- `/bin/sh    B-shell`

  Uinx标准Shell

- `/bin/csh    C-shell`

- `/bin/bash     Bourne Again Shell`

  Linux标准Shell

Shell一般由管理员指定，保存在`/etc/passwd`文件中，可以使用`usermod`命令修改

**Linux命令种类**

- **内部命令**：内嵌在Shell中

- **外部命令**：存在于磁盘上的独立可执行文件

- 使用`type`查看命令类型

  **`type [option] command`**

  - **-t：显示类别，file：外部命令，alias：别名，builtin：内部命令**
  - **-p：显示命令完整路径**
  - **-a：显示所有匹配命令**

- **bash命令查找循序**

**bash基本功能**

- **名称补全**
- **命令别名**
  - `lias dir='ls – –color=tty'`增加一个别名
  - `unalias dir`删除一个别名

- **历史机制**

  使用`history`获取历史命令

- **输入输出重定向**
  - **输入重定向** `< 文件名`
  - **标准输出重定向：**`[1]>  >>`
  - **指定文件描述符的输出重定向** `文件描述符1>&文件描述符2  1：标准输出 2：标准出错`

- **管道** 

  **用于连接两个命令，将前面命令的输出作为后面命令的输入**



**更多语法详见Shell语法文件**



## C开发工具

**先导知识：C语言语法**

**Linux下C语言程序**

```c
int main(int argc, char *argv[]){
  /*
  argc：命令行输入参数的个数
  argv：命令行输入参数的数组
  */
  ...
  return 0;
}
```

**gcc编辑器**

- 编译流程

  ![image-20220529092103981](https://i0.hdslb.com/bfs/album/8bd1f5ba83dbe6c3716cff72e21718c30e5f9149.png)

- 编译选项

  | 选项        | 效果                                               |
  | ----------- | -------------------------------------------------- |
  | -o [文件名] | 指定输出文件名，默认为a.out                        |
  | -E          | 仅进行预处理，生成预处理代码（可通过-o输出到文件） |
  | -S          | 编译成汇编语言，生成汇编代码:*.s                   |
  | -c          | 编译到目标文件，不进行链接，生成目标文件：*.o      |
  | -g          | 编译时在可执行文件中插入调试信息，以便gdb调试      |
  | -Wall       | 显示更多警告信息                                   |
  | -O n        | 优化编译，提高可执行程序的速度，n可选：1，2，3     |
  | lx          | 链接x链接库，对于库文件libx.so或libx.a             |
  | ldir        | 指定头文件位置                                     |
  | Ldir        | 指定库文件位置                                     |

  

**函数库**

- 函数库是一组预先编译好的函数集合，一边重复使用

- **静态库：*.a**

  - **在链接阶段，编译器将指定的静态库和程序代码结合生成可执行文件**

  - 创建静态库：将源码编译成目标文件（*.o），再利用`ar`创建静态库 

    ```shell
    ar [crv] 静态库 目标文件列表
    # c：创建归档
    # r：将目标文件追加或替换原有文件
    # v：显示过程信息
    ```

- **共享库（静态库）：*.so**
  - **在编译时，并不将函数库的代码插入到可执行程序中，而是将库的引用插入，在执行期动态的加载函数库**

**Make工程管理**

- 在模块开发中，使用`make`来根据程序模块的修改情况重新编译链接目标代码，以保证目标代码总是由它最新的模块组成
- Makefile文件：**Makefile描述了软件包中各个文件之间的依赖关系，提供了更新每个文件的命令**

```shell
make [选项][宏][目标]
# -f makefile	指定规则文件，默认为Makefile
# -d	显示调试信息
# -n	显示命令，但不执行
# -s	执行命令但不显示任何信息
```

- **make规则**

```makefile
目标文件: 依赖文件列表
<TAB>命令列表
eg：

3-3: prom.o insert.o fast.o
        gcc prom.o insert.o fast.o -o 3-3
prom.o: prom.c
        gcc -c prom.c
insert.o: insert.c
        gcc -c insert.c
fast.o: fast.c
        gcc -c fast.c
clean:
        rm *.o
```



**gdb调试工具**

- 跟踪指定程序的运行，给出它的内部运行状态以协助开发者定位程序中的错误

```shell
gdb  [选项]  [可执行程序]
# -n	不执行任何初始化文件中的命令，默认初始化文件为 .gdbinit
# -q	安静模式运行，不输出介绍和版权信息
# -cd dir	将dir作为调试的工作目录，默认为当前目录
```

- **gdb命令**

```gdb
file						装入待调试的程序
kill						终止当前调试的程序
list/l					列出源程序，默认只显示10行，按回车继续显示下10行
next/n					执行一行程序但不进入函数
step/s					执行一行程序但且进入函数
run/r						执行当前程序
watch/w					动态监视指定变量的值，当变量变化时立即暂停执行
print/p					打印表达式值
break n/b n			在第n行上设置断点
quit/q					退出调试
```



## Linux系统调用

**系统调用（函数）与库函数**

- 系统调用：是操作系统为用户态运行的进程和硬件设备(如CPU、磁盘、打印机等)进行交互提供的一组接口；是操作系统留给用户程序的一个接口。**系统调用直接运行在内核空间。系统调用面向硬件，不带缓冲**。系统调用是**操作系统**相关的，因此一般没有跨操作系统的可移植性

- **库函数调用**：**面向应用开发，相当于应用程序的api**。它对系统调用进行了封装，库函数的优势：第一：双缓冲技术的实现。第二，可移植性。第三，弥补了底层调用本身的一些性能方面的缺陷。**库函数调用运行在用户空间**

**数学函数**

头文件<math.h>，实现在libm.so

```c
double pow(double x, double y)
//幂运算
double sqrt(double x)
//开方运算
```
**随机数函数**

头文件在<stdlib.h>

```c
int rand()
//随机数，产生一个0~2147483647之间的一个数，不设置种子，一直一个数
void srand(unsigned int seed)
//设置随机种子
```

**字符函数**

头文件在<ctype.h>

```c
int isalnum(char ch)	
//ch是否为数字或字母，是返回非零值
int isalpha(char ch)
//ch是否为字母，是返回非零值
int isupper(char ch)
//ch是否为大写字母，是返回非零值
int islower(char ch)
//ch是否为小写字母，是返回非零值
```

**系统时间与日期函数**

- **包括系统日期的获取设置、日期转换等，包含在“time.h”头文件中。Unix/Linux以秒为单位记录间，数据类型为time_t**

- 相关结构体

```c
struct tm{
	int tm_sec;		 /* Seconds.     [0-60] (1 leap second) */
	int tm_min;		 /* Minutes.     [0-59] */
	int tm_hour;	 /* Hours.       [0-23] */
	int tm_mday;	 /* Day.         [1-31] */
	int tm_mon;		 /* Month.       [0-11] */
	int tm_year		 /* Year - 1900. */ 
	int tm_wday;	 /* Day of week. [0-6] */
	int tm_yday;	 /* Days in year.[0-365] */
	int tm_isdst;  /* 夏令时        [-1/0/1]*/
}

#inlcude<sys/time.h>
struct timeval{
	time_t tv_sec;
	suseconds_t tv_usec;
}

struct timezone{
	 int     tz_minuteswest;
	 int     tz_dsttime;//若夏令时则返回非零
}
```

- 函数

```c
time_t time(time_t *t)  
//系统调用，返回自1970.1.1午夜以来流失的秒数

struct tm * gmtime(const time_t *timep)
//转换为格林尼治时间

struct tm * localtime(const time_t * timep)  
//将时间转换为当地更人性化的时间
char * asctime(const struct tm *tp)
char * ctime(const time_t *t)
//都是将指定时间转换为字符形式的时间，长度大概26个字母

time_t mktime(struct tm *tp)
//将结构体时间转换为流失的秒数

#inlcude<sys/time.h>
int gettimeofday(struct timeval *tv, struct timezone *tz)
//将当前系统时间填充到tv中，将当前时区填充到tz中。返回0表示成功，-1表示失败
//可以获取高精度时间
```

- 示例

```c
#include<stdlib.h>
#include<time.h>
#include<sys/time.h>
#include<unistd.h>

int main(){
    time_t mtime;
    struct tm *gtime;
    char * ctime;
    struct timeval tv;
    struct timezone tz;
    //获取本时区与格林尼治时间之间的差：分钟
    gettimeofday(&tv,&tz);

    time(&mtime);//获取系统时间
    //打印系统时间（当前时间到1970.1.1午夜流失的秒数）、时区
    printf("seconds:%ld\ntimezone:%d\n",mtime,tz.tz_minuteswest/60);

    gtime = localtime(&mtime);//转换为本地时间
    //按格式输出时间
    printf("cur Time: %d-%d-%d %d:%d \n",gtime->tm_year+1900,gtime->tm_mon+1,gtime->tm_mday,gtime->tm_hour,gtime->tm_min);
    //转换为字符串时间
    ctime = asctime(gtime);
    printf("local time: %s\n",ctime);


    return 0;
}
```



**环境控制函数**

```c
char * getenv(char *name)
//获得名称为name的环境变量的值
  
int putenv(char *str)
//添加变量或修改变量值，str格式：name=value

int	setenv(char *name, char *value, int overwrite)
//若name不存在则添加，若存在且overwrite为1则用value值更新原值，若overwrite为0则忽略
  
int unsetenv(char *name)
//删除指定的环境变量

extern char **environ
//所有环境变量
```

- 示例

```c
#include<stdio.h>
#include<stdlib.h>

extern char **environ;
int main(){
    int i;
    printf("current user: %s \n",getenv("USER"));

    printf("\n\nENV VAR List:\n");

    for(i = 0; environ[i]; i++){
                    printf("%s\n",environ[i]);
    }

    return 0;
}
```



**内存分配**

```c
void *malloc(size_t size)
//分配一个大小为size的内存块，不做初始化，返回一个为类型指针

void *calloc(size_t nmemb, size_t size)
//分配size个大小为nmemb的内存块，返回的是一个无类型指针数组

void free(void *ptr)
释放ptr指向的内存

#include<sys/mman.h>
void *mmap(void *start, size_t len, int port, int flags, int fd, off_t offset)
/*
start: 内存起始地址，一般设为NULL
len：分配内存大小
prot：映射内存区域的包含方式；可取值：PROT_EXEC、PROT_READ、PROT_WRITE、PROT_NONE(内存不可访问) 
fd：文件描述符
offsize：映射文件内容的起始位置，设为0表示映射整个文件
flags：指定映射类型。MAP_SHARED：共享内存，对内存的修改其它进程可见，同时反映到文件；MAP_PRIVATE：修改其它进程不可见，且不反映到文件。Map_SHARED和MAP_PRIVATE必须二选一。MAP_FIXED：若指定了start，且使用start无法创建成功，则放弃映射；不推荐使用
系统调用，将指定文件内容映射到内存中，对该区块内存的存取即对该文件的存取
*/
  
int munmap(void *addr, size_t len)
/*
addr：待解除内存起始地址
len：大小
解除映射
*/
```

- 示例

```c
#include<stdio.h>
#include<stdlib.h>
#include<unistd.h>
#include<sys/types.h>
#include<sys/mman.h>
#include<sys/stat.h>
#include<fcntl.h>

int main(int argc, char **argv){
    int fd;//文件描述符
    off_t len;//文件长度
    char *mapper;//内存映射地址

    fd = open(argv[1],O_RDWR);//打开文件，以读写方式

    len = lseek(fd,1,SEEK_END);//获取文件大小

    //将整个文件映射到内存，以读写模式、共享映射
    mapper = (char *)mmap(NULL,len,PROT_READ|PROT_WRITE,MAP_SHARED,fd,0);
    //若映射失败
    if(mapper == MAP_FAILED)
                    perror("mapped fail...");
    //关闭文件
    close(fd);
    //修改映射区内容
    mapper[10] = 'R';
    //解除映射
    munmap((void *)mapper,len);

    return 0;
}
```



## Linux 文件IO操作

**文件与目录**

- **文件除了文件内容外，还有一个名字和一些属性，即：“管理信息”，以便于进行管理**
- **文件的属性被保存在文件的索引节点（inode）中**
- **在Unix/Linux文件系统中Inode是文件系统中的一个特殊的数据块，用于保存文件的属性信息，这些属性信息包括**
  - **文件使用的设备号**
  - **索引节点号**
  - **文件访问权限和文件类型**
  - **文件的硬链接数**
  - **UID**
  - **GID**
  - **设备文件的设备号**
  - **文件大小**
  - **包含该文件的磁盘的块大小**
  - **文件占用的磁盘块的数**
  - **最后访问时间**
  - **最后修改时间**
  - **文件状态最后改变时间**

- 目录的内容主要由：**文件名和索引节点号**组成。目录中每一对文件名和索引节点号称为一个**连接**
- **删除一个文件时，实质是删除目录中与该文件对应的“连接”，同时将文件属性中的硬连接数减1（只有硬连接数为0时，文件才被真正的删除）**

![image-20220529192005267](https://i0.hdslb.com/bfs/album/1fed878a3e85f80310d73651309ed3de5bb51d7c.png)

**Unix/Linux输入输出基本概念**

- **在程序开始读写文件之前，必须首先建立程序和文件之间的连接或通讯通道，这个过程称为打开文件。在Linux有两种机制实现该过程：文件描述符和流**

- **文件描述符**

  **为int类型的对象。文件描述符函数多为系统调用，它们提供底层的输入输出操作接口，主要用于对特定的设备进行操作**

- **流**

  **建立在文件描述符之上。流操作函数都是C的标准库函数，任何运行ANSI C的系统上均支持流**

```c
默认的三个文件描述符
STDIN_FILENO(标准输入)
STDOUT_FILENO(标准输出)
STDERR_FILENO(标准出错)
```



**系统调用**

```C
int system(char *cmdstr);
//产生一个子进程，调用 /bin/sh –c cmdStr 来执行 cmdstr 指定的任务，/bin/sh 调用失败返回127，其他失败返回-1，成功返回0
```





**文件权限**

```c
#include<sys/types.h>
#include<sys/stat.h>
int chmod(cahr *path, mode_t mode);
//修改path指定的文件的权限，注意当前用户的身份
//mode可以表示为一串八进制数字
//eg:所有者读写，其他人读
0644
```

**mode是一个32位的无符号整数，取值为：**

| **S_IRUSR** | **所有者读权限**   | **S_IXGRP** | **组成员执行权限** |
| ----------- | ------------------ | ----------- | ------------------ |
| **S_IWUSR** | **所有者写权限**   | **S_IROTH** | **其他人读权限**   |
| **S_IXUSR** | **所有者执行权限** | **S_IWOTH** | **其他人写权限**   |
| **S_IRGRP** | **组成员读权限**   | **S_IXOTH** | **其他人执行权限** |
| **S_IWGRP** | **组成员写权限**   |             |                    |



**权限掩码**

```c
mode_t umask(mode_t cmask);
//修改当前进程环境的权限掩码为 cmask：八进制值，同上
//返回修改之前的掩码
```

- **掩码可以理解为删去的权限**



**读取文件属性**

```c
#include <sys/stat.h> 
#include <unistd.h>
struct stat { 
    dev_t         st_dev;       //文件的设备编号 
    ino_t         st_ino;       //节点 
    mode_t        st_mode;      //文件的类型和存取的权限 
    nlink_t       st_nlink;     //连到该文件的硬连接数目，刚建立的文件值为1 
    uid_t         st_uid;       //用户ID 
    gid_t         st_gid;       //组ID 
    dev_t         st_rdev;      //(设备类型)若此文件为设备文件，则为其设备编号 
    off_t         st_size;      //文件字节数(文件大小) 
    unsigned long st_blksize;   //块大小(文件系统的I/O 缓冲区大小) 
    unsigned long st_blocks;    //块数 
    time_t        st_atime;     //最后一次访问时间 
    time_t        st_mtime;     //最后一次修改时间 
    time_t        st_ctime;     //最后一次改变时间(指属性) 
}; 

int fstat(int fd, struct stat *buf);
//获取指定文件描述符文件的属性信息，并填充到buf

int stat(const char *path, struct stat *buf);
int lstat(const char *path, struct stat *buf);
//获取指定文件文件的属性信息，并填充到buf
//若文件为符号链接，stat返回的是该链接指向的文件的信息，而lstat返回的是符号链接的属性信息

//文件判断宏
//若为对应文件返回1
int S_ISREG(st_mode);		常规文件
int S_ISDIR(st_mode);		目录
int S_ISBLK(st_mode);		块设备
int S_ISCHR(st_mode);		字符设备
int S_ISSOCK(st_mode);	套接字
int S_ISFIFO(st_mode);	命名管道
int S_ISLNK(st_mode);		符号链接
  
//文件权限判断
//拥有权限返回1
st_mode & 权限码
//eg：
//判断所有者读权限
st_mode & S_IRUSR
```

**示例**

```c
#include<stdio.h>
#include<stdlib.h>
#include<sys/types.h>
#include<sys/stat.h>

void ftype(mode_t mt,char rs[]){
      char t = ' '; 

      if(S_ISREG(mt))
                      t = '-';
      else if(S_ISDIR(mt))
                      t = 'd';
      else if(S_ISBLK(mt))
                      t = 'b';
      else if(S_ISCHR(mt))
                      t = 'c';
      else if(S_ISLNK(mt))
                      t = 'l';
      else if(S_ISSOCK(mt))
                      t = 's';
      else if(S_ISFIFO(mt))
                      t = 'p';
      rs[0] = t;

      rs[1] =  mt & S_IRUSR?'r':'-';
      rs[2] =  mt & S_IWUSR?'w':'-';
      rs[3] =  mt & S_IXUSR?'x':'-';
      rs[4] =  mt & S_IRGRP?'r':'-';
      rs[5] =  mt & S_IWGRP?'w':'-';
      rs[6] =  mt & S_IXGRP?'x':'-';
      rs[7] =  mt & S_IROTH?'r':'-';
      rs[8] =  mt & S_IWOTH?'w':'-';
      rs[9] =  mt & S_IXOTH?'x':'-';

}

int main(int argc, char **argv){
    struct stat st;
    char rs[] = "----------";

    if(stat(argv[1],&st) < 0){
                    perror("file open fail...");
                    exit(1);
    }
    ftype(st.st_mode,rs);
    printf("%s\n",rs);

    return 0;
}
```





**不带缓存的I/O操作**

```c
#include<sys/types.h>
#include<sys/stat.h>
#include<fcntl.h>
int creat(char *pathname, mode_t mode);
/*
pathname：待创建文件路径
mode_t：新建文件的初始权限
return：成功返回一个最小可用的文件描述符，否则返回-1
功能：创建文件
*/

int open(char *pathname, int flags[, mode_t mode]);
/*
pathname：待打开文件路径
flags：打开方式
O_RDONLY 以只读方式打开文件
O_WRONLY 以只写方式打开文件
O_RDWR 以可读写方式打开文件. 上述三种旗标是互斥的, 也就是不可同时使用, 但可与下列的旗标利用OR(|)运算符组合.
O_TRUNC（清空原有内容）
O_CRO_TRUNC（清空原有内容）EAT 若欲打开的文件不存在则自动建立该文件.
O_EXCL 如果O_CREAT 也被设置, 此指令会去检查文件是否存在. 文件若不存在则建立该文件, 否则将导致打开文件错误. 此外, 若O_CREAT 与O_EXCL 同时设置, 并且欲打开的文件为符号连接, 则会打开文件失败.
*/

#include<unistd.h>
int close(int fd);
//关闭fd文件

ssize_t read(int fd, void *buf, size_t count);
//从fd中读取count个字节到缓存buf中，返回实际读取的字节数，出错返回-1
ssize_t write(int fd, void *buf, size_t count);
//将buf中count个字节写入到fd指向的文件中；返回实际写入的字节数，出错返回-1

#include <sys/types.h>
#include <unistd.h>
off_t lseek(int fd, off_t offset, int whence);
/*
fd : 文件描述符
offset : 文件偏移量（offset为负值表示往前偏移，正值则表示往后偏移）
whence : 偏移位置(SEEK_SET，SEEK_CUR，SEEK_END)
  1. SEEK_SET表示从文件开头位置往后移动offset个字节，且offset只能为正数，如果offset为负数是没有意义的。
  2. SEEK_CUR表示从当前文件的位置往前或往后移动offset个字节，如果offset为正数则表示往后移动，为负数则表示往前移动。
  3. SEEK=END表示从文件末尾的位置往前或往后移动offset个字节，如果offset为正数则表示往后移动为负数则表示往前移动。
return： 成功返回文件当前读写位置相对于文件开始位置的偏移量（字节数），失败返回-1并设置errno
*/

#include<unistd.h>
int access(char *path, int mod);
/*
path：待检测文件
mode：测试项；R_OK、W_OK、X_OK、F_OK（是否存在）其中之一或多值按位或
*/

#include<fcntl.h>
#include<unistd.h>
int fcntl(int fd, int cmd[, flags|lockType]);
/*
对文件加强制性锁
fd：文件描述符
cmd：操作命令
	F_GETFL（读取锁）：获取指定描述符的状态标识；
	F_SETFL（设置锁）：重设文件状态标识：O_APPEND、O_NONBLOCK、O_ASYNC。
		O_NONBLOCK 非阻塞I/O;如果read(2)调用没有可读取的数据,或者如果write(2)操作将阻		塞,read或write调用返回-1和EAGAIN错误
		O_APPEND 强制每次写(write)操作都添加在文件大的末尾,相当于open(2)的O_APPEND标志
		O_ASYNC 当I/O可用的时候,允许SIGIO信号发送到进程组,例如:当有数据可以读的时候
flags：同open函数中的flags
lockType：一个struct flock 类型变量
*/
```

**示例**

```c
#include<stdio.h>
#include<stdlib.h>
#include<fcntl.h>
#include<unistd.h>

int main(int argc,char *argv[]){
  int fd,cnt;
  char buf[80];

  fd = open(argv[1],O_RDONLY);
  fd2 = open(argv[2],O_WRONLY);
  if(fd < 0){
    perror("open fial ...\n");
    exit(1);
  }

  while((cnt = read(fd,buf,80)) > 0){
    write(fd2,buf,cnt);
  }
  close(fd);
}


```







**文件的阻塞与非阻塞**

![image-20220530202545328](https://i0.hdslb.com/bfs/album/7cda10930b43879c33257fa4529f49dcee897e94.png)

- **文件默认以阻塞方式打开；非阻塞方式在打开文件时，在flags中添加O_NONBLOCK即可**
- **以非阻塞方式操作时，若不能读写，则读写函数立即返回-1，并置errno为EWOULDBLOCK**
- 使用 **fcnlt函数** 修改已打开文件
  - 首先，通过 **fcntl** 获取文件描述符的打开标志 **flags**
  - 然后 修改flags的值：
    - 设置为非阻塞模式：**flags** **|=** **O_NONBLOCK**
    - 设置为阻塞模式：**flags &= ~O_NONBLOCK**
  - 最后，通过 **fcntl** 将新的 **flags** 写入文件文件描述符**

**文件上锁**

- 文件上锁可以避免对共享的资源产生竞争，发生读写错误
- 文件锁分为 **建议性锁（使用flock函数）**、**强制性锁（使用fcntl函数）**

- **建议性锁（使用flock函数）**
  - **建议性锁，不具备强制性**，一个进程将文件锁住后，另一个进程亦可以操作，flock可以检测是否加锁
  - 进程使用flock尝试锁文件时，如果文件已经被其他进程锁住，进程会被阻塞直到锁被释放掉，或者在调用flock的时候，采用LOCK_NB参数，在尝试锁住该文件的时候，发现已经被其他服务锁住，会返回错误，errno错误码为EWOULDBLOCK。即提供两种工作模式：阻塞与非阻塞类型

```c
#include<sys/file.h>
int flock(int fd, int operation);
/*
opteration：锁类型
	LOCK_SH：共享锁；多个进程可同时对同一个文件建立共享锁
	LOCK_EX：互斥锁；一个文件只能有一个互斥锁
	LOCK_UN：解锁
	LOCK_NB：指示若无法建立锁则立即返回；通常与LOCK_SH和LOCK_EX同时使用。
*/

//fcntl加锁
int fcntl(int fd, int cmd, lockType)
//lockType：一个struct flock 类型变量
//cmd：F_SETLK（设置锁）、F_GETLK（读取锁）


struct flock{
  shot l_type;			//锁类型
	shot l_whence;  		//l_start计算方式
  off_t	l_start;		//加锁起始点
  off_t  l_len;			//加锁长度，0：表示整个文件
  pid_t	 l_pid;			//加锁进程号,由内核设置
}
/*
l_type ：F_WRLCK（互斥锁）、F_RDLCK（共享锁）、F_UNLCK
l_whence：SEEK_SET、SEEK_CUR、SEEK_END
*/
```

**示例**

```c
#include<stdio.h>
#include<stdlib.h>
#include<fcntl.h>

int main(){
    int fd,cnt;
    char buf[80];

    fd = open("/dev/tty",O_RDWR);

    printf("Now is block read....\n");
    printf("Wait your input....\n");
    cnt = read(fd,buf,80);

    printf("your input:\n");
    write(fd,buf,cnt);

    printf("Now is NoBlock read....\n");
    printf("You must input in 3 seconds...\n");

    int flags;
    flags = fcntl(fd,F_GETFL);

    fcntl(fd,F_SETFL,flags|O_NONBLOCK);//设置对文件的操作为非阻塞
    sleep(3);//等待3秒
    cnt = read(fd,buf,80);

    if(cnt == -1){
      printf("no input in 3 seconds....\n");
    }
    else{
      write(fd,"your input： ",13);
      write(fd,buf,cnt);
    }

    close(fd);
    return 0;
}
```







**带缓冲的文件流操作**

- 又称为标准I/O操作，符合ANSI C标准，是在内存中开辟一个“缓存区”，为程序中的每个文件使用
- 标准I/O更便于移植，效率更高
- 相关函数（基本与不带缓冲的相同）
  - fopen、fclose、fgetc、fputc、fgets、fputs、fread、fwrite、fseek、rewind、ftell
  - 特殊流：stdin、stdout、stderr（标准输入，标准输出、标准出错）

**特殊文件操作**

- **目录**

```c
#include<dirent.h>
int mkdir(char *path, mode_t mode);
//创建目录

DIR opendir(char *name);
//打开目录

struct dirent * readdir(DIR *dir);	
//返回下一个文件的入口点，若到达目录文件的末尾或出现错误，则返回NULL

int closedir(DIR *dir);
//关闭目录

struct dirent{
  Ino_t	d_ino;									//此目录的i节点号
  ff_t	d_off;									//开始目录至此目录的偏移量
  Unsigned short int  d_reclen;	//文件名长度
  unsigned char d_type; 				//文件类型
  char d_name[NAME_MAX+1];			//文件名
}

```

- **连接文件**
  - **符号链接：**类似于windows中的“快捷方式”。符号链接是一个独立的文件，有自己的i节点，内容保存的是指向真实文件的路径。可以跨越文件系统，创建时原文件可以不存在
  - **硬链接：**与原文件共享同一个i节点，相当于原文件的一个别名；硬链接不可以跨越文件系统，创建时原文件必须存在，不能给目录创建目录链接

```c
int symlink(char *oldpath, char *newpath);
//创建符号链接

int link(char *oldpath, char *newpath);
//创建硬链接
```

**示例**

```c
#include<stdio.h>
#include<stdlib.h>
#include<dirent.h>

int main(){
    DIR *dir;
    struct dirent *dirent;
    char dirname[60];

    scanf("%s",&dirname);

    if(( dir = opendir(dirname)) == NULL){
        perror("Fail ..");
        exit(1);
    }

    while((dirent = readdir(dir)) != NULL){
        printf("%s\t\t%ld\n",dirent->d_name,dirent->d_ino);
    }

    closedir(dir);
    exit(0);
}
```

**总示例**

```c
#include<stdio.h>
#include<sys/types.h>
#include<sys/stat.h>
#include<unistd.h>
#include<stdio.h>
#include<stdlib.h>
#include<string.h>
#include<pwd.h>
#include<grp.h>
#include<time.h>
#include<dirent.h>

long int process_file(char filename[], char dirname[]);
int process_dir(char dirname[]);
void mode_to_letter(int mode, char str[]);


int main(int argc, char *argv[])
{
        char mypwd[301];
        memset(mypwd, 0, sizeof(mypwd));
        getcwd(mypwd, 300);
        int i = 1;
        //无参数
        if(argc == 1){
                if(!process_dir("./"))
                        exit(1);
        }
        else{
        //有参数
                for(;i < argc;i++){
                        chdir(argv[i]);
                        if(!process_dir(argv[i]))
                                exit(1);
                        chdir(mypwd);
                }
        }
        return 0;
}

int process_dir(char dirname[]){
        //获取文件夹下所有文件名称
        long int total = 0;
        DIR * dir;
        struct dirent * ptr;
        dir = opendir(dirname);
        //处理文件
        printf("%s:\n", dirname);
        while((ptr = readdir(dir)) != NULL){
                //printf("%s\n",ptr->d_name);
                total += process_file(ptr->d_name, dirname);
        }
        printf("total:%ld\n\n", total);
        //关闭目录文件
        closedir(dir);
        return 1;
}

long int process_file(char filename[], char dirname[]){
        //获取名称
        char str[12];
        struct stat fst;
        struct tm *mytime = (struct tm *)malloc(sizeof(struct tm));
        if(lstat(filename, &fst) == 1){
                //文件信息读取失败
                perror("state");
                return 0;
        }
        //读取文件权限模式信息
        mode_to_letter(fst.st_mode, str);
        printf("%s", str);      //文件权限信息
        printf(" %3ld", fst.st_nlink);
        printf(" %s", getpwuid(fst.st_uid)->pw_name);
        printf(" %s", getgrgid(fst.st_gid)->gr_name);
        printf(" %9ld", fst.st_size);
        mytime = localtime(&fst.st_mtime);
        printf(" %d-%02d-%02d %02d:%02d ",mytime->tm_year+1900, mytime->tm_mon+1, mytime->tm_mday, mytime->tm_hour, mytime->tm_min);
        printf(" %s", filename);
        printf("\n");
        return fst.st_size;;
}


void mode_to_letter(int mode, char str[]){
        //初始化
        for(int i = 0;i < 11;i++) str[i] = '-';
        //第一位，文件类型
        if(S_ISDIR(mode))       str[0] = 'd';
        else if(S_ISBLK(mode))  str[0] = 'b';
        else if(S_ISCHR(mode))  str[0] = 'c';
        else if(S_ISSOCK(mode)) str[0] = 's';
        else if(S_ISFIFO(mode)) str[0] = 'f';
        else if(S_ISLNK(mode))  str[0] = 'l';
        //二到十文件权限
        if(mode & S_IRUSR) str[1] = 'r'; 
        if(mode & S_IWUSR) str[2] = 'w'; 
        if(mode & S_IXUSR) str[3] = 'x'; 
        if(mode & S_IRGRP) str[4] = 'r'; 
        if(mode & S_IWGRP) str[5] = 'w'; 
        if(mode & S_IXGRP) str[6] = 'x'; 
        if(mode & S_IROTH) str[7] = 'r'; 
        if(mode & S_IWOTH) str[8] = 'w'; 
        if(mode & S_IXOTH) str[9] = 'x'; 

        str[10] = '\0';
}
```







## 进程控制

**进程**

- **正在内存中运行的程序**

- **进程启动的途径**

  - **手动启动**：**前台进程和后台进程**
  - **调度启动（计划任务）**：通过 `at` 或 `cron` 启动，都是**后台进程**

- **进程的终止**

  - **正常终止**
    - 从main返回
    - 调用exit函数
    - 调用_exit系统调用
    
    exit与_exit
    
    <img src="https://i0.hdslb.com/bfs/album/5cf523c5bf629454db5b9dbb7bedb6cde3f180d3.png" alt="image-20220531193028595" style="zoom:80%;" />
    
  - **异常终止**
    - 被信号终止
    - 调用abort，它产生的SIGABRT信号

- **进程标识**

  **PID（无符号整数）是进程的唯一标识**

  **三个特殊进程**

  - PID=0，调度进程（交换进程/系统进程）：内核的一部分
  - PID=1，init进程：内核启动并运行的第一个用户进程，负责对用户进行初始化，应将系统引导到某个状态。**init进程不能被终止**
  - PID=2，kthreadd内核进程：是一个内核线程，负责指向后台操作

- **进程状态**

  ![image-20220530224156856](https://i0.hdslb.com/bfs/album/ee1c9cb8622696b3358c26a0169bfb18711baed4.png)

  - **运行态：**指在CPU中运行或就绪的状态，包括：内核运行态、用户运行态、就绪态

  - **可中断睡眠态：**处在此状态的进程，系统不会调度该进程执行，当系统产生一个中断或释放了其正在等待的资源，或进程收到一个信号，都可以被唤醒而进入就绪态

  - **不可中断睡眠态：**不是指不响应外部的硬件中断，而是指进程不响应异步信号，只有wake_up()显式的唤醒

  - **暂停态：**当进程接收到**SIGSTOP、SIGTSTP、SIGTTIN或SIGTTOU**信号时会进入暂停态，可向其发送**SIGCONT**信号唤醒

  - **僵尸态：**当进程已经停止运行，但其父亲没有响应其信号，则该进程处于僵死态

- **进程控制块**

  **内核通过PCB（Process Control Block）对进程的执行进行控制和管理**。Linux中PCB由task_struct结构体定义

  - **PID：进程标识**

  - 进程状态；

  - 进程资源清单：包括拥有的设备、打开的文件；

  - 进程的优先级

  - CPU现场保护区

  - 其他信息：如PPID、用户ID、组ID等

    ```c
    #include<unistd.h>
    pid_t getpid();
    //获取当前进程的PID
    pid_t getppid();
    //获取当前进程父进程的PID
    ```

    

**进程创建**

- 使用**fork（vfork）**系统调用来创建一个进程
- **fork(vfork)创建的子进程将会复制父进程的数据空间、堆和栈，但会共享代码段**

![image-20220530224919911](https://i0.hdslb.com/bfs/album/6238e255bf552a34b987d56fc33f3ee13ca64005.png)

```c
#include<unistd.h>
pid_t fork();
//父进程返回大于0的值
//子进程返回1
//失败返回-1

eg：
#include<stdio.h>
#include<stdlib.h>
#include<unistd.h>

int main(){
    pid_t pid;
    char *message;
    int n = 10;
    printf("fork program starting...\n");
    //创建子进程
    pid = fork();
    switch(pid){
    case -1:
            perror("fork fail...");
            exit(1);
            break;
    case 0:         //子进程
            message = "This is the child(%d)...\n";
            n = 5;
            break;
    default:
            message = "This is the parent(%d)...\n";
            break;
    }
    //从此，父子进程按给自变量执行相同代码
    for(;n > 0; n--){
            printf(message,getpid());
            sleep(2);
    }
    exit(0);
}
```

- **vfork调用**，同fork；与fork不同的是**vfork需与execve()或exit系统调用配合使用**。在vfork调用中，**子进程先运行，父进程挂起，直到子进程调用exec或_exit**，在这以后，父子进程的执行顺序不再有限制，另外vfork建立的子进程与父进程共享数据段。

  **示例**

  ```c
  #include<stdio.h>
  #include<stdlib.h>
  #include<unistd.h>
  
  int main(){
      pid_t pid;
      char *message;
      int n = 10;
  
      printf("fork program starting...\n");
      //创建子进程
      pid = vfork();
      switch(pid){
      case -1:
          perror("fork fail...");
          exit(1);
          break;
      case 0:         //子进程
          message = "This is the child(%d)...\n";
          for(;n > 0; n--){
                  printf(message,getpid());
                  sleep(1);
          }
          n = 5;
          break;
      default:
          message = "This is the parent(%d)...\n";
          for(;n > 0; n--){
                  printf(message,getpid());
                  sleep(1);
          }
          break;
      }
      exit(0);
  }
  ```

  

**exec函数族**

- 一个进程调用**exec**启动进程时，该**进程将被新进程完全替换**
- *调用exec并不创建新进程，而是用**指定程序替换进程的正文、数据、堆和栈段**，所以调用exec前后**进程ID**并不改变

- 函数格式

```c
#include<unistd.h>
int execl(char *path, char *arg, …);
int execv( char *path, char *argv[]);
int execle(char *path, char *arg, …, char *envp[]);
int execve(char *path, char *argv[], char *envp[]);
int execlp(char *file, char *arg, …);
int execvp(char *file, char *argv[]);
/*
path：待运行程序的全路径名
file：程序（命令）名称，在PATH路径上搜索
arg, … ：可选的多个命令参数，要求最后一个必须是NULL ; 为了方便第一个参数要求为执行程序的名称。
argv：命令参数指针数组，要求同arg,…
envp：传递给运行程序的环境变量指针数组；若没有此参数，启动进程的环境变量则继承自当前shell，否则为该数组中的变量。
*/
```

- **exec函数族的执行**

  只有 **`execve`** 是系统调用，其他五个都是库函数

  <img src="https://i0.hdslb.com/bfs/album/b36ac5155163fc0c72908888ee605c8a2be794eb.png" alt="image-20220531190410406" style="zoom:80%;" />

- **示例**

```c
char *const argv[] = {"ls", "-l", NULL};
char *const envp[] = {"PATH=/bin:/usr/bin", "TERM=console", NULL};
execl("/bin/ls", "ls", "-l", NULL);
execv("/bin/ls", argv);
excle("/bin/ls", "ls", "-l", NULL, envp);
execve("/bin/ls", argv, envp);
execlp("ls", "ls", "-l", NULL);
execvp("ls", argv);
```



**僵尸进程与孤儿进程**

- **僵尸进程**

  一个已经终止运行、但其父进程尚未对其进行善后处理（释放其PCB块）的进程、

- **孤儿进程**

  使用fork创建的子进程，父进程已经结束，子进程还在运行，这种进程为 **孤儿进程**。这种进程很快会被 **init进程（PID=1）** 收养

**进程等待**

```c
#include<sys/wait.h>
#include<sys/types.h>

pid_t wait(int *status);
/*
等待子进程结束，并阻塞父进程。
返回时将子进程的返回码保存到status中
返回等到的结束的子进程的PID
*/

pid_t waitpid(int pid, int *status, int options);
/*
等待任何进程
option：0或WNOHANG;
WNOHANG指明即使指定子进程的退出状态不能立即得到也不阻塞，而是返回0.
*/

//status判断宏
WIFSIGNALED(status);	//若是因未捕获信号而退出则该宏为非0；
WTERMSIG(status);			//若因未捕获信号而退出，则通过该宏获得信号值；
WIFSTOPPED(status);		//若子进程意外终止，则该宏为非0；
WSTOPSIG(status);			//若因意外终止，则该宏获得引起子进程终止的信号值
```



**守护进程**

- **运行在后台，独立于控制台并且周期性的执行某种任务或等待处理某些发生的事件**
- 常见守护进程
  - init：系统守护进程，PID为1，负责启动各运行层次特定的系统服务
  - keventd：为内核定时任务提供上下文
  - portmap：端口映射，提供RPC程序号映射为网络端口号

- 编写要点

  - **创建子进程，终止父进程**
  - **在子进程中创建新的会话**
  - **改变工作目录**
  - **重设文件创建掩码**
  - **关闭文件描述符**

- **相关函数**

  ```c
  #include<sys/types>
  #include<unitd.h>
  
  pid_t setsid(void);
  //创建新的会话和新进程组，并设置该进程为新进程组的Leader及新会话的leader，该进程组独立于控制终端。返回新进程组的PID
  
  void chdir(char *path);
  //修改工作目录，一般为 "/" "/tmp"
  
  void umask(mode_t mask);
  //设置文件掩码，一般设为umask(0)
  
  int dup(int fno);
  //将文件描述符复制到一个可用的描述符
  
  int dup2(int oldfno, int newfno);
  /*
  让newfno和oldfno描述符共享同一个文件表项
  注：oldfno必须是一个已打开的文件描述符
  常用于实现文件重定向
  */
  ```

  

- 示例

```c
//创建守护进程
#include<stdlib.h>
#include<stdio.h>
#include<fcntl.h>
#include<unistd.h>

void daemonize(void)
{
  pid_t pid;
  if(pid = fork() < 0){
    perror("fork");
    exit(1);
  }
  else if(pid != 0)	//parent
    exit(0);
  setsid();	//创建新对话
  //改变目录到 '/'
  if(chdir("/") < 0){
    perror("chdir");
    exit(1);
  }
  //将标准输入、输出、错误输出定位到/dev/null中
  close(0);
  open("/dev/null", O_RDWR);
  dup2(0, 1);
  dup2(0, 2); 
}
```



**系统日志文件操作**

- **在守护进程运行过程中，为了保存运行过程中的一些信息，一般都通过写日志来完成。**

```c
#include<syslog.h>
void openlog(char *ident, int option, int facility);
/*
打开日志（/var/log/message），可选，若不调用在第一次使用syslog自行调用。
indent：输出日志时加的前缀，默认为程序名称；
option：LOG_PID：日志信息添加PID；LOG_cons：不能写日志时直接输出到控制台；
facility：日志种类：LOG_DAEMON、LOG_CRON
*/

void syslog(int priority, char *format,…..);
/*
写日志
priority：日志信息或等级：LOG_INFO、LOG_ERR、LOG_DEBUG
format：格式字符串，同printf
*/

void closelog();
//关闭日志，可选

#include<stdio.h>
#include<stdlib.h>
#include<syslog.h>

int main(){
        openlog("logTest-----",LOG_PID,LOG_DAEMON);
        syslog(LOG_INFO,"log info ...");
        closelog();
        return 0;
}
```





## 进程通信

- **进程间通信（IPC—Inter Process Communication）：是指在不同进程间传递或交换信息**
- **常见通信方式**
  - **管道**
    - 管道：**半双工，只能单向传送数据**，**且只能在同源进程（在进程创建上具有亲缘关系）间使用**
    - 命名管道：**又称为FIFO队列**，借助于外存解除普通管道只能在同源进程使用的限制
  - **System V IPC**
    - **消息队列**
    - 信号量
    - 共享内存
  - **套接字**：**UNIX域套接字和Internet套接字**
  - 信号：不能称之为真正意义上的IPC，只是简单的事件通知，并不能完成数据传输

![image-20220531201427923](https://i0.hdslb.com/bfs/album/9374cf9162c738baa2ce9a0053b46f8f1796f8c6.png)

**信号**

- **信号是一种软中断**
- **由一个进程发给另一个进程**
- **进程的产生条件**
  - **用户在终端按下一个组合键**
  - 硬件异常
  - **进程调用kill函数发送信号**
  - 当检测到某软件异常时产生信号

- 信号处理

  - 忽略信号
  - 捕获信号
  - 执行默认动作

- 常见信号

  可使用 `kill -l` 查看

  | 信号名  | 含义                                                         |
  | ------- | ------------------------------------------------------------ |
  | SIGINT  | 程序终止信号。当用户按下CRTL+C时通知前台进程组终止进程       |
  | SIGKILL | 用来立即结束程序的运行，不能被阻塞、处理或忽略               |
  | SIGTSTP | 在用户按下挂起键（Ctrl+z）时，系统发送此信号，会造成程序挂起 |
  | SIGSTOP | 同上，但是不能被阻塞、处理或忽略                             |

- **信号的生命周期**

  - **从创建一个信号，并且一直保存，直到内核可以根据这个信号做出相应动作为止，然后引发这个动作**

    ![image-20220601193632587](https://i0.hdslb.com/bfs/album/05f20d77e7f81ec2af8aec75517596c9468c14ca.png)

- **发送信号**

  ```c
  #include<sys/types>
  #include<signal.h>
  int kill(pid_t pid, int sig);
  /*
  向指定进程发送sig信号
  pid：>0，发送指定PID的进程
  		=0，将信号发送给和目前进程所在进程组的所有进程
    	-1，将信号广播给系统内所有进程
    	<-1, 发送信号给PID为pid绝对值的进程
  */
  
  #include<unistd.h>
  int alarm(int second);
  /*
  设定一个定时器，在指定秒数后向进程自身发送一个SIGALRM信号，该信号默认处理是终止当前进程。
  sescode：设置为0，则取消所有闹钟；否则覆盖前一个闹钟并返回剩余秒数。
  函数返回0或剩余的秒数
  */
  
  int puase(void);
  //挂起进程，知道有进程到达
  
  int sleep(int sec);
  //挂起进程，知道金浩到达或过去sec秒，
  //返回剩余秒数
  
  #include<unsitd.h>
  #include<signal.h>
  int raise(int sig);
  /*
  向自己发信号
  等价于 kill(getpid(), sig)
  */
  ```

- **信号的捕获与处理**

  ```c
  #include<signal.h>
  sighandler_t signal(int signum,sighandler_t handler);
  /*
  向内核注册指定信号的处理
  signum：待捕获或忽略的信号；
  handler：捕获信号后由系统回调的函数；可以设为一下特殊值：
  	SIG_IGN：忽略信号
  	SIG_DEL：恢复默认行为
  返回值：成功时返回原定义信号处理函数，失败返回：SIG_ERR
  */
  ```

  - 定义处理函数
  - 使用signal处理
  - 使用完后，恢复默认处理 `signal(signum, SIG_DFL)`

- **信号阻塞**

  ```c
  #include<signal.h>
  int sigprocmask(int how,sigset_t *set,sigset_t *oldset);
  /*
  设置或查询阻塞信号集
  how：
  	SIG_BLOCK：将set中的信号添加到阻塞信号集
  	SIG_UNBLOCK：将set中的信号从阻塞信号集中删除
  	SIG_MASK：将set信号集设置为阻塞信号集
  set：新的信号集，若为NULL则忽略how，只是将原信号集保存到oldset
  oldset：保存原信号集
  */
  
  int sigemptyset(sigset_t *set);
  //清空信号量集
  
  int	 sigfillset(sigset_t *set);
  //初始化信号集，并用系统所有有效信号填充到信号集
  
  int sigaddset(sigset_t *set, int signo);
  int sigdelset(sigset_t *set, int signo);
  //将指定信号添加到信号集或从信号集删除
  
  int sigismember(sigset_t *set int signo);
  //判断指定信号是否包含在信号集中，包含返回1，不包含返回0，失败返回-1
  ```

- **示例**

  ```c
  #include<stdio.h>
  #include<stdlib.h>
  #include<unistd.h>
  #include<signal.h>
  void sig_handler(int num)
  {
      printf("receive the signal %d.\n", num);
      raise(SIGCONT);
      signal(SIGALRM,SIG_DFL);
  }
  
  int main(){
  
      signal(SIGALRM, sig_handler);
      alarm(2);
      pause();
      printf("pause is over.\n");
     exit(0);
  }
  
  #include<stdio.h>
  #include<stdlib.h>
  #include<signal.h>
  
  void handle(int signo){
          int i;
          printf("signal %d is captured....\n",signo);
  
          for(i = 0;i<5;i++){
                  puts("signal is blocked (in signal processing)...");
                  sleep(1);
          }
  }
  
  int main(){
          struct sigaction action;
  
          action.sa_handler = handle;
          action.sa_flags = SA_NODEFER;
          sigemptyset(&action.sa_mask);
  
          sigaction(SIGINT,&action,NULL);
  
                  puts("Hi.....");
                  sleep(5);
  
          return 0;
  }
  ```

  

**管道**

- **特点**

  - **管道是半双工的，数据只能向一个方向流动**

  - **需要双方通信时，需要建立起两个管道**

  - **普通管道只能用于父子进程或者兄弟进程之间（具有亲缘关系的进程）**

  - **命名管道，又称为FIFO队列，借助于外存解除普通管道只能在同源进程使用的限制**

- **无名管道**

  <img src="https://i0.hdslb.com/bfs/album/e4b397dc3ea21d6a3f70f5be3a5735bf2fe10993.png" alt="image-20220601195902378" style="zoom:80%;" />

  ```c
  #include<unistd.h>
  int pipe(int fd[2]);
  /*
  创建管道同时创建两个文件描述符，其中fds[0]已读打开，fds[1]以写打开。
  成功返回0，失败返回-1
  */
  
  #include<stdio.h>
  FILE *popen(char *cmd, char *type);
  /*
  创建一个管道，并fork一个子进程，关闭管道不使用端，在子进程中exec一个shell并执行指定命令，然后等待命令终止。
  cmd：命令
  type：打开方式：r或w
  返回值：成功返回一个文件流指针，失败返回NULL
  */
  
  int pclose(FILE *stream);
  //关闭popen打开的文件流
  
  ```

- 使用无名管道进行通信的步骤如下：
  1. 创建所需的管道
  2. 生成(多个)子进程
  3. 关闭/复制文件描述符,使之与相应的管道末端相联系
  4. 关闭不需要的管道末端
  5. 进行通信活动
  6. 关闭所有剩余的打开文件描述符

- **示例**

  ```c
  #include<stdio.h>
  #include<unistd.h>
  #include<stdlib.h>
  #include<sys/types.h>
  #include<sys/wait.h>
  #include<string.h>
  int main()
  {
          pid_t result;
          int r_num;
          int pipe_fd[2];
          char buf_w[1000], buf_r[1000];
          if(pipe(pipe_fd) < 0){                  //创建管道
                  perror("管道创建失败\n");
                  exit(1);
          }
          result = fork();
          if(result < 0){
                  perror("进程创建失败\n");
                  exit(1);
          }
          if(result == 0){ //子进程
                  close(pipe_fd[1]);
                  close(0);
                  dup(pipe_fd[0]);
                  execlp("grep", "grep", "1.c", NULL);
                  close(pipe_fd[0]);
          }
          else{                   //父进程
                  close(pipe_fd[0]);
                  close(1);
                  dup(pipe_fd[1]);
                  execlp("ls", "ls", "-l", NULL);
                  close(pipe_fd[1]);
          }
          return 0;
  }
  
  #include<stdio.h>
  #include<stdlib.h>
  
  int main(){
          FILE *fin,*fout;
          char line[256];
  
          fin = popen("ls -l","r");
          fout = popen("grep ^d","w");
  
          while(fgets(line, 256, fin) != NULL){
                  fputs(line,fout);
          }
  
          pclose(fin);
          pclose(fout);
          return 0;
  }
  ```



**命名管道——FIFO**

```c
#include<sys/types.h>
#include<sys/stat.h>
int mkfifo(char *pname, mode_t mode);
/*
创建一个命名管道：
	pname：路径
	mode：新建管道文件的权限
	成功返回0，失败返回-1
*/

#include<unistd.h>
#include<fcntl.h>
int mknod(const char *pname, mode_t mode, dev_t dev);
/*
创建一个特殊文件
	pname：路径
	mode：新建管道文件的权限
	dev_t：文件类型，S_IFREG, S_IFCHR, S_IFBLK, S_IFIFO or S_IFSOCK
*/
```

- **编程步骤**
  1. 使用mkfifo或mkmod创建管道文件
  2. 以只读或以只写方式打开（open）管道文件
  3. 以read读取或write写管道
  4. 关闭管道文件

​	**注：默认管道的读写是阻塞的，而且只有两端都打开后才能进行读写**

- **示例**

```c
#include<stdio.h>
#include<stdlib.h>
#include<unistd.h>
#include<sys/types.h>
#include<sys/stat.h>
#include<fcntl.h>

const char *fifopath = "/tmp/myfifo";

//write
int main(){
        int fifo;
        int fd;

        char buf[80];
        int cnt;

        if(access(fifopath,F_OK) != 0){
                fifo = mkfifo(fifopath,0660);
                if(fifo < 0){
                        perror("fifo creat fail...");
                        exit(1);
                }
        }

        fd = open(fifopath,O_WRONLY);
        if(fd < 0 ){
                perror("open fail...");
                exit(2);
        }
        cnt = read(0,buf,80);
        while(cnt > 1){
                write(fd,buf,cnt);
                cnt = read(0,buf,80);
        }

        close(fd);
        exit(0);
}

//read
int main(){
        int fd;
        int cnt;
        char buf[80];

        if(access(fifopath,F_OK)  == -1){
                perror("fifo file is not exist...");
                exit(1);
        }

        fd = open(fifopath,O_RDONLY);
        if(fd < 0){
                perror("open fifo fail...");
                exit(2);
        }

        cnt = read(fd,buf,80);
        while(cnt > 0){
                write(0,buf,cnt);
                cnt = read(fd,buf,80);
        }

        close(fd);

        return 0;
}
```



**消息队列**

- **提供了一种从一个进程向另一个进程发送一个数据块的方法**

- **消息队列是链表队列，它通过内核提供一个struct msqid_ds \*msgque[MSGMNI]向量维护内核的一个消息队列列表**

- **使用key唯一确定消息队列**

- **编程方法**

  ```c
  #include<sys/types.h>
  #include<sys/ipc.h>
  #include<sys/msg.h>
  key_t	ftok(char path,int proj_id);
  /*
  创建一个key
  	path：指定一个路径，在不同的进程中通过约定的path确保可产生相同的msgid。
  	proj_id：一个序数，取值在0-127之间。
  */
  
  int msgget(key_t mkey, int msgflg);
  /*
  创建、打开一个消息队列
  key：消息队列ID，若key为IPC_PRIVATE，创建新的消息队列
  msgflg：
  	IPC_CREAT：若消息队列不存在则创建
  	IPC_EXCL：和IPC_CREAT配合使用，若消息队列存在则失败。
  	同时指定权限：IPC_CREAT|0666
  */
  
  int msgsnd(int msqid, const void *msgp, size_t msgsz, int msgflg);
  /*
  把指定消息插入到指定的消息队列中
  msqid：消息队列ID
  msgp：消息体，应该是一个结构体指针
  msgsz：发送消息的大小
  msgflg：0或IPC_NOWAIT，0：若队列满则被阻塞；IPC_NOWAIT若队列满在立即返回错误。
  返回值：成功为0，失败为-1。
  */
  
  //消息体
  struct msg{
    long	mtype; //消息类型，固定项，必须大于0,用来指定具体
  	···	//自定义项
  }
  
  ssize_t msgrcv(int msqid, void *msgp, size_t msgsz, long msgtyp, int msgflg);
  /*
  从指定消息队列中接收消息
  msqid：消息队列ID
  msgp：消息体，应该是一个结构体指针
  msgsz：接收消息的大小
  msgtyp：接收那条消息，0：队列第一条消息；绝对值>0：接收|msgtype|与msgp的mtype相同的消息
  msgflg：0:若没有消息则阻塞；IPC_NOWAIT：若没有消息则立即返回错误。
  */
  
  int msgctl(int msqid, int cmd, struct msqid_ds *buf);
  /*
  msqid：消息队列ID
  cmd：指定操作
  	IPC_RMID：删除指定的消息队列，buf指定为NULL
  	IPC_STAT：将内核中的消息结构复制到用户空间中的buf中
  	IPC_SET：设置消息队列的有效UID和GID、操作权限等。
  */
  ```

- **示例**

```c
#include<stdio.h>
#include<stdlib.h>
#include<sys/types.h>
#include<sys/msg.h>
#include<sys/ipc.h>
#include<unistd.h>
#include<string.h>

struct msgmbuf{         //消息结构体
        long mtype;
        char msg_text[512];
};

int main()
{
        char name[100];
        printf("请输入你的姓名：");
        scanf("%s", name);
        int s = strlen(name);
        name[s] = ' ';
        name[s+1] = ':';
        name[s+2] = ' ';
        int qid;
        key_t key;
        int len;
        struct msgmbuf msg;
        msg.mtype = 1;
        pid_t pid;
        if((key = ftok(".", 'a')) == -1)
        {
                perror("产生标准key出错\n");
                exit(1);
        }
        if((qid = msgget(key, IPC_CREAT | 0666)) == -1){
                perror("创建消息队列出错\n");
                exit(1);
        }
        printf("创建、打开的队列号是：%d\n", qid);
        pid = fork();
        if(pid < 0) {
                perror("进程创建失败\n");
                exit(0);
        }
        if(pid == 0) {          //子进程，监听
                while(1){
                        //只能接受mtype=2的消息
                        msgrcv(qid, &msg, 512, 2, 0);
                        printf("%s\n",(&msg)->msg_text);
                        memset((&msg)->msg_text, 0, strlen((&msg)->msg_text));
                }
        }
        else{                           //父进程，用来发送消息
                while(1){
                        char str[512];
                        scanf("%s", str);
                        strcpy((&msg)->msg_text, name);
                        strcat((&msg)->msg_text, str);
                        len = strlen(msg.msg_text);
                        msgsnd(qid, &msg, len, 0);
                        printf("%s\n",(&msg)->msg_text);
                }
        }
}
```



