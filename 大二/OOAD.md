# OOAD

[TOC]

## 第一章 面向对象方法概论

**面向对象的发展史**

OOA/D的发展历程具有众多分支，其中Alan Kay发明的 Smalltalk语言贡献最为突出

- 雏形阶段
  - 60年代，挪威Simula 67首次使用类和继承概念
  - 70年代，CLU、并发Pascal、Ada、Modula-2开始支持数据 和操作的封装
  - 72年，Smalltalk-72使用“面向对象”这一术语
- 完善阶段
  - **81年，Smalltalk-80具备了面向对象的大多数基本概念和支持 机制，被认为是第一个完善的、能够实际应用的面向对象语言 （OOPL）**
- 繁荣阶段
  - 80年代中期至90年代，出现了C++、Object-C、Object  Pascal、Eiffel、Actor、Java
  - 目前，普遍采用语言、类库、可视化编程环境相结合的方法， 如Visual C++、Java、C#、Visual Basic、Delphi等。

**软件开发**

- 60年代，自由编程没有方法
- 功能分解法：自上而下分解子功能，定义接口。缺点：无法深入描述问 题域，对需求适应性差
- **结构化方法：**软件按功能组织，相比功能分解法更强调对问题域的分析。 缺点：数据和操作结合得不紧密，适合功能稳定的科学计算，但不适合 功能随市场变化的企业和商业软件
- 信息建模方法：以信息实体为构造块，以数据结构为中心来开发软件。 缺点：对功能的处理较弱
- **面向对象方法（OOM）**在继承传统方法抽象与模块化等概念 的基础上，软件模型是问题域的完整和直接映射，分析、设 计和编程采用一致的概念和表示

**面向对象方法的基本思想**

- 客观世界中的事物都是对象，对象间存在一定关系，复杂对象由简单 对象组成
- 具有相同属性和操作的对象属于一个类，对象是类的一个实例
- 类之间可以有层次结构，子类继承父类的全部属性和操作，且可有自 己的属性和操作
- 类有封装性，隐藏或公开自己的属性或操作；对象只能通过消息请求 其他对象或自己的操作
- 强调运用人类日常思维方法

**面向对象的思考方式**

- <img src="https://i0.hdslb.com/bfs/album/13f558e875b3bfcb18baaa4864e665b090c90508.png" alt="image-20220603181017187" style="zoom:67%;" />

- **面向对象与面向过程的比较**
  - 面向过程侧重于考虑方法的编写（哪个方法做什么事，不考 虑所涉及的数据在哪里）
  - 面向对象则致力于将数据和方法先做一个封装（分配一个对 象做事，先考所需要的数据是否和它在一起）
  - 过程化解决方法通过信道传递数据，服务器端需要有专门的工具对接受的数据进行处理
  - 面向对象解决方法通过信道传递对象（数据+对数据的处理 方法）



**面向对象方法的优点**

- 与人们认识世界的方法相对应
- 使客观世界到计算机语言的鸿沟变窄，面向对象语言比非面向对象语言 **更接近** 问题域
- 面向对象方法使问题域和计算机的鸿沟变窄
- 易于维护和复用
- 提高软件质量和生产效率
- 提高软件质量和生产效率



**面向对象的基本概念和基本原则**

<img src="https://i0.hdslb.com/bfs/album/bd3c8833e13a39463887294858e4fee4ca25967b.png" alt="image-20220603181245659" style="zoom:67%;" />

**面向对象的基本概念**

- **对象（Object）**

  - 是系统中用来描述客观事物的一个实体

  - 它是构成系统的基本单位

  - 由一组属性和施加于这组属性的一组操作构成

  - **对象中的属性（Attribute）**

    用来描述对象**静态特征**的一个数据项

  - **对象中的操作（Operation）**

    用来描述对象**动态特征（行为**）的一个动作序列

- **类（class）**
  - 相同属性和操作的一组对象属于同一个类
  - 它为属于该类的全部对象提供了统一的抽象描述
  - 由一个类名、一组属性和一组操作构成
  - 同一个类的对象之间，属性值可不同，操作完全相同
  - **类用于创建对象，对象是类的实例**
  - 属性state\==信息information\==数据data==状态state
  - 操作operation == 方法Method ==行为behaviour == 职责responsibility

- **继承（inheritance）**

  - 特殊类自动拥有其一般类的全部属性和操作，称为特殊类对一般类的**继承**，也称一般类对特殊类的**泛化**
  - 继承有传递性，简化了人们对事物的认 识和描述，有益于软件复用

  <img src="https://i0.hdslb.com/bfs/album/720343704676c224027188ebd35f88fd543daf3c.png" alt="image-20220603181535338" style="zoom:50%;" />

- **关联(Association)**
  - **关联** 刻画不同类别事物之前的关系
  - 类之间的静态关系
  - <img src="https://i0.hdslb.com/bfs/album/b86c26f9bf38efec00d065c2b6fb331da7bbbca6.png" alt="image-20220603181650855" style="zoom:67%;" />
- **聚合/组合(Aggregation/ Composition)**
  - **聚合（Aggregation）**
    - 一个（较复杂）对象由其他若干（较简单）对象作为其构成 成分，这种对象间关系称为聚合；如：大学是由学生和老师 组成的
    - 具有传递性和不对称性，是关联的一种
    - <img src="https://i0.hdslb.com/bfs/album/bdc8eb8798b4e656950395f61fe0a9548dede19a.png" alt="image-20220603181807400" style="zoom:67%;" />
  - **组合（Composition）**
    - 聚合关系的一个变种，称为组合。整体控制着部分的生命
    - 部分对象只能存在于整体对象之中，整体对象控制部分对象的生命周期

**面向对象的基本原则**

- **抽象（Abstraction）**

  - 从事物中**舍弃**个别的、非本质的特征，**保留**共同的、本质特征的做法
  - **抽象是面向对象领域发现类的主要方法**
  - <img src="https://i0.hdslb.com/bfs/album/c0e83865b77f491b234cd964f8bfb0a8b0195e27.png" alt="image-20220602220217076" style="zoom: 67%;" />

- **分类(Classification)**

  - 较多地注意事物间的差别，把具有相同属性和操作的对象划分一类

- **封装（encapsulation）**

  - 用对象把属性和操作包装起来，形成一个独立的实体单位，并尽量对外隐蔽内部细节

  - 为什么封装：保护隐私、保护数据安全、隔离复杂度

  - 封装的四种方式

    <img src="https://i0.hdslb.com/bfs/album/b840e9eecc7d0e299d34b271170962818a4f527d.png" alt="image-20220603182047265" style="zoom:80%;" />

- **多态性（polymorphism）**

  - 特殊类可定义同名的属性或操作，来代替继承来的属性或操作
  - 一般类中的属性或操作，在不同特殊类中可有不同的 定义
  - 多态的核心思想，是设计模式的基础：使**用指向父类的指针或者引用， 能够调用子类的对象**

- **接口/实现 (Interface /Implementation)**

  - **接口Interface**

    描述一个类的用户如何与这个类交互

  - **实现Implementation**
  - <img src="https://i0.hdslb.com/bfs/album/9fba5c635bac66dd81103c6f47942babdb21f80a.png" alt="image-20220603182355342" style="zoom:80%;" />

- **消息（message）**

  - 向一个对象发送的操作 **请求**，称为消息
  - 对象之间通过消息进行通信，实现对象之间的 **动态联系**
  - 在C++中是函数调用，在Java中是方法激活

- **动态行为分析**

  - 用对等（关联）和层次（继承和聚合）描述类间关系， 称为静态模型（或结构模型）
  - 按属性值，可把对象划分为不同的状态，请求对象操 作会引起状态变化，用状态转化图表示
  -  对象间发送消息，协同完成某项功能，用交互图（即 写作图和顺序图）表示
  - 用主动对象和被动对象表示并非行为

- **主动对象（active object）** 

  - **至少有一个**操作不需要接收消息就可主动执行的对象
  - **所有**操作必须接收消息才能执行的对象，称为被动对象
  - 在**多**任务并发执行的系统中，存在**多个**主动对象

