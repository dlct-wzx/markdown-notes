# Markdown学习笔记
[TOC]

## 1.斜体和粗体

源码:

```markdown
*斜体*或_斜体_
**粗体**
***加粗斜体***
~~删除线~~
<u>下划线</u>
```
Typora快捷键

1. 斜体：==ctrl+i==
2. 粗体：==ctrl+b==
3. 加粗斜体：==ctrl+b+i==
4. 删除线：==alt+shift+5==
5. 下划线：==ctrl+u==

显示效果:

1. *斜体*或_斜体_
2. **粗体**
3. ***加粗斜体***
4. ~~删除线~~
5. <u>下划线</u>

##    2.分级标题

源代码：

第一种写法：

```markdown
这是一个一级标题
==================
这是一个二级标题
------------------
```
第二种写法：

```markdown
# 一级标题
## 二级标题
### 三级标题
#### 四级标题
##### 五级标题
###### 六级标题
```

Typora快捷键：

==ctrl+数字==

## 3.超链接



### 3.1 行内式

语法说明：

* []内写链接文字，()里内写链接地址，()中的“”可以为链接指定的title属性，title可写可不写。title属性是指鼠标在链接上悬停会出现title文字。`[链接文字](链接地址 "链接标题")，`地址与标题之间必须要有一个空格。

源代码：

```markdown
欢迎来到[王泽玺的仓库](https://gitee.com/wang-zexi/projects)
欢迎来到[王泽玺的仓库](https://gitee.com/wang-zexi/projects "王泽玺的仓库")
```

Typora快捷键：

==ctrl + k==

显示效果:

1. 欢迎来到[王泽玺的仓库](https://gitee.com/wang-zexi/projects)
2. 欢迎来到[王泽玺的仓库](https://gitee.com/wang-zexi/projects "王泽玺的仓库")



### 3.2参考式

参考式一般用于学术论文或者一个连接多次使用

语法说明:

* 参考式链接分为两部分，文中写法为`[链接文字][链接标记]`,在文本的任意位置`[链接标记]:链接地址 “链接标题”`，记得地址与标题间的空格,任意位置最起码离最后一个链接空一行

```markdown
我常去的网站[CSDN][1]、[Google][2]以及[我的码云][3]
[Google搜索][2]非常的好使。

[1]:https://www.csdn.net "CSDN"
[2]:https://www.google.com "Google"
[3https://gitee.com/wang-zexi/projects "dlct's gitee"
```

我常去的网站[CSDN][1]、[Google][2]以及[我的码云][3]
[Google搜索][2]非常的好使。

[1]:https://www.csdn.net "CSDN"
[2]:https://www.google.com "Google"
[3]:https://gitee.com/wang-zexi/projects "dlct's gitee"



### 3.3自动链接

语法说明:

Markdown支持以比较简短的自动连接来处理网址和邮箱，<>。

```markdown
<http://www.baidu.com>
<18109232165@163.com>
```

显示效果：

<http://www.baidu.com>

<18109232165@163.com>



## 4.锚点

一般用于目录的制作，一般只能在标题后插入锚点

语法说明:

在准备跳转的指定标题后插入锚点{#标记}，然后再文档的其他地方协商链接锚点的链接

源代码:

```markdown
# Markdown学习笔记{#index}

跳转到[标题](#index)
```

显示效果：

跳转到[标题](#index)

## 5.列表

### 5.1无序列表

使用*，+，-表示无需列表

源代码：

```markdown
-	无序列表1
*	无序列表2
+	无序列表3
```

显示效果：

- 无序列表1
- 无序列表2
- 无序列表3



### 5.2 有序列表

数字接着一个英文句点，换行列表会继承，按Ctrl+[消除

源代码：

```markdown
有序列表1
有序列表2
有序列表3
```

显示效果：

1. 有序列表1
2. 有序列表2
3. 有序列表3



### 5.3 包含引用的列表

语法说明:

如果要在列表项目内放进引用，那>就需要缩进

源代码:

```markdown
*	阅读方式：
>打开书本
>打开台灯
```

显示效果:

* 阅读方式：

> 打开书本
>
> 打开台灯



## 6. 引用

语法说明：

引用需要在被引用的文本钱加上>符号。

源代码

```markdown
> 11111
> 22222
> 33333
> 
> 44444
> 55555
```

Typora快捷键：

ctrl + shift + q

效果展示：

> 11111
> 22222
> 33333
>  
> 44444
> 55555

Markdown允许只在整个段落的第一行前面加上>

源代码：

```markdown
> 1111,
2222.
3333.
> 4444,
5555.
```

显示效果：

> 1111,
2222.
3333.
> 4444,
5555.

### 6.2 引用的多层嵌套

区块引用可以嵌套（例如：引用内的引用），只要根据层次加上不同数量的>

源代码：

```markdown
> 一层引用
>> 二层引用
>>> 三层引用
```

效果展示

>一层引用

> >二层引用

> > >三层引用

### 6.3 引用的其他要素

引用的区块内也可使用其他的Markdown语法，包括标题、列表、代码区块等

源代码：

```markdown
> 第一行
> 第二行 
> 有一行代码
> ```
> return shell_exec("echo $input | $markdown_scropt");
> ```
```

效果演示：

> 第一行
> 第二行 
> 有一行代码
> ```
> return shell_exec("echo $input | $markdown_scropt");
> ```

## 7.插入图像

图片的创建方式与超链接相似，而且和超链接一样也有两种写法，行内式和参考式写法。(也可以直接拖拽，自动生成地址)

语法中Alt的意思是如果图片因为某些原因不能显示，就用定义的图片Alt文字来代替图片。图片Title则和链接中的Title一样，表示鼠标悬停在图片上是出现的文字。Alt和Title都不是必须的，可以省略，但建议加上。

### 7.1 行内式

语法说明：

`![图片Alt](图片地址 "图片")`

源代码

```markdown
风景图:
![风景图 Alt](/home/dlct/图片/风景图.webp "风景图")
```

Typora快捷键：

==ctrl + shift + i==

风景图:
![风景图 Alt](/home/dlct/图片/风景图.webp "风景图")

### 7.2 参考式

语法说明：

在文档中要插入图片的地方写`![图片Alt][标记]`
在文档的最后写上`[标记]:图片地址 "Title"`

源代码：

```markdown
风景：
![风景图	][the]
[the]:/home/dlct/图片/风景图.webp "风景图"
```

风景：
![风景图	][the]

[the]:/home/dlct/图片/风景图.webp "风景图"



## 8. 内容目录

在段落中填写`[TOC]`以显示全文内容的目录结构。
效果参见最上方的目录

## 9. 注脚

语法说明：
在需要添加注脚的文字后加上注脚名字`[^注脚名字]`，成为加注。然后在文本的任意位置（一般在最后）添加注脚，注脚前必须有对应的注脚名字。

注：注脚与注脚之间必须空一行，不然会失效。即使你没有把注脚写在最后，经Markdown转换后，也会自动归类到文章的最后。点击注脚后的链接可以直接跳回加注的地方。

```markdown
使用 Markdown[^1]可以效率的书写文档, 直接转换成 HTML[^2], 你可以使用 Leanote[^Le] 编辑器进行书写。

[^1]:Markdown是一种纯文本标记语言

[^2]:HyperText Markup Language 超文本标记语言

[^Le]:开源笔记平台，支持Markdown和笔记直接发为博文
```

效果演示：

使用 Markdown[^1]可以效率的书写文档, 直接转换成 HTML[^2], 你可以使用 Leanote[^Le] 编辑器进行书写。

[^1]:Markdown是一种纯文本标记语言

[^2]:HyperText Markup Language 超文本标记语言

[^Le]:开源笔记平台，支持Markdown和笔记直接发为博文

## 10. LaTeX 公式

### 10.1 $表示行内公式

源代码:

```markdown
质能方程可以用一个很简洁的方程式 $E=mc^2$ 来表示
```

显示效果：

质能方程可以用一个很简洁的方程式 $E=mc^2$ 来表示

### 10.2 $$表示整行公式

源代码：

```markdown
$$\sum_{i=1}^n a_i=0$$

$$f(x_1,x_x,\ldots,x_n) = x_1^2 + x_2^2 + \cdots + x_n^2 $$

$$\sum^{j-1}_{k=0}{\widehat{\gamma}_{kj} z_k}$$
```

显示效果：

$$\sum_{i=1}^n a_i=0$$

$$f(x_1,x_x,\ldots,x_n) = x_1^2 + x_2^2 + \cdots + x_n^2 $$

$$\sum^{j-1}_{k=0}{\widehat{\gamma}_{kj} z_k}$$

## 12. 表格

语法说明：

1. 不管是哪种方式，第一行为表头，第二行分隔表头和主体部分，第三行开始每一行为一个表格行。
2. 列于列之间用管道符|隔开。原生方式的表格每一行的两边也要有管道符。
3. 第二行还可以为不同的列指定对齐方向。默认为左对齐，在-右边加上:就右对齐。

源代码：

```markdown
姓名|性别|成绩
-|-|-
小明|男|99
小红|女|98
小华|男|97
```

Typora快捷键：

==ctrl + t==

显示效果：

| 姓名 | 性别 | 成绩 |
| ---- | ---- | ---- |
| 小明 | 男   | 99   |
| 小红 | 女   | 98   |
| 小华 | 男   | 97   |

## 13. 分隔线

你可以在一行中用三个以上的星号、减号、底线来建立一个分隔线，行内不能有其他东西。你也可以在星号或是减号中间插入空格。下面每种写法都可以建立分隔线：

源代码：

```markdown
***
*****
---------------
```

效果演示：

***

---------



