- **复杂性控制**

  系统分为若干 **包（package）**，把类图中按模型元素之间关系的紧密程度，把模型元素组织到各个包中



## 第二章 什么是面向对象分析

**OO方法的三个阶段**

- **面向对象分析（OOA）**

  不考虑实现，只找出所需对象及对象间关 系，一般会确定对象有哪些属性和操作

- **面向对象设计（OOD）**

  根据与实现有关的因素，定义对象中操作 的实现，对OOA模型修改和补充，得OOD 模型

- **面向对象编程（OOP）**

  按OOD模型，进行编程实现

- OOA和OOD的**界限有时是模糊的**



**OOA面临的主要的问题**

- 问题域和系统责任的复杂性日益增长

- 问题域

  被开发系统的应用领域，即系统的业务范围

- 系统责任

  所开发的系统应该具有的功能

- 交流问题
  - 开发人员与领域专家交流
  - 开发人员之间的交流
  - 开发人员与管理人员交流
- 需求的不断变化
- 软件复用的要求



**模型**

- **建模 modeling**
  - 重要的研发成果常常产自类比（analogy）
  - 把不太理解的东西和一些已经较为理解、且十分类似的东西做比 较，可以对这些不太理解的东西产生更深刻的理解，叫做建模
- **模型**
  - 建模产生的结果就是模型，模型是对现实的简化、对事物的一种抽象
  - 模型可以帮助人们更好地了解事物的本质，抓住问题的要害
  - 在模型中，人们总是剔除那些与问题无关的、非本质的东西，从 而使模型与真实的实体相比更加简单、易于把握
- **建模是为了能够更好地理解正在开发的系统**
- **建模的四个目的**
  1. 帮助我们按照需要对系统进行**可视化** 
  2. 允许我们详细**说明系统的结构和行为**
  3. 给出了一个指导我们**构造系统**的模板
  4. 对我们所做出的决策进行**文档化**
- **建模的四项基本原理**
  1. 选择要创建什么模型
  2. 每一种模型可以在不同的精度级别上表示
  3. 最好的模型是与现实相关联的
  4. 单个模型是不充分的, 对每一个重要的系统最好用一组 几乎独立的模型去处理

![image-20220603190917698](https://i0.hdslb.com/bfs/album/cd1e7d77f16fba94063814d5340d23a53e55b5df.png)





**OOA模型**

- **需求分析：**研究问题域，产生一个满足用户需求的系统分析模型
- OOA模型如下

<img src="https://i0.hdslb.com/bfs/album/04a81a75898da15551bdcb38b5d58116335dc62a.png" alt="image-20220603185633562" style="zoom:80%;" />

**OOA过程**

![image-20220603101026329](https://i0.hdslb.com/bfs/album/d6d020df0add38bd18ffb2d2ca58096bb7f81dde.png)

**UML**

- **UML（统一建模语言）**是一种为面向对象系统的产品进行说明、可视化和编制文档的一种标准语言
- UML只是一种建模语言，而不是一种建模方法

- UML的构造块

- ![](https://i0.hdslb.com/bfs/album/18d19e40c9bb79deefb1466b96a72fb98789519c.png)

  <img src="https://imgconvert.csdnimg.cn/aHR0cHM6Ly9tbWJpei5xcGljLmNuL21tYml6X3BuZy9IblVkNTZWSGlhZjEyV3A4TnFCMkN6V2ljSnhYYzlyNDV3b1VzMmlhN21pYjBGRWFGdmVlbVIxOXF0MWlhOFJvdXlMMmZpY0YxbmhwOW5sbVNLSnBzN01FOXVkdy82NDA?x-oss-process=image/format,png" alt="img" style="zoom:80%;" />

![image-20220604110024205](https://i0.hdslb.com/bfs/album/c7b4ff5a8875b63bc46e42455dd3a7f8c6c42e44.png)

**UML的概念模型**

- UML的语法和语义规则

  -  命名 ：为事物、关系和图起的名字
  - 范围 ：使名字具有特定含义的语境
  - 可见性 ：这些名字如何让其他成分看见和使用
  - 完整性 ：事物如何正确 、一致地相互联系
  - 执行 ：运行或模拟动态模型的含义是什么

- 图符：**每个建模元素都有子集特定的图形符号**

- UML常用符号

  ![image-20220603190226515](https://i0.hdslb.com/bfs/album/798d32a7577b79ff6bd3af498b48ed1696d57ed0.png)



![image-20220603190650718](https://i0.hdslb.com/bfs/album/f7d25ba79547ffb2aef5ae60c8f6c93c2d2d65ba.png)





## 第三章 建立需求模型——用况图

**用况图（use case diagram）**

- 对一个系统的参与者、用况以及它们之间的 关系进行可视化表示的模型图，称为用况图

- 作用

  - 以直观形式展示了系统的用户需求
  - 是系统的需求模型

- 用况图的构成元素

  ![image-20220603190528809](https://i0.hdslb.com/bfs/album/d38092c07cf9aa0e7801a301b45ed13d0994bac6.png)



**系统边界：是一个系统所包含的所有系统成分与系统以 外各事物的分界线**

<img src="https://i0.hdslb.com/bfs/album/b99bf956c1a0156fa0cd076080dcfb3572bb0b47.png" alt="image-20220603101233722" style="zoom:67%;" />

**现实事物的四种情况**

- **位于系统边界内**

  如超市商品销售系统中的商品

- **参与者，且系统中没有相应成分与之对应**

  收款员

- **既有系统内成分作为其抽象描述，又在系统外与系统交互**

  收款员

- **属于问题域，但与系统责任无关**

  保安员、保洁员

- 注意：已开发的软件系统，位于边界外。

**参与者（Actor）**

- 是在系统之外（透过系统边界）与系统进行交互的任何事物
- 定义了一组在功能上密切相关的角色
- 与系统的关系
  - 向系统发出请求，系统以某种形式响应
  - 系统也可向参与者发出请求，参与者予以响应![image-20220603101433212](https://i0.hdslb.com/bfs/album/5a22f0d8397bd843f1cd9a17f38e6758841a369f.png)
- **参与者之间的继承关系**
  - 特殊参与者可继承一般参与者放出请求的能力
  - **特殊参与者有一般参与者的所有权利，而一般参与者没有特殊参与者的特殊权利**

<img src="https://i0.hdslb.com/bfs/album/5ad1f3b2dcc40c85378ccddbfcac19827f2c15c4.png" alt="image-20220603101751561" style="zoom:50%;" />

- **识别参与者**

  - 人员

    从可直接使用系统的人员中发现参与者

  - 外部系统

    外部已开发投入使用的应用系统

  - 设备

    监视器、键盘通常不被看做参与者

    外部传感器、马达则可能是参与者

![image-20220603190632009](https://i0.hdslb.com/bfs/album/e321c874ea5e9bb54b41175c38416b098f2ee991.png)





**用况（use case）**

- 对用户需求的规范化描述
- 为开发人员提供认识和理解系统的技术
- 为领域专家、最终用户和开发者提供一种相互交流的手段
- 可作为人机界面的设计基础，也可用于制作测试用例

- **一个用况的功能**
  - 描述**系统级**的一项功能，把这样的功能描述 为一组动作序列，系统执行该动作序列，为参与者产生一个可观察的结果值；其中的每个序列表示参与者与系统的一次交互
  - **强调参与者和系统彼此为对方做了什么，不关心怎么做，也不关心间接做了什么**
  - 既表达了系统的功能需求，也表达了系统的 功能划分
  - 描述的系统功能是相对完整的，而不是其中 的小片段，但也不要过于综合

- 用况与参与者之间的关系

  - 一个参与者可以和多个用况交互

  - 一个用况可以和多个参与者交互

  - 关联是参与者和用况的唯一关系

    <img src="https://i0.hdslb.com/bfs/album/5231bba32d0e30c6aac4ed8d014fdec3276bc514.png" alt="image-20220603102126560" style="zoom:67%;" />

- **用况之间的关系**

  - **包含（include）**

    - 把两个或多个用况中重复的行为放在一个新 用况中，原有用况中某一位置引入新用况

    - 基用况使用被包含用况的结果

  <img src="https://i0.hdslb.com/bfs/album/96d42d85385153467dcac6162c1c13c83213cda3.png" alt="image-20220603102219208" style="zoom:67%;" />

  - **扩展（extend）**

    - 在一个或多个用况中存在可选的行为片段
    - 把该片断抽取出来，形成新片段
    - 在原用况中删除片段的位置（即扩展点）对新片段进行扩展

    <img src="https://i0.hdslb.com/bfs/album/7c4534e687a2bfdf31f5c0b7ecf2e97c25c7c1b6.png" alt="image-20220603102426280" style="zoom:67%;" />

  - **继承/泛化**

    与类的继承一样，特殊用况继承一般用况的 行为和含义，而且可增加行为或覆盖一般用 况的行为

    <img src="https://i0.hdslb.com/bfs/album/8725a30169a3be416f4f01f8a83138474a74a106.png" alt="image-20220603102519024" style="zoom:80%;" />

![image-20220603191029835](https://i0.hdslb.com/bfs/album/d40e3418ab883178ad3ddfa5ea55d58c2cd17bf2.png)



**用况图**

![image-20220603102550713](https://i0.hdslb.com/bfs/album/d32f51953b93e222d4e8eefbaf5f12e41ec3f073.png)

**实例：学籍管理功能有登录、选课、查看学分三种功能**

1. 登录包含选课查看学分

   <img src="https://i0.hdslb.com/bfs/album/77d203dcb61b495ac29b1d38ec8da7085a53823a.png" alt="image-20220603102720651" style="zoom:67%;" />

2. 让所有用况都包含“登录”

   <img src="https://i0.hdslb.com/bfs/album/ef8b45879e8bbc26fec6ed671ea01d6050b20270.png" alt="image-20220603102748954" style="zoom:67%;" />

3. 使用扩展设计“登录”用况

   <img src="https://i0.hdslb.com/bfs/album/b8fb30bdbfd706c70f6643219c2c1a0d2e9e0d72.png" alt="image-20220603102805228" style="zoom:67%;" />

4. 用况“登录”独立于其他用况，必须在其他用况中指定 **前置条件**

​	<img src="https://i0.hdslb.com/bfs/album/64c2c7781b324700e499a92661aae5cc29492944.png" alt="image-20220603102837127" style="zoom:67%;" />

**用况规约**

![image-20220603191109342](https://i0.hdslb.com/bfs/album/1892538e6dae682db70650d00dd13fa4c114bbcb.png)

![image-20220603191117798](https://i0.hdslb.com/bfs/album/bee6aa63030ab43759bc3aa3c7da21f227bed4fe.png)

**eg**:

![image-20220603191139949](https://i0.hdslb.com/bfs/album/861dacfb8feb75afb926fdf381370dfb76c61a5c.png)



**用况模型**

- 用况模型包括
  - 系统边界
  - 参与者
  - 用况
  - 用况图
  - 用况规约
- 用况模型是系统分析的结果、是系统设计的输入

![image-20220603191316795](https://i0.hdslb.com/bfs/album/5331b4f43576ca6cee89fe1aaef8f79da0d5a431.png)





## 第四章 建立基本模型——类图

- 在OO方法中，类图是**最重要的图**
- 它描述了系统中各对象的类型和它们之间的关系
- 注重表达系统的**静态结果**

**面向对象分析的主要步骤**

- 识别对象
- 组织对象
- 定义对象之间的关系
- 定义对象的操作
- 定义对象内部细节



**对象**

- 对象是具有明确语义边界并封装了状态和行为的**实体**
- 对象是系统中描述客观事物的一个实体，是系统的基本单位
- 有一组属性和作用在属性上一组操作组成

**类**

- **对具有相同属性、操作、关系和语义的对象集合的抽象**
- 对属于该类的全部对象提供统一的描述



**类的图形表示  **

- 在显示时，只有名称部分是必须的，其余部分可以**隐藏**

![image-20220603194713287](https://i0.hdslb.com/bfs/album/1110ff89deb3a766197abe46dbaf66ba73f221fa.png)

<img src="https://i0.hdslb.com/bfs/album/9d16048e5e3484287377e40a6365ec1fc54e71d5.png" alt="image-20220603195200059" style="zoom:67%;" />





**创建类图过程**

- **识别对象和类**

- **审查与筛选**

  - 舍弃无用的对象
  - 精简对象

- **抽象出类，并进行调整**

  - 对象分类
  - 对类进行调整

- **识别主动对象**

  - 主动对象是拥有线程或进程，并启动控制活动的对象
  - 主动对象是线程或进程中最先开始执行的对象
  - 被动对象除了不能拥有线程或进程，与主动进程没有区别

  ![image-20220603195247167](https://i0.hdslb.com/bfs/album/fa5562c80d025d9c17388795a9c63e15581135de.png)

- **类的命名**

  类名中的每个词的第一个字母通常要大写

- **建立类图的对象层**
- **定义属性和操作**
  - 属性名除第一个单词之外的每个单词的第一个字母要大写
  - [可见性] 属性名[:类型] [=初始值] [{约束串}]  
  - 可见性 :公有的(+)，受保护的(#)，私有的(-)，包范围的(~)
  - ![image-20220603195617688](https://i0.hdslb.com/bfs/album/1aeb278b65fd1bdf313d4cc14f4b06408441a2eb.png)
  - 操作名除第一个词之外的每个单词的第一个字母要大写
  - [可见性] 操作名 [(参数列表)] \[:返回类型][{约束串}]
  - ![image-20220603195735243](https://i0.hdslb.com/bfs/album/7437f94580f009d7a541c6b2391cf24df70dd350.png)

- **建立关系**



**类之间的关心**

- **继承**

  - 如果类A具有类B的全部属性和操作，且还有 自己特有的一些 属性和操作，则A称为B的特 殊类，B称为A的一般类

  - 单继承 ：只继承一个一般类

  - 多继承 ：继承了多个一般类

  - 抽象类

    - 包含至少一个操作，没有定义其怎么实现
    - 一般类的抽象操作的特征标记在特殊类中出现，且不是抽象的 ，则称特殊类实现了该操作
    - 不同特殊类有不同的对抽象操作的实现，称为“多态”现象
    - 含有抽象操作的类，不能被实例化

  - 抽象操作的表示 ：用斜体的特征标记 ；或者，在操作名后 加上{abstract}

  - 抽象类的表示 ：用斜体的类名表示； 或者，在类名后加上 {abstract} 

  - **继承的表示**

    ![image-20220603200121304](https://i0.hdslb.com/bfs/album/cc2393a5e71f769a6da18c2bbdaf819e35a87464.png)

- **关联**

  - 静态关系

    - 最终可通过**对象属性**来表示的一个对象与另一个对象的 联系
    - 例：“教师”为“学生”“指导论文”， 两个“城市” 之间“存在航线”

  - 动态关系

    - 对象之间在行为（操作）上的联系

  - **类之间的静态关系，称为关联**

  - 关联的表示

  - <img src="https://i0.hdslb.com/bfs/album/b728cdecaac9a5131ebf5b553fbd96f8c751a9b1.png" alt="image-20220603200426545" style="zoom:67%;" /><img src="https://i0.hdslb.com/bfs/album/8916e28b0828ddd15fda8d3c860357fd1547ec34.png" alt="image-20220603200436635" style="zoom:67%;" />

    <img src="https://i0.hdslb.com/bfs/album/bc26dfadf022115c5c912d7b2b5f35a98e15f0d6.png" style="zoom:50%;" />

  - **关联类**

    ![image-20220603200655821](https://i0.hdslb.com/bfs/album/0f5bc5a3006dfab19117269f2613dd5d9c55797f.png)

- **聚合与组合**

  - 聚合：是表示整体的类和表示部分的类之间的“整体-部分”关系

  - 组合：是聚合的一种，且整体管理部分的生存期

    ![image-20220603200831657](https://i0.hdslb.com/bfs/album/a8be3030eabb5382a7334daeab5ebab983901078.png)

    <img src="https://i0.hdslb.com/bfs/album/7058f975f97f9652925a83625c5a88b4ddfa82f9.png" alt="image-20220603200900030" style="zoom:67%;" />

- **依赖**

  - UML中，依赖可用于多种建模元素之间
  - 对目标元素的改变，可能需要改变该关系的源元素

  ![image-20220603200947345](https://i0.hdslb.com/bfs/album/7a692dbb74929126771fc1586471c7ef8ce54e90.png)

**接口（实现关系）**

- 抽取类的公共操作，构成一个或多个接口， 称该类对这个或这些接口提供了实现

- 一个类可实现一个或多个接口，也称该类提供了一个或多个接口

  ![image-20220603201115590](https://i0.hdslb.com/bfs/album/3ad422576582613cfcea77dea4cc7f7231ef4a41.png)

  ![image-20220603201124409](https://i0.hdslb.com/bfs/album/1e8bfdfc0de6289eeb9f460029a68966df3667a4.png)

## 第五章 建立辅助模型——顺序图

**顺序图，又称序列图**，是一种详细表示**对象之间以及对象与 参与者之间行为关系**的图,由一组协作的**对象(或参与者)**以及它们之间可发送的**消息**组成,强调消息之间的**顺序**

![image-20220603204712695](https://i0.hdslb.com/bfs/album/adbbbbf779330b37c4d62521d8f6596c3428f5e6.png)



**顺序图的主要概念与表示法**

- **对象（生命线）**
  - **对象生命线:**表示对象在一段时间内存在,垂直虚线,置于对象下面
  - **对象**并不会处于一排, 规则是
    - 在图顶部放置在所有消息开始前就存在的对象
    - 所有通信完成后仍存在的对象，其生命线要延伸**超出最后**一个箭线
  - **生命线**可在某处分成两条或多条并行的生命线,也可在某处合并
  - **但生命线不能超过销毁处**

- **操作（控制焦点、激活、执行规约）**

  - 表示对象执行一个操作的周期,也表示了对象和它 的调用者之间的控制关系

  - 表示方式: 其顶端和操作的开始时刻对齐，末端 和操作的结束时刻对齐

  - **先在类中定义操作，然后在顺序图中为对象选择操作**

    <img src="https://i0.hdslb.com/bfs/album/95f84aa333fd7a573382439381d8b4acbe4d4d12.png" alt="image-20220603205539469" style="zoom:67%;" />

- **消息**

  - **消息是对象之间的通信的描述,这样的通信用于传输将发生的动作所需要的信息**

  - 用水平箭线表示消息,在其上表明**消息名字/参数/ 条件表达式,也可有序号**

  - **消息的分类**

    - **同步消息需要等待**对方对消息的回答后才能继续自已的操作

      <img src="https://i0.hdslb.com/bfs/album/82b801a4572707288e1ca3639506f37ee05b4db2.png" alt="image-20220603205801576" style="zoom:50%;" />

    - **异步消息不需要等待**对方对消息的回答便可以继续自已的操作

      <img src="https://i0.hdslb.com/bfs/album/8fade92e7638a58913f610951f596fbb4bcd44c0.png" alt="image-20220603205817751" style="zoom: 67%;" />

    - **返回消息**表示从同步消息创建的激活返回到调用者激活

- 对象的创建与销毁

  在过程性代码的情况下，一个激活表示在一个对象中一个过程是活动的，或者它的 从属过程（可能在其它的对象中）是活动的持续时间。**换句话说，可以在一个特定的时间看到所有活动着的嵌套过程激活**

  <img src="https://i0.hdslb.com/bfs/album/2a331a9c25734d33991218db5428b7f7d6e064a4.png" alt="image-20220603210021668" style="zoom:80%;" />

- **信号**

  - 对象之间的异步传送的消息的规格说明

  - 信号名(用逗号分隔的参数列表)从一个对象可以向另一个对象或对象 的集合发送信号。例如消息广播

  - 发送者在发送信号时，要实例化其参数。对于接收者来说，它收到的是一个事件

  - 在类图中，在类符号上用关键字<>声明信号。把参数说明为 性。信号没有操作

  - 在类的描述模板中，要指定所能接收的信号

  - 通常用信号对异常情况建模

    <img src="https://i0.hdslb.com/bfs/album/954b1c2e8e3013c555d784734bc7f2424a36c167.png" alt="image-20220603210246491" style="zoom:80%;" />

- **顺序图的结构化控制**

![image-20220603210333990](https://i0.hdslb.com/bfs/album/8f4c096ce302b1fbf0cac107d3cffb8b2ff02b8d.png)

![image-20220603210343519](https://i0.hdslb.com/bfs/album/c372a9e31752175b3997fb412aa1b7337649a477.png)

**eg：**

![image-20220603210628631](https://i0.hdslb.com/bfs/album/ec74ae8716e62db5fc8e928bc7df18c2872fefc4.png)

![image-20220603210639266](https://i0.hdslb.com/bfs/album/df3862e455ed6971401edfd99e632a7208728098.png)

![image-20220603210648117](https://i0.hdslb.com/bfs/album/cc1091d89c15316e5ea22acb3b6b0cf7c6dac099.png)



**总结**

- 顺序图可以动态验证类模型的可行性
- 顺序验证的某一功能，属于某个用例描述的功能中的一部分，又被称为用例实现 “usecase realization”
- 顺序图从上到下，反映了个对象相互协作的时间顺 序



## 第五章 建立辅助模型——通信图

- 对象间的协作与交流表现为

  一个对象以某种方式启动另一个对象的活动，这种交流被定义为消息

- 通信图是交互图的另一种表现形式

  它在语义上和顺序图是等价的

- 通信图强调的是参加一个交互的各对象的组织结构

- 通信图的构成

  - 对象
  - 链接
  - 在链接上传递的消息

  <img src="https://i0.hdslb.com/bfs/album/8005c28b0fe046ccf80ae3a6207d008bb636de1c.png" alt="image-20220603210950130" style="zoom:80%;" />

**顺序图与通信图的区别**

- 顺序图和通信图都来自UML的元模型中相同的信息，二者在语义上是等价的，可以相互转化、
- 通信图显示对象之间是如何被连接的结构关系
  - 对象之间的交流，通过在链接上附着带顺序号的消息
  - 顺序图没有
- 顺序图显示消息的返回、有对象生命线、控制焦点
  - 通信图没有

**总结**

![image-20220603211155094](https://i0.hdslb.com/bfs/album/3cd9aaf2e5d0d2f08ac4ab99cafbbe70879d61c7.png)





## 第五章 建立辅助模型——活动图

- 活动图描述了在一个过程中，顺序的/并行的**活动**及其之间 的关系
- 活动图是**点和弧**的集合



**活动图的基本元素**

1. **动作和活动**

   - 动作是一种**原子操作**，它不能被外部事件的转换所中断。 动作不可以分解成更小的部分，它是构造活动图的最小单位。**如调用另一个操作，发送一个信号，创建或撤销一个对象，或者某些纯计算（例如对一个表达式求值），都 是一个动作**

   - 活动可由动作和其他活动组成，最底层的活动是由动作执行的

   - <img src="https://i0.hdslb.com/bfs/album/e1d2db76826dae471bd29c8bbefef2247e699cfd.png" style="zoom: 67%;" />

2. **活动图的开始、结束**

   ![image-20220604101647625](https://i0.hdslb.com/bfs/album/4995bec84888e3e4bc27218f8f2da724d5c2043c.png)

3. **控制流**
   - 在图形上，用一个箭头表示从一个动作或活动到下一个动作或活动的转移
   - <img src="https://i0.hdslb.com/bfs/album/175d870fdbd4ca29fb4efe408225108514028b1a.png" alt="image-20220604101727265" style="zoom:80%;" />
4. **分支**
   - 一个分支可以有一个**进入流**和**多个离去流**
   -  在每个离去流上必须设置一个监护条件：条件放在方括号里
   - <img src="https://i0.hdslb.com/bfs/album/69cb10caccc6982b3ff803df568f77c240f97873.png" alt="image-20220604101847036" style="zoom:80%;" />
5. **分岔和汇合**
   - 岔表示把一个单独的控制流分成两个或多个并发的控制流
   - 汇合表示两个或多个并发控制流的同步发生，一个汇合可以有两个或多个进入转移和一个输出转移
   - <img src="https://i0.hdslb.com/bfs/album/3030cbb73603e0a74a5e9073511c26fd168c9d02.png" alt="image-20220604101955767" style="zoom:80%;" />
6. **对象流**
   - 对象流是动作或者活动与对象之间的依赖关系
   - ![image-20220604102022616](https://i0.hdslb.com/bfs/album/ee0145505f7ff4cb8830b6c6f16c54cb530b66b4.png)
7. **泳道**
   - 将一个活动图中的活动分组，每一组表示一个特定的类别、人或部门，他们负责完成组内的活动
   - 每个组被称为一个泳道
   - 转移和同步棒可以跨越泳道
   - <img src="https://i0.hdslb.com/bfs/album/2f3ffc1ed62390a547c7ab1dd85771efd4dd43e2.png" alt="image-20220604102222440" style="zoom:80%;" />

**活动图与流程图的区别**

- 活动图和传统的流程图也很相似，往往流程图所能表达的内容，大多数情况下活动图也可以表达
- 活动图是面向对象的 ，而流程图是面向过程的
- 活动图不仅能表达顺序流程控制，还能表达并发流程控制



**eg：**

![image-20220604102438327](https://i0.hdslb.com/bfs/album/6d1697831d1c7525e1540c55ff060c6c7a1d5049.png)

![image-20220604102446248](https://i0.hdslb.com/bfs/album/ae01a5216368794dd18f88dfc35202c5a983278a.png)



## 第五章 建立辅助模型——状态图

**状态图：单个对象的状态行为**

**状态机：是一种行为，说明对象在它的生命期中, 响应事件所经历的状态序列 以及它们对每个事件的响应**



**状态图(state diagram，State Chart)**

- 状态机可以用状态图来可视
- 状态图显示了一个状态机，它强调从状态到状态的控制流
- 一般仅对这样的对象建立状态图
  - 有清晰的生命期
  - 对其语境外部的事件能做出反应
  - 且它当前的行为受它**过去**行为的影响



**状态图的基本概念**

- **事件 Event**

  - **在状态机的语境中，一个事件是一个激励的发生，它能够触发一个状态迁移**

  - **信号事件 (异步）**
    - 一个对象收到另一个对象的信号
    - 可在一个类的符号中加一个附件的信号栏，列出其能接收的信号
    - 信号可以作为状态机中的状态转换上的动作被发送，或者作为交互中的一个消息被发送
    - ![image-20220604104213081](https://i0.hdslb.com/bfs/album/654fb85082a89bd9cea2a01a018631fe23c68892.png)
    - 可把信号指定为另一个信号的子类。这表示，子事件的出现触发依赖它的任何转换，或依赖它的任何祖先的转换
    - <img src="https://i0.hdslb.com/bfs/album/2b4873f68abc5b0b4fb0ee05f0e53634459ffe46.png" alt="image-20220604104342495" style="zoom:80%;" />

  - **调用事件（同步）：一个对象收到操作调用的请求消息**

  - **改变事件：由布尔表达式为真代表的事件**

  - **时间事件：是表示一段时间的推移**
    - 用关键字after 后面跟着时间表达式
    - 用关键字at 表示某个绝对时间点上发生的时间事件
  - <img src="https://i0.hdslb.com/bfs/album/23b872f047cc72233bc11a1d054d270b956ace0d.png" alt="image-20220604104610216" style="zoom:80%;" />

- **状态(state)**

  - 是对象的生命期中的一个条件或状况
  - <img src="https://i0.hdslb.com/bfs/album/1d36936bcd0b534b32f72589a3dac8520a610714.png" alt="image-20220604104643150" style="zoom:80%;" />
  - **动作**
    - 是在状态内或状态转换时所做的操作
    - 它是原子的和即时的（不可中断、瞬间的）

- **迁移Transition**

  - 当一个特定事件发生，且满足一定的条件， 对象从第一个状态（源状态）进入第2个状态（目标状态），并执行一定的动作
  - **自身迁移 self transition：从状态A迁移到状态A**
  - **内部迁移 internal transition：在状态A内部 行为**

<img src="https://i0.hdslb.com/bfs/album/c52ebae54774efdf65afc76b37f3fb9a1a752481.png" alt="image-20220604104912611" style="zoom:80%;" />

**状态图建模注意事项**

- 不允许孤立的状态存在
- 不允许只进不出的状态迁移 (“黑洞”)
- 不允许只出不进的状态迁移 (“奇迹”) 
- 不允许没有事件发生的迁移

**eg：**

![image-20220604105020305](https://i0.hdslb.com/bfs/album/3f19b385596a28e67d5d5d0716d291e1605a40c4.png)



**状态图与活动图的区别**

- **状态图**
  - 对**单个对象**的行为建模
  - 动态行为建模
- **活动图**
  - 强调从活动到活动的控制流，多个业务角色
  - 状态图是强调对象潜在的状态和这些状态之间的迁移





## 第五章 建立辅助模型——包图

-  **包图就是用来描述包及其关系的图，我们常用包图来描述 系统、子系统的宏观组成和结构**
- 一个包形成一个命名空间
- 在同一包中，同一类型的元素的名字必须唯一，不同类型的元素可以同名
- 不同包中模型元素可以有相同的名字
- 用“+”来表示“public”
- 用“#”来表示“protected”
- 用“-”来表示“private”

**包的关系**

1. **依赖关系**

   ![image-20220604105623623](https://i0.hdslb.com/bfs/album/b1a7d8a92b0a7556a55ccf2ebd13c8eb9e073b80.png)

​	![image-20220604105631220](https://i0.hdslb.com/bfs/album/02e6cc29cae4d529f5b4a06125050e6b42204baf.png)

2. **泛化关系：包间的泛化关系类似于类间的泛化关系，子包继承了父包的公共元素和保护元素，并可以增加新的元素**

![image-20220604105728610](https://i0.hdslb.com/bfs/album/2de2baa864a9987523510ceff91969d720b5d154.png)

**eg：**

<img src="https://i0.hdslb.com/bfs/album/2d0fa58fef2a908e2bcb2f7a66ae4a03d0de308c.png" alt="image-20220604105749304" style="zoom:80%;" />





## 第十一章 构建及部署部分设计——构件图/部署图

**物理建模：描述组件与结点之间的关系**

**构件（component）图**

- 构件是系统中符合一套接口标准并且提供其实现的物理的、可部署、可替换的部分
- 构件将一组实现（细节）封装起来，提供一组接口
- **构件的特点**
  - 独立的封装单位，并对外界提供接口
  - 可替换（条件：接口兼容）
  - 可复用（满足供接口和需接口要求）
  - 可组装（形成粒度更大的构件）
  - 可实例化
- ![image-20220604110137362](https://i0.hdslb.com/bfs/album/7fb70f5cf544aa91740c830425c59b6746c44c53.png)



## 第六章 什么是面向对象设计

**OOD（Object Oriented Design）**

- 在OOA模型的基础上，考虑与实现系统有关的因素（计算机设备、操作系统、网络、数据库、编程语言），进一步运用OO方法对系统进行设计，产生一个**可实现**的设计模型即OOD模型

**OOA与OOD的关系**

- OOD与OOA的追求目标不同，但它们采用一致的 **概念、原则和表示法**
- 不需要从分析文档到设计文档的转换
- 但是，二者还是有不同的侧重点和分工

**OOD模型框架**

![image-20220604111101547](https://i0.hdslb.com/bfs/album/08012e871507abdb75e3b7240d5a9a7ac9bba586.png)

**OOD过程**

![image-20220604111119924](https://i0.hdslb.com/bfs/album/121b96340a7f977888503a99ba6ac9008f1d3ad3.png)



## 第七章 问题域部分设计

问题域部分是OOD模型的四个组成部分之一，由来自问题域的对象构成， 是在OOA模型基础上，按照具体的实现条件进行必要的修改、调整和细节补充而得到的

![image-20220617153208405](https://i0.hdslb.com/bfs/album/2a82658d1b8625c9347888b0091ca0364a685b07.png)

**实现服用的设计策略**

![image-20220617153258805](https://i0.hdslb.com/bfs/album/96c2a8022035653f0de37f61d2e28031c09ede0f.png)

在OOA模型基础上，按**实现条件**进行补充和调整

- 为复用类而增加结构
- 提高性能
- 增加一般类以建立共同协议
- 按编程语言调整继承
- 对复杂关联的转化并决定关联的实现方式
- 调整和完善属性
- 构造及优化算法
- 决定对象间的可访问性



## 第八章 人机交互部分的设计

**人机交互部分时OOD模型的组成部分之一，突出人如何命令系统，系统如何向用户提交信息**

**人机交互部分的分析**

- 人机交互部分的设计不仅包括设计和实现，还包括分析
- 解决的核心问题：人如何命令系统，系统如何向人提交信息
- 以用况图为基础，继续分析

**人机界面的设计准则**

- 易学、易用、操作方便
- 尽量保持一致性
- 及时提供有意义的反馈
- 使用户的注意力集中在当前任务上，而不是 在界面上
- 尽量减少用户的记忆工作
- 具有语境敏感的帮助功能
- 减少重复的输入和操作
- 对用户的操作具有容错性
- 放置灾难性的错误



## 第九章 控制驱动部分的设计

**控制驱动部分的设计**

- 控制驱动部分是OOD模型的一个组成部分
- 由系统中**全部的主动类**构成
- 每个主动类所创建的一个主动对象是系统中 一个控制流的驱动者
- 控制流是一个在处理机上顺序执行的动作序 列
- 在目前的实现技术中，控制流就是进程或线 程
- 在顺序系统中，只有一个控制流。一个时刻 只有一个执行点

**控制流**

- 控制流是进程或线程的通称

- 在面向对象方法中，每个独立的控制流被建模为主动对象

- 该主动对象驱动进程或线程，它是控制流的根

- 当创建一个主动对象后，其中第1个被执行的操作的执行就开始一个控制流

- 当撤销这个主动对象时，就终止了相关的控 制流，它所代表的进程或线程就终止了

- **进程**

  - 具有一定独立功能的程序的一次执行过程
  - 是处理机和其他资源的分配单位
  - 单处理机上，各进程轮流占用处理机

- **线程**

  - 进程内定义的一些能分别占用处理机的执 行单位
  - 所有线程竞争整个进程内部提供的所有资源

- **进程与线程的关系**

  ![image-20220607205414178](https://i0.hdslb.com/bfs/album/af20c14f7775b6c9028bc39d241856434f818985.png)



**控制流的表示**

- 用主动对象表示一个控制流
- 用主动类表示一类控制流
- 在对象名前加<<process\>>或<<thread\>>表 示用进程还是线程实现控制流
- 一个主动类中，仅有一个主动操作

**进程间的通信**

- 同步
- 异步

**控制流间的同步**

1. Sequential（顺序的） 

   - 把整个对象作为临界资源，两个调用者在对 象外协调好，先后访问该对象

   - 对象访问的顺序化

2. Guarded（受监护的）
   - 操作标识为guarded，作为临界资源
   - 操作访问的顺序化
   - Java语言的synchronized相当于guarded

3.  Concurrent（并发的）
   - 多个控制流出现于某操作，把操作当做 **原子** 处理



## 第十章 数据管理部分的设计

**数据管理部分的设计**

- 数据管理部分是OOD模型的一部分

- 负责利用**文件、关系数据库（DB）或面向对象数据库管理系统（OODBMS）**来存储和检索永久对象

  - 还有封装对永久对象的查找和存储机制， 隔离数据管理方案对其他部分的影响
  - 只需存储永久对象的属性部分

- **持久对象**

  **需要长期存储的对象**



## 第x章 面向对象的基本设计原则

![image-20220604114057449](https://i0.hdslb.com/bfs/album/266071411ca3f902de1c7820d21914c5d2f81aa6.png)

**单一职责原则（The Single Responsibility Principle， SRP）**

- **就一个类而言，应该仅有一个引起它变化的原因**
- **一个类只负责一个功能领域中的相应职责**
- **SRP体现了内聚性（Cohesion）：一个模块的组成元素之间的功能相关性**

**开闭原则（OCP）**

- **软件系统应当允许功能扩展(即开放性）** 
- **但是不允许修改原有的代码（即关闭性）**

- **OCP的关键在于抽象**
  - 抽象预见了可能的所有扩展（闭）
  - 由抽象可以随时导出新的类（开）
- **开闭原则具有理想主义的色彩，它是面向对象设计的终极目标。其他设计原则都可以看作是开闭原则的实现手段或方法**

**里氏代换原则**

- 只要父类能出现的地方子类就可以出现，而且调用子类还不产生任何的错误或异常
- 里氏替换法则包含了四层意思：
  1. 子类必须完全实现父类的方法 
  2. 子类可以有自己的个性 
  3. 覆盖和实现父类的方法时，输入参数可以被放大，但不 能被缩小
  4. 覆盖和实现父类的方法时，输出结果可以被缩小，但不 能被放大
- **LSP是OCP成为可能的主要原则之一正是子类型的可替换性才使得使用基类类型的模块在无需修改的情况下就可以扩展**

**依赖倒置原则（DIP）**

- 继承层次关系中，基类不应当知道任何子类
- **依赖倒置原则启发了面向接口设计**







## 第十二章 若干经典设计模式

**设计模式的特点**

- 描述了一个反复出现的问题
- 描述了核心的解决方案
- 其他人可以无数次地使用这个方案解决类似的问题
- 解决方案针对反复出现的问题
- **不是一个“具体”的解决方案，而是一个抽象的方案**

**设计模式的定义（四个本质）**

- 模式的名字
- 模式解决的问题 
- 模式提出的解决方案 
- 应用模式的后果、折衷考虑的问题

**模式的作用**

- 解决某些特殊的设计问题
- 减少重复设计的工作量
- 把专家的知识、经验传递给新手
- 为设计提供共同的词汇
- 编写开发文档更加容易
- 应用设计模式可以让系统重构变得容易

**经典设计模式**

![image-20220604113843920](https://i0.hdslb.com/bfs/album/ae3a557c818d2e99a25fd305d8941567caeefb0e.png)



## 第十二章 设计模式——外观模式 Facade

![image-20220604132547808](https://i0.hdslb.com/bfs/album/63fe255f4ca299f20be816f8cef79236ef0c0382.png)

**为子系统中的一组接口提供一个一致的界面， Facade模式定义 了一个高层接口，这个接口使得这一子系统更加容易使用。引入 外观角色之后，用户只需要直接与外观角色交互，用户与子系统 之间的复杂关系由外观角色来实现，从而降低了系统的耦合度**

**eg：**

![image-20220604132823704](https://i0.hdslb.com/bfs/album/c0d93a39002a0aa610f90d67adbbb41d444938b9.png)

![image-20220604132832668](https://i0.hdslb.com/bfs/album/cadff3e477252df25a6f6e9bf95241c991cc53b6.png)

![image-20220604133219529](https://i0.hdslb.com/bfs/album/b78ad69e4a5fc901b88255c2b54f1f05ba304aba.png)

**外观模式的优点**

- 简化复杂系统的使用
- 对客户屏蔽子系统组件，减少了客户处理的对象数目并使得子系统使用起来更加容易
- 实现了子系统与客户之间的松耦合关系
- 降低了大型软件系统中的编译依赖性，并简化了系统在不同平台之间的移植过程
- 只是提供了一个访问子系统的统一入口，并不影响用户直接使用子系统类

**外观模式的缺点**

- 不能很好地限制客户使用子系统类
- **违背了开闭原则**



## 第十二章 设计模式——适配器模式

![image-20220604133405445](https://i0.hdslb.com/bfs/album/03ddc7103ae73f47f8431ac526e3025ddc02d4ff.png)

**对象适配器**

- **Target（目标抽象类）**：目标抽象类定义客户所需接口，可以是一个 抽象类或接口，也可以是具体类

-  **Adapter（适配器类）：**适配器可 以调用另一个接口，作为一个转换器，对Adaptee和Target进行适配，适配器类是适配器模式的核心， 在对象适配器中，它通过继承 Target并关联一个Adaptee对象使 二者产生联系

- **Adaptee（适配者类）：**适配者即 被适配的角色，它定义了一个已经 存在的接口，这个接口需要适配， 适配者类一般是一个具体类，包含 了客户希望使用的业务方法，在某 些情况下可能没有适配者类的源代 码。

- eg：

  在接口ScoreOperation中声明了排序方法sort(int[]) 和查找方法 search(int[], int)，为了提高排序和查找的效率，开发人员决定重用算法库中的快速排序算法类QuickSort和二分查找算法类BinarySearch，其中 QuickSort的quickSort(int[])方法实现了快速排序，BinarySearch 的 binarySearch (int[], int)方法实现了二分查找

![image-20220604133748220](https://i0.hdslb.com/bfs/album/fc69468e6a860c51b5826d1de62bab7279be79c5.png)

**类适配器**

- **类适配器模式**和**对象适配器模式**最大的区别在于**适配器和适配者之间的关系不同**，对象适配器模式中适配器和适配者之间是关联关系，而**类适配器模式中适配器和适配者是继承关系**



**适配器模式的优点**

- **将目标类和适配者类解耦**，通过引入一个适配器类来重用现有的适配者类，无须修改原有结构
- **增加了类的透明性和复用性**
- **灵活性和扩展性都非常好**

**适配器模式的缺点**

- 对于只能单继承的语言（Java、C#等），**不能同时适配多个适配者**
- **适配者类不能为最终类（Java中的final类）**



**外观模式与适配器模式的比较**

- 外观定义了新的接口，适配器使用旧的接口
- 适配器使得两个不一致的接口协同工作，而不是定义一个新的
- 外观模式的本意是产生一个轻便的接口，适配器的本意是把现有的接口转换一下
- 一个外观接口可能包装了多个现有系统的对象、也可能增 加了一些新功能，而适配器只是包装一个对象

<img src="https://i0.hdslb.com/bfs/album/d59ff2dec33ed8bcf7eb6fbce14be961fb9e0ad7.png" alt="image-20220604134308736" style="zoom:80%;" />



## 第十二章 设计模式——观察者模式 Observer

**当有许多不同的客户都对同一数据源感兴趣，对相同的数据有不同的处理方式，该如何解决？**

**观察者模式 Observer**

- **定义对象之间的一对多依赖关系，当一个对象改变状态时，所有依赖于它的对象都会自动获得通知**
- **又称之为：做发布-订阅（Publish/Subscribe）模式**
- **又称之为：模型-视图（Model/View）模式**
- **又称之为：源-监听器（Source/Listener）模式**

**观察者模式架构**

![image-20220604152229591](https://i0.hdslb.com/bfs/album/7911558c9857b5f2d11be8731430383ba3f7c10c.png)

**观察者模式的角色**

- Subject：抽象主题（抽象被观察者），抽象主题角色把所有观察者对象保存在一个集合里，每个主题都可以有任意数量的观察者，抽象主题提供一个接口，可以增加和删除观察者对象

  ```java
  public interface Subject {
      /**
       * 增加订阅者
       * @param observer
       */
      public void attach(Observer observer);
      /**
       * 删除订阅者
       * @param observer
       */
      public void detach(Observer observer);
      /**
       * 通知订阅者更新消息
       */
      public void notify(String message);
  }
  ```

- ConcreteSubject：具体主题（具体被观察者），该角色将有关状态存入具体观察者对象，在具体主题的内部状态发生改变时，给所有注册过的观察者发送通知

  ```java
  public class SubscriptionSubject implements Subject {
      //储存订阅公众号的微信用户
      private List<Observer> weixinUserlist = new ArrayList<Observer>();
      @Override
      public void attach(Observer observer) {
          weixinUserlist.add(observer);
      }
      @Override
      public void detach(Observer observer) {
          weixinUserlist.remove(observer);
      }
      @Override
      public void notify(String message) {
          for (Observer observer : weixinUserlist) {
              observer.update(message);
          }
      }
  }
  ```

- Observer：抽象观察者，是观察者者的抽象类，它定义了一个更新接口，使得在得到主题更改通知时更新自己

  ```java
  public interface Observer {
      public void update(String message);
  }
  ```

- ConcrereObserver：具体观察者，实现抽象观察者定义的更新接口，以便在得到主题更改通知时更新自身的状态

  ```java
  public class WeixinUser implements Observer {
      // 微信用户名
      private String name;
      public WeixinUser(String name) {
          this.name = name;
      }
      @Override
      public void update(String message) {
          System.out.println(name + "-" + message);
      }
  }
  ```

**客户端调用**

```java
public class Client {
    public static void main(String[] args) {
        SubscriptionSubject mSubscriptionSubject=new SubscriptionSubject();
        //创建微信用户
        WeixinUser user1=new WeixinUser("杨影枫");
        WeixinUser user2=new WeixinUser("月眉儿");
        WeixinUser user3=new WeixinUser("紫轩");
        //订阅公众号
        mSubscriptionSubject.attach(user1);
        mSubscriptionSubject.attach(user2);
        mSubscriptionSubject.attach(user3);
        //公众号更新发出消息给订阅的微信用户
        mSubscriptionSubject.notify("刘望舒的专栏更新了");
    }
}
/*
杨影枫-刘望舒的专栏更新了
月眉儿-刘望舒的专栏更新了
紫轩-刘望舒的专栏更新了
*/
```



**推模式**

- 推模式是当通知消息来之时，把所有相关信息都通过参数 的形式 **推送给** 观察者
- 优点
  - 所有信息通过参数传递过来，直接、简单，观察者可以马上进行处理
  - 观察者与被观察者没有一点联系，两者几乎没有耦合
- 缺点
  - 所有信息都强迫推给观察者，不管有用与否
  - 如果想添加一个参数，那就需要修改所有观察者的接口函数

**拉模式**

-  当通知消息来之时，通知的函数不带任何相关的信息，而是要观察者主动去被主题对象那里去 **拉取** 信息
- 优点
  - 可以主动去取自己感兴趣的信息
  - 如要添加一个参数，无需修改观察
- 缺点
  - 观察者与被观察者有一定的联系



## 第十二章 设计模式——策略模式

**问题提出**

- 有一个鸭子接口，定义了许多方式，而有一部分鸭子不需要全部的方式，就需要在子类中覆盖不用的方法

  ![image-20220604163121460](https://i0.hdslb.com/bfs/album/eaa53688695f2aae3482b94725168cec95c1faf8.png)

- **新设计**
  - Duck自己**不再去fly( )、不再去quack( )** 
  - 增加了两个属性：行为对象
    - 当需要fly的时候，委托给**flyBehavior对象**去处理
    - 当需要quack的时候，委托给**quackBehavior对象**去处理
    - 当这些变量所引用的对象不同时，有不同的执行效果，以满足需求变 化

![image-20220604163322926](https://i0.hdslb.com/bfs/album/4bff350592abbb4297ccc6bbd5cc568f7823c605.png)

![image-20220604163351739](https://i0.hdslb.com/bfs/album/b113490a6ed4dbd05e07803d8f09b11a4b667c9c.png)

![image-20220604163440191](https://i0.hdslb.com/bfs/album/d4059d43539ee5d002fbde00daa061c2fd9332dd.png)



**策略模式**

- **定义了算法族，分别封装起来，让它们之间可以互相替换，此模式让算法的变化独立于使用算法的客户**

![image-20220604163632477](https://i0.hdslb.com/bfs/album/7c315a60a851fec3cf5342e8d07ed570490ac3c2.png)

**策略模式包含的角色**

- **Context（环境类）：**环境类是使用算法的角色，它在解决某个问题（即实 现某个方法）时可以采用多种策略。在环境类中维持一个对抽象策略类的引 用实例，用于定义所采用的策略

  ```java
  class Context {
    private Strategy strategy;
    //维持一个对抽象策略类的引用
    public void setStrategy(Strategy strategy) { 
    	this.strategy= strategy;
    }
    //调用策略类中的算法
    public void algorithm() { 
    	strategy.algorithm();
    }
  }
  ```

- **Strategy（抽象策略类）：**它为所支持的算法声明了抽象方法，是所有策略 类的父类，它可以是抽象类或具体类，也可以是接口。环境类通过抽象策略 类中声明的方法在运行时调用具体策略类中实现的算法

  ```java
  abstract Strategy { 
  public abstract void algorithm();
  //声明抽象算法
  }
  ```

- **ConcreteStrategy（具体策略类）：**它实现了在抽象策略类中声明的算法， 在运行时，具体策略类将覆盖在环境类中定义的抽象策略类对象，使用一种 具体的算法实现某个业务处理

  ```java
  class ConcreteStrategyA extends Strategy {
  //算法的具体实现
  public void algorithm() { //算法A
  	}
  }
  ```

**客户端代码片段**

```java
Context context = new Context(); 
Strategy strategy;
strategy = new ConcreteStrategyA();
//可在运行时指定类型
context.setStrategy(strategy); 
context.algorithm();
```

****

**策略模式的优点**

- 策略模式提供了对 **开闭原则** 的完美支持，**用户可以在不修改原有系统的基础上选择算法或行为，也可以灵活地增加新的算法或行为**
- **策略模式提供了管理相关的算法族的办法**
- 策略模式提供了**一种可以替换继承关系的办法**
- 使用策略模式可以**避免多重条件选择语句**
- **策略模式提供了一种算法的复用机制**

**策略模式的缺点**

- **客户端必须知道所有的策略类，并自行决定使用哪一个策略类**
- 策略模式**将造成系统产生很多具体策略类**，任何细小的变化都将导致系统要增加一个新的具体策略类
- **无法同时在客户端使用多个策略类**



## 第十二章 设计模式——工厂模式

**工厂模式定义了一个创建产品对象的工厂接口，将实际创建工作推迟到子 类中**

**简单工厂模式**

![image-20220604170207724](https://i0.hdslb.com/bfs/album/628ff067e93bb011c6c8b51a17feae199cf2cdad.png)

eg：

- **Phone类：手机标准规范类(AbstractProduct)**

  ```java
  public interface Phone {
      void make();
  }
  ```

- **MiPhone类：制造小米手机（Product1）**

```java
public class MiPhone implements Phone {
    public MiPhone() {
        this.make();
    }
    @Override
    public void make() {
        // TODO Auto-generated method stub
        System.out.println("make xiaomi phone!");
    }
}
12345678910
```

- **IPhone类：制造苹果手机（Product2）**

```java
public class IPhone implements Phone {
    public IPhone() {
        this.make();
    }
    @Override
    public void make() {
        // TODO Auto-generated method stub
        System.out.println("make iphone!");
    }
}
```

- **PhoneFactory类：手机代工厂（Factory）**

```java
public class PhoneFactory {
    public Phone makePhone(String phoneType) {
        if(phoneType.equalsIgnoreCase("MiPhone")){
            return new MiPhone();
        }
        else if(phoneType.equalsIgnoreCase("iPhone")) {
            return new IPhone();
        }
        return null;
    }
}
```

**演示：**

```java
public class Demo {
   public static void main(String[] arg) {
       PhoneFactory factory = new PhoneFactory();
       Phone miPhone = factory.makePhone("MiPhone");            // make xiaomi phone!
       IPhone iPhone = (IPhone)factory.makePhone("iPhone");    // make iphone!
   }
}
```



**工厂方法模式（Factory Method）**

- 和简单工厂模式中工厂负责生产所有产品相比，工厂方法模式将生成具体产品的任务分发给具体的产品工厂

- 也就是定义一个抽象工厂，其定义了产品的生产接口，但不负责具体的产品，将生产任务交给不同的派生类工厂。这样不用通过指定类型来创建对象了

- **抽象工厂的组成**

  - **Product（抽象产品）：**它是定义产品的接口，是工厂方法模式所创建对象的超类 型，也就是产品对象的公共父类
  - **ConcreteProduct（具体产品）：**它实现了抽象产品接口，某种类型的具体产 品由专门的具体工厂创建，具体工厂和具体产品之间一一对应
  - **Factory（抽象工厂）：**在抽象工厂类中，声明了工厂方法(Factory Method)，用于 返回一个产品。抽象工厂是工厂方法模式的核心，所有创建对象的工厂类都必须实 现该接口
  -  **ConcreteFactory（具体工厂）：**它是抽象工厂类的子类，实现了抽象工厂中定义 的工厂方法，并可由客户端调用，返回一个具体产品类的实例

  ![image-20220604171601943](https://i0.hdslb.com/bfs/album/7c3ac40d2d4799c91bb470da40bb1c5d72725a65.png)

**eg：**

- **AbstractFactory类：生产不同产品的工厂的抽象类**

```java
public interface AbstractFactory {
    Phone makePhone();
}
```

- **XiaoMiFactory类：生产小米手机的工厂（ConcreteFactory1）**

```java
public class XiaoMiFactory implements AbstractFactory{
    @Override
    public Phone makePhone() {
        return new MiPhone();
    }
}
```

- **AppleFactory类：生产苹果手机的工厂（ConcreteFactory2）**

```java
public class AppleFactory implements AbstractFactory {
    @Override
    public Phone makePhone() {
        return new IPhone();
    }
}
```

- **演示：**

```java
public class Demo {
    public static void main(String[] arg) {
        AbstractFactory miFactory = new XiaoMiFactory();
        AbstractFactory appleFactory = new AppleFactory();
        miFactory.makePhone();            // make xiaomi phone!
        appleFactory.makePhone();        // make iphone!
    }
}
```



**简单工厂模式与工厂模式之间的对比**

- 当系统中需要引入 新产品时，由于 **简单工厂方法** 通过所传入参数的不同来创建不同的产品，这必定要修改工厂类的源代码，将违背 **开闭原则**

- 在工厂方法模式中，**我们不再提供一个统一的工厂类来创建所有的产品对象，而是针对不同的产品提供不同的工厂，系统提供一个与产品等级结构对应的工厂等级结构**



**工厂模式的优点**

- 用户只需要关心所需产品对应的工厂，无须关心创建细节， 甚至无须知道具体产品类的类名
- 能够让工厂可以自主确定创建何种产品对象，而如何创建这个对象的细节则完全封装在具体工厂内部
- 完全符合 **开闭原则**

**工厂模式的缺点**

- 在添加新产品时，需要编写新的具体产品类，而且还要提供与之对应的具体工厂类，系统中类的个数将成对增加，在一定程度上增加了系统的复杂度
- 增加了系统的抽象性和理解难度，增加了系统的实现难度

**工厂模式使用场景**

- 客户端不知道它所需要的对象的类
- 抽象工厂类通过其子类来指定创建哪个对象



## 第十二章 设计模式——抽象工厂模式

**抽象工厂模式(Abstract Factory Pattern)：提供一个创建一系列相关或相互依赖对象的接口，而无须指定它们具体的类。抽象工厂模式又称为Kit模式，它是一种对象创建型模式**

![image-20220604175205247](https://i0.hdslb.com/bfs/album/cf884328e3f39f663692629c15b09be900b21ed1.png)

**抽象工厂模式总结**

- **在抽象工厂模式中，增加新的产品族很方便，但是增加新的产品等级结构很 麻烦，抽象工厂模式的这种性质称为“开闭原则”的倾斜性。**

- **优点**

  - 抽象工厂模式隔离了具体类的生成，使得客户并不需要知道什么被创建。由于这种隔离，更换一个具体工厂就变得相对容易
  - 增加新的产品族很方便，无须修改已有系统，符合 **开闭原则**

- **缺点**

  增加新的产品等级结构麻烦，需要对原有系统进行较大的修改，甚至 需要修改抽象层代码，这显然会带来较大的不便，违背了 **开闭原则**

- **适用于多个产品族的情况**
