# JavaEE

[TOC]

# 第一章 JavaEE简介

Java EE不是编程语言、也不是产品，而是系列的**技术规范**

![image-20220923161011002](https://i0.hdslb.com/bfs/album/faa3828789d09dbaa7f0fcf332309614c87d7b1d.png)

**表现层**：主要功能就是实现用户交互、界面表示以及页面流程控制等。表现层收集客户请求数据，调用处于第二层即业务层中的核心服务，并生成客户请求响应

**业务层**：主要实现核心业务逻辑服务。业务逻辑层接收来自于表现层的服务请求，向持久层请求数据存取服务，并将处理结果返回给处于表现层的请求者

**持久层**：主要负责数据库等应用数据的存取。持久层为业务逻辑层提供对业务数据的存取服务

# 第二章 Java Web基础

## 2.1 JavaWeb开发模型演化

1. **原始阶段**

   JavaWeb应用开发采用Servlet或JSP，所有数据请求、逻辑处理、数据库存取和用户响应均至于一个文件中，可读性差，难以维护

2. **模型阶段**
   - JSP/Servlet + JavaBean
   - JSP + Servlet + JavaBean

3. **框架阶段**
   - **框架(Framework)**是将整个或部分系统进行可重用设计，表现为一组抽象构件及构件实例间交互的方法
   - **框架是一种规范**，规定了所包括组件构成及其之间的交互规范
   - **框架又是一种基础服务的实现**，为应用开发人员提供相应API及配置进行基于框架的应用系统开发
   - **常见框架：**struts、spring mvc、spring boot、MyBatis、Hibernate等

## 2.2 静态网页和交互式网站

**静态网页**：内容一直不变

**交互式网页**：页面内容根据交互变化

- 优点
  - **具有良好的交互性，可以根据不同的要求动态产生页面内容**
  - **支持后台数据库，可以将数据永久的保存在数据库，有利于数据的查找；**
  - **使用动态页面，页面量减少，降低了网页的维护工作量，提高了工作效率。**

**Http协议特性**

<img src="https://picogo-1314393134.cos.ap-nanjing.myqcloud.com/markdown/image-20230130121043526.png" alt="image-20230130121043526" style="zoom:67%;" />

- **简单快速**：客户向服务器请求服务时，只需传送请求方法、路径及所需的参数
- **灵活：**HTTP允许传输任意类型的数据对象，传输类型由Content-Type加以标记
- **无状态：**HTTP是无状态协议

## 2.3 Java Web 应用体系结构

**Java Web应用体系结构：个Web应用程序是由完成特定任务的各种Web组件构成的并通过Internet将服务展示给外界。在Java Web中，Web应用程序是由多个Servlet、JSP页面、HTML文件以及图像文件等组成。所有这些组件相互协调为用户提供一组完整的服务**

**Java Web应用的基本组成：由一组Servlet、JavaBean类、JSP页面、HTML页面等其它相关的资源组成，它必须运行在实现了Servlet规范的容器中**

<img src="https://picogo-1314393134.cos.ap-nanjing.myqcloud.com/markdown/image-20230130121239638.png" alt="image-20230130121239638" style="zoom:67%;" />

**Java Web应用文档结构**

<img src="https://picogo-1314393134.cos.ap-nanjing.myqcloud.com/markdown/image-20230130121311530.png" alt="image-20230130121311530" style="zoom:80%;" />

## 2.4 Java Web运行与开发环境

Java Web应用程序，必须有相应的**Servlet/JSP容器**。所有的Servlet/JSP程序代码在容器中被执行，然后将执行的结果由Web服务器返回给客户端。常用的Servlet容器有Tomcat、Jboss、Glassfish、Weblogic、Websphere等

**集成开发环境：MyEclipse/Eclipse/Intellij IDEA**

**编码：UTF-8**

## 2.5 Maven

Maven是一个项目管理工具，可以对Java项目进行构建、依赖管理

Maven可以完成以下工作：**构建**、文档生成、报告、依赖、发布

**Maven配置——pom.xml**

<img src="https://picogo-1314393134.cos.ap-nanjing.myqcloud.com/markdown/image-20230130162547914.png" alt="image-20230130162547914" style="zoom: 67%;" />

<img src="https://picogo-1314393134.cos.ap-nanjing.myqcloud.com/markdown/image-20230130162608838.png" alt="image-20230130162608838" style="zoom: 67%;" />

<img src="https://picogo-1314393134.cos.ap-nanjing.myqcloud.com/markdown/image-20230130162618527.png" alt="image-20230130162618527" style="zoom: 67%;" />

<img src="https://picogo-1314393134.cos.ap-nanjing.myqcloud.com/markdown/image-20230130162629387.png" alt="image-20230130162629387" style="zoom:67%;" />

<img src="https://picogo-1314393134.cos.ap-nanjing.myqcloud.com/markdown/image-20230130162656014.png" alt="image-20230130162656014" style="zoom:67%;" />

# 第三章 JSP技术

## 3.1 JSP概述

**JSP：是将Java代码嵌入到HTML代码中形成JSP文件。在执行时，JSP首先要由Servlet容器将JSP文件转换为Servlet并编译，然后才能执行**

**JSP工作原理**

1. 客户端通过浏览器向服务器发出请求，在该请求中包含了请求的资源的路径，这样当服务器接收到该请求后就可以知道被请求的内容
2. 服务器根据接收到的客户端的请求来加载相应的JSP文件
3. Web服务器中的JSP引擎会将被加载的JSP文件转化为Servlet
4. JSP引擎将生成的Servlet代码编译成Class文件
5. 服务器执行这个Class文件
6. 最后服务器将执行结果发送给浏览器进行显示


<img src="https://picogo-1314393134.cos.ap-nanjing.myqcloud.com/markdown/image-20230130163005393.png" alt="image-20230130163005393" style="zoom:67%;" />

**JSP三种元素**

- **脚本元素**

  - **声明**：声明的变量是页面共享级变量，所有访问此界面的用户共享，线程不安全

    `<%! 声明语句1; 声明语句2; …%>`

  - **脚本段**

    `<% Java代码 %>`

  - **表达式**：**表达式是由变量、常量和运算符组成的式子**

    `<%=表达式%>`

- **指令元素**

  **JSP指令用于通知JSP引擎在转换JSP文件的时候有关该JSP文件的信息及如何处理，**它并不向客户端产生任何输出，格式：`<%@ 指令名 属性名1="属性值" 属性名2="属性值" … %>`

  - **page指令**

    **用于整个JSP页面，定义整个页面的相关属性**

    相关属性

    - **import**：定义该JSP文件要引入的类，默认为：空
    - **contentType**：定义字符编码和输出的MIME类型，默认值：**text/html;charset=ISO-88590-1**，由于一般文件编码使用的是 **UTF-8** 所以设置为：**text/html;charset=UTF-8**
    - **session**：设置当前JSP页面是否参与HTTP会话，默认值：true
    - **pageEncoding**：设定JSP页面采用的字符编码。若没有指定，则使用contentType指定的字符编码，若两者都没有指定，则使用默认：ISO-8859-1

  - **include指令**

    - include指令是将一个文件的内容**静态的包含**到当前JSP文件的指定位置
    - include指令的语法：`<%@ include file= "path " %>`
    - **file属性被解释为相对于当前JSP页面的URL**

  - **taglib指令**

    - **tablib指令用于在JSP页面中引入自定义标签库**
    - 语法格式：`<%@ taglib (uri="URI"|tagdir="tagDir") prefix="tagPrefix" %>`

- **动作元素**

  **JSP内置标签，用于控制页面行为。这些动作由JSP容器实现**

  - `<jsp:param>`

    - 为其它动作元素提供参数。它一般和\<jsp:include>、\<jsp:forward>一起使用。**通俗来说就是传递参数**
    - 语法格式：`<jsp:param name="keyName" value="keyValue" />`

  - `<jsp:include>`

    - **在当前JSP页面中动态的包含一个HTML文件或JSP文件**

    - 语法格式：

      ```jsp
      <jsp:include page="path" flush="true|false" />
      或
      <jsp:include page="path" flush="true|false" >
      	<jsp:param … />
          …
      </jsp:include>
      flush：是否强行输出
      ```

    - **include动作和include指令的区别**
      - include指令在JSP **页面转换期**，直接将被包含的内容插入到相应位置，再编译。**编译之前**
      - include动作再JSP **请求处理期**，在编译之后，只包含结果
      - **include动作可以向被包含的文件传递参数，include指令则不能**
      - include动作通常用于提取页面中相同的部分，如：页头、页尾    

  - `<jsp:forward>`

    - **请求转发**。forward告诉JSP容器停止当前JSP文件的执行，将请求转向另一个资源，可以是一个HMTL文件、JSP文件或Servlet。请求转向的资源必须与该JSP文件在同一个上下文环境中

    - 语法格式 

      ```jsp
      <jsp:forward page="path" />
      或
      <jsp:forward page="path">
      	  <jsp:param … />
      </jsp:forward>
      ```

      

## 3.2 JSP内置对象

**JSP内置对象也称为隐含对象。**在JSP页面中，这些对象不用声明便可以直接使用，它们的生命周期由JSP容器掌控

**SP内置对象共有9个：**out、**response、request、session、applicant、**exception、config、page和pageContext

**out**

- **表示一个输出流。其主要功能是向客户端输出信息**

  ```java
  void print(Object)
  void println([Object])
  void newline()
  void close()
  ```

**response对象**

- **response对象的主要功能是对客户端的请求进行响应，设置响应头、向客户端写入cookie信息、将处理结果返回给客户端等**

  ```java
  setCharacterEncoding(String) //设置响应的字符编码
  setContentType(String) //设置响应的MIME类型，默认值：text/html。
  addCookie(Cookie) //将指定的Cookie加入到响应中
  SendRedirect(String) //将页面重定向到指定的地址
  ```

**request对象**

- **request对象封装了客户端请求的所有信息，如：请求头、提交的参数、Cookie信息、客户端浏览器信息等**

  ```java
  setCharacterEncoding(String):用于设置request对象中客户端提交参数的编码。
  getParameter(String) 
  getParamterValues(String)：用来获取客户端提交的参数值，不同的是若参数为单值时使用getParameter，若为多值则使用getParamterValues
  void setAttribute(String,Object)：向request对象添加一个附加属。
  Object getAttribute(String)：获取request中的附加属性
  void removeAttribute(String)：移除一个附加属性
  Cookie[] getCookies()：获取客户端提交的cookie
  String getContextPath()：获得上下文路径
  ```

**session对象**

- 是Java Web用于支持 **HTTP的会话机制的解决方案**

- **会话机制：**客户第一次访问参与会话页面时，服务器会为每个客户端创建一个session对象。可在这个session对象中记录客户的相关信息，根据session对象记录的信息，服务器可以实现对客户的跟踪

- **session对象会被容器所管理，不同的客户容器会产生不同的session对象**，这些会话对象通过不同的session ID来进行区分

- 可以使用session唯一确定一个用户

  ```java
  void setAttribute(String,Object)：将指定对象绑定到session对象上。
  Object getAttribute(String)：通过键名获取绑定在session对象上的附加对象
  void removeAttribute(String)：移除指定的附加对象
  void invalidate()：注销session对象，并释放绑定在此session对象上的所有附加对象。
  long getId()：返回session对象的session ID
  ```

- **session对象失效**
  - 会话超时，即超过session对象的生存时间。指定是用户在规定时间内没有再次访问该网站，则认为超时。**默认超时时间为30分钟**
  - 显式调用invalidate()方法。
  - **客户关闭浏览器：通常关闭浏览器不会直接清楚session对象，而是为用户分配一个新的session对象**

- 使用session设计一个用户登录及内容保护

  <img src="https://picogo-1314393134.cos.ap-nanjing.myqcloud.com/markdown/image-20230130223512001.png" alt="image-20230130223512001" style="zoom:67%;" />

**application对象**

- 与session对象类似，但是**application对象对所有用户都是同一个对象**

  ```java
  String getRealPath(String)：返回指定虚拟路径的真实路径。
  String getInitParameter(String)：返回配置文件web.xml中，指定的上下文参数值。
  getAttribute():与session相同
  setAttribute()：与session相同
  removeAttribute()：与session相同
  可通过修改web.xml添加参数
  在<web-app>中加入：
  <context-param>
  	<param-name>xxx</parm-name>
  	<param-value>yyy</param-value>
  </context-param>
  ```

**pageContext对象**

- 与session、application相同，但只能在本JSP页面内生效

  ```java
  getAttribute():与session相同
  setAttribute()：与session相同
  removeAttribute()：与session相同
  ```

**对象范围——生命周期**

- **page范围**：从jsp页面开始执行到执行结束
- **request范围**：从接受到请求开始，到响应结束
- **session范围**：整个会话期
- **application范围**：应用启动到应用关闭

## 3.3 Cookie对象

**Cookie是用来在客户端浏览器中保存一些信息的方法。通过cookie可以使用户在多次访问同一网站不同页面之间共享信息**

```java
//创建Cookie对象
Cookie varName = new Cookie(key,value);
//将Cookie写到客户端（浏览器）
response.addCookie(varName);
//读取客户端提交的Cookie
Cookie[] cks = request.getCookies();
```

**Cookie对象的生命周期**

- 指Cookie生效的时间，Cookie有效时间后失效
- 若没有指定有效时间，浏览器关闭后就会失效
- 使用`setMaxAge()`设置有效时间内，单位秒

**Cookie有效范围**

- Cookie有效范围是指Cookie被设置后那些资源可以获取(客户端访问那些资源时进行传送)
- 其有效范围是其所在目录及其子目录
- 可通过`setPath(String)`来设置其范围，默认为Cookie所属资源所在目录

# 第四章 Servlet技术

## 4.1 Servlet工作机制及生命周期

**Servlet：Servlet是运行在web服务器端的小程序，是JSP出现前Java中用于构建Web应用的一项很重要的技术**

**Servlet的功能**

- 创建并返回一个包含基于客户请求性质的动态内容的完整的 HTML页面
- 与其它服务器资源进行通信
- 对特殊的处理采用MIME类型过滤数据

**Servlet工作原理**

<img src="https://picogo-1314393134.cos.ap-nanjing.myqcloud.com/markdown/image-20230131102606229.png" alt="image-20230131102606229" style="zoom:67%;" />

1. web服务器（Servlet容器）接收到客户端请求，容器创建 **请求和响应对象**，并判断请求的Servlet对象是否存在
   1. 如果存在，则直接调用此Servlet对象的Service方法（间接调用doPost或doGet等方法），并将 **请求和响应对象** 作为参数传递
   2. 如果不存在，容器负责加载Servlet类，创建Servlet对象并实例化，然后调用Servlet的init方法进行初始化，之后调用Service方法
2. 在Service方法中，通过请求对象获取客户端提交的数据并处理，然后通过响应对象将处理结果返回给客户端

**Servlet的生命周期**

​	**Servlet不是独立的应用程序，它不能由用户或程序员直接调用，它的产生与销毁完全由容器（Web服务器）管理**

- **初始化阶段**：调用init()方法。Servlet对象被创建时，由容器调用此方法对该对象进行初始化
- **响应客户请求阶段**：调用service()方法。当客户请求到达时，容器调用此方法完成对请求的处理和响应
- **终止阶段**：调用destroy()方法。当容器检测到一个Servlet对象应从服务中移除时，会调用此方法完成Servlet对象被销毁前的收尾工作

## 4.2 Servlet的创建与配置

### 4.2.1 Servlet的创建

**Servlet相关类及接口**

- javax.servlet.Servlet接口

  Servlet接口是Servlet的基本接口，所有定义的Servlet都要直接或间接实现这个接口。Servlet接口的基本目标是提供生命周期方法

- javax.servlet. GenericServlet类

  GenericServlet类是一个实现了javax.servlet.Servlet接口和javax.servlet.ServletConfig接口的抽象类，它对除service()方法外的所有接口方法做了缺省实现。这意味着通过简单的扩展GenericServlet类便可编写一个基本的Servlet

- **javax.servlet.http. HttpServlet类**
  - HttpServlet类是继承自GenericServlet并对HTTP协议进行了封装的子类
  - 针对HTTP1.1中定义的Get、Post、Delete、Put、Head、Trace和Options7种方法，分别提供了7个方法来（doXXX）处理相应的请求
  - 要编写一个HTTP Servlet至少要覆盖一个方法，通常只要覆盖doPost和doGet两个方法即可
    - protected void doPost(HttpServletRequest request, HttpServletResponse response)
    - protected void doGet(HttpServletRequest request, HttpServletResponse response) 

<img src="https://picogo-1314393134.cos.ap-nanjing.myqcloud.com/markdown/image-20230131110308756.png" alt="image-20230131110308756" style="zoom:67%;" />



**Servlet与客户端进行通信**

- **Servlet与客户端的交互主要通过doXXX方法或Service方法中传入的request对象和response对象**
- **request对象**
  - request对象保存了用户的请求信息，通过此对象可以获取用户提交的数据。该对象的使用和JSP的内置对象request的使用方法完全相同
  - **public HttpSession getSession()**：获得会话对象，若不存在则建立
  - **public HttpSession getSession(boolean create)**：create决定是否创建会话对象
  - **public Cookie[] getCookies()**：获取cookie对象

- **response对象**
  - **JSP和Servlet中都通过response对象来对客户端做出响应的**
  - **PrintWriter out = response.getWriter();**  在servlet中获取输出流
  - **response. setContentType("text/html;charset=UTF-8")**： 设置响应的内容类型和编码，需要在 getWriter() 方法之前调用
  - **response.setCharacterEncoding("UTF-8")**：设置响应编码，需要在 getWriter() 方法之前调用

**servlet上下文（Application）**

- 获得上下文 ServletService
- 直接在Servlet中调用 **this.getServletContext()**

**请求转发**

- Servlet中要想实现JSP技术中的include动作和forward动作就必须首先获得RequestDispatcher接口实例

  ```java
  //获得RequestDispatcher接口对象
  request.getRequestDispatcher(String path).forward(ServletRequest request, ServletResponse response)
  request.getRequestDispatcher(String path).include(ServletRequest request, ServletResponse response)
  ```

**页面重定向**

- 通过response对象的sendRedirect方法将请求重定向的另外一个资源

  ```java
  response.sendRedirect(String path)
  ```

**请求转发与页面重定向**

- 请求转发不会产生新的请求，只是将原请求转发给新的资源
- 请求转发发生在服务器端，而重定向发生在客户端，因此请求转发引起客户端URL的变化
- 请求转发只能转发到同一应用内的资源，而重定向可以转到任何资源
- **请求转发的req和resp是同一个，重定向不同**

<img src="https://picogo-1314393134.cos.ap-nanjing.myqcloud.com/markdown/image-20230131134356906.png" alt="image-20230131134356906" style="zoom:67%;" />

### 4.2.2 Servlet的配置

**基于注解文件的配置**

```xml
<servlet>
	<servlet-name>MyServlet</servlet-name>  <!--Servlet标识名-->
    <servlet-class>demo.MyServlet</servlet-class> <!--Servlet实现类-->
</servlet>
<servlet-mapping>
	<servlet-name>MyServlet</servlet-name>  <!--对servlet标记中标识名的引用-->
    <url-pattern>/myServlet</url-pattern>   <!--- Servlet的映射URL -->
</servlet-mapping>
```

**基于注解的Servlet配置**

- **注：基于注解的配置只能应用于Web3.0及以上（JavaEE6）**

```java
@WebServlet(“/映射路径”)
public class XXX extends HttpServlet{}
//或
@WebServlet(
	name=“名称” ,
	urlPatterns={"/映射路径1","/映射路径2"}
)
public class XXX extends HttpServlet{}
```

## 4.3 Filter的工作机制

过滤器(Filter)是Java在服务器端的一个**可插拔的Web组件**。根据部署配置过滤器可以截取客户端和请求目标资源之间的请求和响应，**并对请求/响应信息进行预处理或过滤**

在客户端请求目标资源时，容器会首先调用这些过滤器，过滤器对这些请求数据进行检查和处理，并依次经过过滤器链，在经过每个过滤器时，过滤器可以将请求交给下一个过滤器或目标资源，也可以将请求转向，到预定页面

<img src="https://picogo-1314393134.cos.ap-nanjing.myqcloud.com/markdown/image-20230131134808402.png" alt="image-20230131134808402" style="zoom:50%;" />

**过滤器链**

为了提高代码的重用性，一般一个过滤器只能完成一个单一的功能。过滤器链是在web.xml中按需要的顺序部署多个过滤器，目标资源的URI指向同一个资源，或包含指定资源即可。过滤器调用时便会按部署文件中的配置顺序调用过滤器

## 4.4 Filter创建及应用

**过滤器的创建**

实现过滤器必须实现javax.servlet.Filter接口，并重写Filter接口中定义了的三个方法

- void destroy()  **过滤器销毁**

- **void doFilter(ServletRequest request, ServletResponse response,FilterChain chain)** 

  doFilter()方法是完成过滤操作的地方。在请求/响应到达时，容器调用此方法对请求/响应内容进行检查处理。在此方法被调用时，除了会传入请求对象（request）和响应对象（response）外，还会传入一个FilterChain对象，该对象代表了请求要经过的过滤器链。当处理完所有的信息后必须调用**FilterChain对象的doFilter()方法**，将请求传递到过滤器链中的下一个过滤器，或调用forward()、sendRedirect()方法结束过滤器链，将请求转向预定页面

- void init(FilterConfig filterConfig) **过滤器初始化**

- 下面时一个登录判断的例子

```java
package com.servlet;

import javax.servlet.*;
import javax.servlet.annotation.WebFilter;
import javax.servlet.http.*;
import java.io.IOException;

//实现过滤器接口
@WebFilter("/admin.jsp")
public class check implements Filter {

    @Override
    public void doFilter(ServletRequest req, ServletResponse resp, FilterChain filterChain) throws IOException, ServletException {
        //获取request、response、session对象
        HttpServletRequest request = (HttpServletRequest) req;
        HttpServletResponse response = (HttpServletResponse) resp;
        HttpSession session = request.getSession();

        String error = null;
        //获取账号密码
        String account = (String) req.getParameter("account");
        String password = (String) req.getParameter("password");

        //判断错误
        if (!"123456".equals(account) && !"123456".equals(password)) {
            error = "账号和密码";
        } else if (!"123456".equals(account)) {
            error = "账号";
        } else if (!"123456".equals(password)) {
            error = "密码";
        }

        if (error != null) {
            //有错
            session.setAttribute("error_my", error);
            System.out.println("有错");
            response.sendRedirect("login.jsp");	//重定向
        } else {
            //无错放行
            Cookie cookie1 = new Cookie("account", account);
            Cookie cookie2 = new Cookie("password", password);
            response.addCookie(cookie1);
            response.addCookie(cookie2);

            session.setAttribute("rem", true);
            session.removeAttribute("error_my");
            filterChain.doFilter(req, resp);	//放行
            System.out.println("无错");
        }
    }


    @Override
    public void init(FilterConfig filterConfig) throws ServletException {}

    @Override
    public void destroy() {
        Filter.super.destroy();
    }
}
```

**过滤器部署**

- 基于配置文件 web.xml

  ```xml
  <filter>
  	<filter-name>filterDemo</filter-name>  <!-- 过滤器标识名 -->
  	<filter-class>chap06.FilterDemo</filter-class>  <!-- 过滤器的实现类 -->
   </filter>
   <filter-mapping>
  	<filter-name>filterDemo</filter-name>  <!-- 引用已定义的过滤器标识名 -->
  	<url-pattern>/*</url-pattern>  <!-- 目标资源的URI -->
   </filter-mapping>
  ```

- 基于注解

  ```java
  @WebFilter(“/过滤规则”)
  public class LoginFilter implements Filter { .... }
  //或
  @WebFilter(filterName = "过滤器名称", urlPatterns = {"/过滤规则1","/过滤规则2"})
  public class LoginFilter implements Filter { ... }
  ```

# 第五章 EL及JSTL

**表达式语言(Expression Lanaguage, EL)**，是JSP规范的一部分，在JSP页面中使用**EL表达式可以简化对变量和对象的访问**

**JSTL全称JavaServer Pages Standard Tag Library**，是Sun公司制订的一套标签库规范，是用来替代原来的scriptlet(代码总嵌入<%%>)进行JSP页面开发，使得页面代码的可读性和可维护性显著提高

**EL和JSTL的出现均是为了简化JSP页面开发而提出的技术规范**，从而将Java代码彻底从JSP页面中移除，以提高页面代码的可读性

## 5.1 EL表达式

**EL表达式的功能**

- 动态读取JavaBean中的数据
- 调用任意静态或公有方法
- 动态执行算术运算

- 格式`&{表达式}`，其中表达式可以是常量、变量、表达式，**通常用于访问JSP内置对象的属性(Attribute)和用户提交的参数值**等

**EL操作符**

- [ ]与 . 操作符
- EL提供“[]"和“."两个运算符来取数据。
- 算术运算符：+、-、*、/ 或 div、% 或 mod（求余）
- 关系运算符：==、!=、>、>=、<、<=
- 逻辑运算符：&&(或and)、||(或or)、!(或not)
- Empty运算符：**${empty a}**，检查指定对象是否为null或empty。
- 条件运算符：布尔量？表达式1:表达式2

**EL内置对象**

- 通过EL内置对象可以访问JSP页面中常用对象的属性

- EL中允许直接访问通过setAttribute被绑定到不同范围的属性变量。作用域内置对象有：**pageScope、requestScope、sessionScope、applicationScope**

- 语法格式为：`${[作用域内置对象.]属性名}`

- 对象与JSP内置对象作用相同

  - pageScope：${pageScope.name}等同与pageContext.getAttribute(“name”)
  - requestScope：${requestScope.name}等同与request.getAttribute(“name”)；
  - sessionScoep： ${sessionScope.name}等同与session.getAttribute(“name”)；
  - applicationScope：${applicationScope.name}等同与application.getAttribute(“name”)；

- **请求头内置对象**

  - **header**：访问请求头中值为单值的属性
  - **headerValues**：访问请求头中值为多值的属性
  - **cookie**：访问请求头中的cookie信息

- **参数访问内置对象**

  - **param**：访问请求参数值为单值的参数，格式：`${param.key}`

    <img src="https://img-blog.csdn.net/20180409103203688" alt="img"  />

- **pageContext对象**：通常用于获取当前目录：`${pageContext.request.contextPath}`

## 5.2 JSTL

JSTL标签库

- **核心标签库**
- 国际化标签库
- xml标签库
- sql标签库
- 函数标签库

**JSTL配置**

- 在JSP文件中要使用JSTL标签库，还必须通过**taglib指令声明和引入相应的标签库**
- 在JSP文件开始部分添加：`<%@ taglib prefix="c" uri="http://java.sun.com/jsp/jstl/core" %>`

**JSTL标签**

- **输出标签——\<c:out>**

  ```jsp
  计算一个表达式并将结果输出：
  <c:out value="表达式" [escapeXML="true|false"] default="默认值" />
  escapeXML：是否对特殊字符进行转换。
  default：当计算结果为null时，输出指定的字符串
  ```

- **\<c:set>标签**

  ```jsp
  <c:set var="var"  value="value"  [scope="varScope" ]/>
  var：指定变量名称。
  scope：指定变量的作用范围，可以是page、request、session或application，默认为page。
  value：待赋给变量的值，可以是一个常量、EL或JSP表达式。
  ```

- **\<c:if>标签**

  ```jsp
  <c:if test="condition">标签体</c:if>
  如果条件为真则执行标签体。
  test：是一个EL的条件表达式
  ```

- **\<c:choose>、\<c:when>和\<c:otherwise>** switch语句

  ```jsp
  <c:choose>
  	<c:when test="condition1">body1</c:when>
      <c:when test="condition2">body2</c:when>
      ...
  	[<c:otherwise>bodyn</c:otherwise>]
  </c:choose>
  注：<c:when>和<c:otherwise>只能作为<c:choose>的子标签出现
  ```

- **\<c:forEach>标签**

  ```jsp
  用于遍历各种类型的集合、数组和用逗号分隔的字符串。
  <c:forEach var="varName" items="collection" [varStatus="varStatusName"] [begin="int"] [end="int"] [step="int"]>
  		标签体
  </c:forEach>
  items：EL表达式；为将被遍历的对象，可以是一个集合、数组或用逗号分隔的字符串。
  var：保存每次遍历得到集合、数组的成员的变量名。
  varStatus：保存遍历状态对象的变量名，其属性有：
  	current：当前这次迭代的（集合中的）项
  	index：当前这次迭代从0开始的迭代索引
  	count：当前这次迭代从1开始的迭代计数
  	first：用来表明当前这轮迭代是否为第一次迭代，该属性为boolean类型
  	last：用来表明当前这轮迭代是否为最后一次迭代，该属性为boolean类型
  begin：遍历开始的索引值。若指定了items，var中保存集合中索引指向的成员，若没有指定，则保持此索引值
  end：遍历结束的索引值。
  step：索引增长的步长，默认为1
  eg:
  <c:forEach var="book" items="${list}">
  	<tr>
  		<td>${book.bookID}</td>
  		<td>${book.bookName}</td>
  		<td>${book.bookCounts}</td>
  		<td>${book.detail}</td>
  	</tr>
  </c:forEach>
  ```

# 第六章 MVC开发模式

- MVC编程模式，全名是Model View Controller，是模型(model)－视图(view)－控制器(controller)的缩写

- MVC代表一种软件架构模式，它把软件系统强行分为三个基本部分：**模型（model）、视图（View）和控制器（Controller）**

- MVC的目的是实现一种动态编程方式，使后续对程序的修改、扩充简化，并且是程序的某部分的重复利用成为可能

<img src="https://picogo-1314393134.cos.ap-nanjing.myqcloud.com/markdown/image-20230131172612281.png" alt="image-20230131172612281" style="zoom:80%;" />

<img src="https://imgconvert.csdnimg.cn/aHR0cHM6Ly9ibG9naW1hZ2UtMTI1NTYxODU5Mi5jb3MuYXAtY2hlbmdkdS5teXFjbG91ZC5jb20vaW1nMjAyMDAzMTgxODE2NDkucG5n?x-oss-process=image/format,png" alt="img" style="zoom:67%;" />

![image-20230131173146590](https://picogo-1314393134.cos.ap-nanjing.myqcloud.com/markdown/image-20230131173146590.png)

- **Model（模型）**

  **Model（模型）又称为数据模型，是应用程序中用于处理应用程序数据逻辑的部分**。模型表示企业数据和业务规则，它封装了与**应用程序的业务逻辑相关的数据（通过JavaBean访问）**以及对**数据的处理方法（通过JDBC访问数据库）**

  - **JavaBean**

    - JavaBeans是Java中一种特殊的类，可以将多个对象封装到一个对象（bean）中。

    - 特点是可序列化(toString)，提供无参构造器，提供getter方法和setter方法(public)访问对象的属性
    - 所有属性均为private
    - 命名必须满足驼峰规范

- **View（视图）**

  **View（视图）是用户看到并与之交互的界面**。对Web应用程序来说，视图就是由HTML元素组成的界面。作为视图来讲，它只是作为一种输出数据并允许用户操纵的方式。

- **Controller（控制器）**

  **Controller（控制器）接受用户的输入并调用模型和视图去完成用户的需求**。控制器本身不输出任何东西和做任何处理，它只是接收请求并决定调用哪个模型构件去处理请求，然后确定用哪个视图来显示模型处理返回的数据

# 第七章 ORM及MyBatis

## 7.1 数据持久化与ORM

**持久化（Persistence）概念**

- 为不让程序运行过程中的信息丢失，就须将保存这些信息于文件（数据量较小时） 或 数据库（数据量较大时）中
- 把程序运行过程中状态信息进行保存供以后使用的操作，称为持久化

<img src="https://picogo-1314393134.cos.ap-nanjing.myqcloud.com/markdown/image-20230131181752661.png" alt="image-20230131181752661" style="zoom:80%;" />

**JDBC**

- JDBC提供了应用程序与数据库之间交互的统一接口。不同数据库管理系统提供者会提供自己的JDBC驱动程序，应用程序可使用不同的JDBC驱动程序与不同的数据库系统进行交互
- JDBC缺陷
  - 大量的重复代码
  - 不必要的SQL语句
  - OO与RDB之间的矛盾

**ORM**

- ORM-Object/Relational Mapping，即 **对象-关系型数据映射组件**
- **ORM为一种规范**，规定完成面向对象编程语言到关系数据库的映射
- ORM完成将数据库中的记录转换为内存中的对象，以及把内存中的对象的状态更新到数据库中
- 既利用了面向对象程序语言的现实业务直观性，又利用了关系数据库管理复杂关系的优势
- **ORM运行示意**

<img src="https://picogo-1314393134.cos.ap-nanjing.myqcloud.com/markdown/image-20230131182004329.png" alt="image-20230131182004329" style="zoom:67%;" />

- **ORM映射**

  <img src="https://picogo-1314393134.cos.ap-nanjing.myqcloud.com/markdown/image-20230131182034001.png" alt="image-20230131182034001" style="zoom:67%;" />

- **ORM优缺点**
  - 提高效率
  - 可维护性
  - 可移植性
  - 效率问题
  - 增加学习成本
  - 复杂查询实现困难

## 7.2 MyBatis概述

- MyBatis 本是apache的一个开源项目
- 一个基于Java的持久层框架。支持定制化 SQL、存储过程以及高级映射
- MyBatis 避免了几乎所有的 JDBC 代码和手动设置参数以及获取结果集
- MyBatis 可以使用简单的 XML 或注解来配置和映射原生信息，将接口和 Java 的 POJOs(Plain Ordinary Java Object,普通的Java对象)映射成数据库中的记录

**MyBatis优缺点**

- **简单易学**：本身就很小且简单。没有任何第三方依赖。
- **灵活**：mybatis不会对应用程序或者数据库的现有设计强加任何影响。
- **解除sql与程序代码的耦合**：通过提供DAL层，将业务逻辑和数据访问逻辑分离，使系统的设计更清晰，更易维护，更易单元测试。
- **支持注解与配置文件**
- **支持动态SQL**

**MyBatis组成**

- **主配置文件**：主要提供数据源信息、映射器；另外提供：基本配置、类型别名等
- **映射接口**：定义数据库操作接口，并与映射配置文件关联或通过注解提供SQL操作
- **映射配置文件**：定义具体的SQL语句、查询参数及查询结果的类型



## 7.3 MyBatis配置

**主配置文件**

```xml
<configuration>
    <!--引入外部配置文件-->
    <properties resource="db.properties"/>

    <!--为实体类起别名-->
    <typeAliases>
        <package name="com.dlct.pojo"/>
    </typeAliases>
    
    <!--设置-->
    <settings>
        <setting name="mapUnderscoreToCamelCase" value="true"/>
        <setting name="logImpl" value="STDOUT_LOGGING"/>
    </settings>

    <!--配置环境-->
    <environments default="development">
        <environment id="development">
            <transactionManager type="JDBC"/>
            <dataSource type="POOLED">
                <property name="driver" value="${driver}"/>
                <property name="url" value="${url}"/>
                <property name="username" value="${username}"/>
                <property name="password" value="${password}"/>
            </dataSource>
        </environment>
    </environments>
    
    <mappers>
        <!--引入com.dlct.Mapper包下的所有xml文件-->
        <package name="com.dlct.Mapper"/>
        <mapper resource="Mapper/UserMapper.xml"/>
        <mapper class="mappers.UserMapper" />
    </mappers>
</configuration>
```

- **environments** ：定义数据库环境列表，default：指明运行时默认使用那个环境定义
- **environmen**：定义一个数据库环境，id：定义环境标识
- **transactionManager**：指定事务管理器；JDBC：指明使用jdbc管理事务。
- **dataSource**：定义数据源；使用property标签指明连接数据库所需参数。
  - type： 指明是否启用连接池：POOLED或UNPOOLED
  - property：参数
- **properties**：引用外部属性文件，在配置文件中，使用${key}应用指定值。
- **typeAliases**：定义类型别名；通过package指明实体所在包，在映射配置文件中只需书写类的短名即可。
- **mappers**：映射器；指明具体的映射文件或映射接口。
  - mapper： resource：映射文件
  - class：映射接口文件
- **settings**：常量设置
  - **mapUnderscoreToCamelCase**：属性名驼峰名格式转换；
  - **logImpl**：开启控制台SQL打印

## 7.4 MyBatis基本使用

**MyBatis常用对象**

- **SqlSessionFactoryBuilder**

  **SqlSessionFactoryBuilder**利用XML文件或者Java代码来获取资源并构建**SqlSessionFactory**

  ```java
  InputStream is = Resources.getResourceAsStream(配置文件);
  SqlSessionFactory ssf = new SqlSessionFactoryBuilder().build(is);
  ```

- **SqlSessionFactory**

  会话工厂读取主配置文件建立数据库连接，并用于创建会话对象

  主要方法：

  - **openSession：打开一个会话（session）**
  - **closeSession：关闭一个会话**   ==每次使用完必须关闭==

- **SqlSession**

  MyBatis的关键对象，完成数据库的持久化操作；SqlSession是线程不安全

  主要方法：

  - **selectList、selectOne、selectMap、insert、update、delete**
  - **T getMapper(Class\<T> type)**：获得一个mapper的接口代理对象，通过该对象可以执行mapper接口中定义的sql方法
  - **commit()：提交事务**       ==查询操作不必提交，更新操作必须进行提交==
  - **rollback()：回滚事务**

**MyBatis编程步骤**

- 创建数据表：使用SQL语句

- 按表创建实体类：JavaBean

- 编写MyBatis配置文件

- 编写映射配置文件、映射接口（二选一或同时创建）

- 创建SqlSessionFactory

- 创建SqlSession

- 使用SqlSession执行相应操作

  

**映射文件的使用**

```xml
<mapper namespace=”xxx”>
	<tag id=”xxx” resultType=”xxx”  parameterType=”xxx”>
		SQL语句
	</tag>
</mapper>
```

- **namespace**

   命名空间，一般为映射接口的完整类名

- **tag**

  具体执行SQL的类型。可以是：select、insert、update、delete分别执行数据库的查询、插入、更新、删除；其标签体为相应的SQL语句。

- **parameterType** 可以在mybatis-config.xml文件中对类起别名，否则必须填写全路径

  传入SQL的参数类型，可以是Java的简单数据类型、map或JavaBean

- **resultType**

  查询结果返回的数据类型，同parameterType

  

**在SQL语句中使用参数**

- sql语句中引用参数

  - #{param}：对参数值进行转换处理，然后替换
    - **若传入参数是一个JavaBean可以通过这个方式获取参数**
    - **若传入参数是一个Map可以通过这个#{key}获取value值**
  - ${param}：对参数值不进行任何处理，直接替换

- 参数传入

  - 单个参数

  - 多个参数

    1. 基于配置文件：参数必须整合为一个bean或Map
    2. 基于接口文件与注解：可以是bean、Map；若是多个单参数，参数需使用@Param进行注解

    ```java
    @Select(“select * from id = #{id} and uname = #{uname}”)
    List<User> find(@Param(“id”) int uid, @Param(“uname”) String name);
    ```


**Map的使用，动态查询**

```xml
<update id="publishT00_notice" parameterType="Map">
update test  
set createdate = #{createdate},
creator = #{creator}
where id in 
<foreach collection="ids" item="ids" separator="," open="(" close=")">
	#{ids}
</foreach>
</update>
```

```java
HashMap<String,Object> map = new HashMap<String, Object>();
map.put("creator", "creator");
map.put("createdate", "createdate");
String[] ids = {"1","2"};
map.put("ids", ids );
```



**MyBatis执行SQL的三种方式**

- **基于映射文件方式** 一般不使用

  1. 创建book.xml文件

  ```xml
  <?xml version="1.0" encoding="UTF-8"?>
  <!DOCTYPE mapper PUBLIC "-//mybatis.org//DTD Mapper 3.0//EN" "http://mybatis.org/dtd/mybatis-3-mapper.dtd">
  
  <mapper namespace="com.dlct.pojo.Book">
  	<select id="selectAllBook" resultType="com.dlct.pojo.Book">
          select * from javaee_practice.books
      </select>
  </mapper>
  ```

  2. 在mybatis-config.xml文件的待添加代码

  ```xml
  <mappers>
  	<mapper resource="./book.xml"/>
  </mappers>
  ```

  3. 测试使用

  ```java
  InputStream inputStream = Resources.getResourceAsStream("config-mybatis.xml");
  SqlSessionFactory sqlSessionFactory = new SqlSessionFactoryBuilder().build(inputStream);
  SqlSession sqlSession = sqlSessionFactory.openSession();
  //在selectOne方法中传入namespace + id的字符串拼接
  Object name = sqlSession.selectOne("com.dlct.pojo.Book.selectAllBook");
  System.out.println(name);
  sqlSession.commit();
  sqlSession.close();
  ```

- **基于接口及注解方式**

  1. 创建接口文件BookMapper.xml，并添加注解

     **注解的分类**

     - **@Select**：查询
     - **@Insert**：插入
     - **@Update**：更新
     - **@Delete**：删除

  ```java
  public interface BookMapper {
      @Select("select * from javaee_practice.books")
      List<Book> selectAllBook();     //查询全部书籍
  
      @Select("select * from javaee_practice.books where id=#{id}")
      Book selectBookById(int id);    //通过id查询书籍
  
      @Delete("delete from javaee_practice.books where id = #{id}")
      int deleteBookById(int id);     //通过id删除书籍
  
      @Insert("insert into" +
              "        javaee_practice.books(book_name, author, price, press, press_date)" +
              "        VALUES (#{book_name}, #{author}, #{price}, #{press}, #{press_date})")
      int insertBook(Book book);      //插入书籍
  
      @Update("update javaee_practice.books" +
              "        set book_name = #{book_name}," +
              "            author = #{author}," +
              "            price = #{price}," +
              "            press = #{press}," +
              "            press_date = #{press_date}" +
              "        where id = #{id}")
      int updateBook(Book book);      //更新书籍
  }
  ```

  2. 在mybatis-config.xml文件的待添加代码

  ```xml
  <mappers>
      <mapper class="com.dlct.Mapper.BookMapper"/>
  </mappers>
  ```

  3. 测试

  ```java
  InputStream inputStream = Resources.getResourceAsStream("config-mybatis.xml");
  SqlSessionFactory sqlSessionFactory = new SqlSessionFactoryBuilder().build(inputStream);
  SqlSession sqlSession = sqlSessionFactory.openSession();
  BookMapper mapper = sqlSession.getMapper(BookMapper.class);
  Book book = mapper.selectBookById(1);
  System.out.println(book);
  sqlSession.close();
  ```

- **映射文件与接口映射混合方式**

  1. 创建接口文件BookMapper.xml

  ```java
  public interface BookMapper {
      List<Book> selectAllBook();     //查询全部书籍
      Book selectBookById(int id);    //通过id查询书籍
      int deleteBookById(int id);     //通过id删除书籍
      int insertBook(Book book);      //插入书籍
      int updateBook(Book book);      //更新书籍
  }
  ```

  2. 创建映射文件BookMapper.xml文件

  ```java
  <?xml version="1.0" encoding="UTF-8" ?>
  <!DOCTYPE mapper
          PUBLIC "-//mybatis.org//DTD Mapper 3.0//EN"
          "http://mybatis.org/dtd/mybatis-3-mapper.dtd">
  <mapper namespace="com.dlct.Mapper.BookMapper">
  
      <select id="selectAllBook" resultType="com.dlct.pojo.Book">
          select * from javaee_practice.books
      </select>
  
      <select id="selectBookById" resultType="com.dlct.pojo.Book" parameterType="int">
          select * from javaee_practice.books where id=#{id}
      </select>
  
      <delete id="deleteBookById" parameterType="int">
          delete from javaee_practice.books where id = #{id}
      </delete>
  
      <insert id="insertBook" parameterType="com.dlct.pojo.Book">
          insert into
              javaee_practice.books(book_name, author, price, press, press_date)
          VALUES (#{book_name}, #{author}, #{price}, #{press}, #{press_date})
      </insert>
  
      <update id="updateBook" parameterType="com.dlct.pojo.Book">
          update javaee_practice.books
          set book_name = #{book_name},
              author = #{author},
              price = #{price},
              press = #{press},
              press_date = #{press_date}
          where id = #{id}
      </update>
  </mapper>
  ```

  3. 在mybatis-config.xml文件的待添加代码

  ```xml
  <mappers>
      <mapper class="com.dlct.Mapper.BookMapper"/>
  </mappers>
  ```

  4. 测试

  ```java
  InputStream inputStream = Resources.getResourceAsStream("config-mybatis.xml");
  SqlSessionFactory sqlSessionFactory = new SqlSessionFactoryBuilder().build(inputStream);
  SqlSession sqlSession = sqlSessionFactory.openSession();
  BookMapper mapper = sqlSession.getMapper(BookMapper.class);
  Book book = mapper.selectBookById(1);
  System.out.println(book);
  sqlSession.close();
  ```

**注**

- **一般使用基于后两种方式**
- 基于注解的方式实现简单，方便阅读，但不能处理较复杂的SQL语句
- 基于接口及配置文件的方法实现复杂，不易阅读，但可以处理比较复杂的SQL语句

## 7.5 动态SQL

动态 SQL 是 MyBatis 的强大特性之一。基于配置文件的映射，可以通过ONGL来动态构建SQL语句

**常用ONGL标签**

- **if**标签

  在test条件内不必使用#{}可以直接写参数

  ```xml
  <if test=”条件”> SQL片段 </if>
  eg:
  <select id="selectAllWebsite" resultMap="myResult">  
      select id,name,url from website 
      where 1=1    <!--必须加否则报错-->
     <if test="name != null">        
         AND name like #{name}   
     </if>    
     <if test="url!= null">        
         AND url like #{url}    
     </if>
  </select>
  ```

-  **where-if**标签

  会自动添加where语句和自动删除and

  ```xml
  <select id="selectBookByMap" parameterType="map" resultType="com.dlct.pojo.Book">
      select *
      from javaee_practice.books
      <where>
          <if test="book_name != null">
              and book_name LIKE concat('%', '${book_name}', '%')
          </if>
          <if test="author != null">
              and author like concat('%', '${author}', '%')
          </if>
          <if test="price != null">
              and price > #{price}
          </if>
          <if test="press != null">
              and press like concat('%', '${press}', '%')
          </if>
          <if test="press_date != null">
              and DATE_FORMAT(press_date,'%Y-%m-%d') > '${press_date}'
          </if>
      </where>
  </select>
  ```

- **foreach**标签

  遍历集合，并进行引用拼接

  ```xml
  <!--批量查询-->
  <select id="findAll" resultType="Student" parameterType="Integer">
      <include refid="selectvp"/> WHERE sid in
      <foreach item="ids" collection="array"  open="(" separator="," close=")">
          #{ids}
      </foreach>
  </select>
  <!--批量删除-->
  <delete id="del"  parameterType="Integer">
      delete  from  student  where  sid in
      <foreach item="ids" collection="array"  open="(" separator="," close=")">
          #{ids}
      </foreach>
  </delete>
  ```

  

# 第八章 Spring

## 8.1 Spring概述

**Spring是一个轻量级的控制反转(IoC)和面向切面(AOP)的容器（框架）**

**Spring的发展及特点**

- **Spring简化了开发**：String中的IoC容器，可以将对象的实例化及对象间的依赖关系移交给Spring进行处理，用户不必再把精力放在最底层代码的编写上，提高了编写代码的效率
- **Spring中AOP技术简洁、易用**：基于注解，Spring中AOP的实现更加简洁、易用，较好的实现了将多个独立逻辑整合到业务逻辑中以更好的完成业务操作
- **Spring中事务管理简单易用**：通过声明式的事务管理降低了代码的复杂性，提高了开发的效率
- **Spring可以较好的与其它框架进行整合**：Spring较好的与当前流行框架(如Struts、Hibernate等)进行整合，以简单的结构实现复杂的业务逻辑

**Spring的体系结构**

<img src="https://picogo-1314393134.cos.ap-nanjing.myqcloud.com/markdown/image-20230206173735875.png" alt="image-20230206173735875" style="zoom:80%;" />

## 8.2 SpringIoC容器与Beans

**SpringIoC容器**

- **控制反转 (Inverse of Control, IoC) 是Spring的核心**。通过配置文件的描述及注解完成对象的注入，而不需要在代码中创建对象，被注册到Spring容器中的Beans由容器负责创建并进行管理
- Spring就像一个调度中心，**负责管理所有的Bean类，管理各个类的创建、使用(包括类属性的初始化)及销毁**，即：**把对象的创建和对象的调用过程，从程序员的手里交给Spring管理**
- Spring使用 **工厂模式和单例模式（所有的对象都是同一个实例）**，并利用Java的 **反射机制创建对象**

**依赖注入（DI，Dependency Injection）**：是根据一个bean对另外一个或多个bean的依赖关系，来创建依赖bean的实例，并将这些实例赋予bean的属性

- **在系统运行中，动态的向某个对象提供它所需要的其他对象**

**SpringIoC与DI的关系**

- IoC 不是一种技术，只是一种思想，一个重要的面向对象编程的法则
- IoC的一个重点是在系统运行中，动态的向某个对象提供它所需要的其他对象。这一点是通过DI（Dependency Injection，依赖注入）来实现的
- **它们是同一个概念的不同角度描述**

**BeanFactory和ApplicationContext**

- Spring容器是Spring的核心，容器通过IoC控制管理系统中的组件。**Spring通过两种类型方法实现Spring容器：BeanFactory和ApplicationContext**

- BeanFactory提供了一种管理bean(对象)的配置方法，这种配置方法考虑到多种可能的存储方式

- **ApplicationContext建立在BeanFactory之上**，扩展了它的功能，如更容易同Spring AOP特性整合，消息资源处理(用于国际化)，事件传递等

  Spring中构建ApplicationContext的方法：

  | 方法                               | 说明                                 |
  | ---------------------------------- | ------------------------------------ |
  | **ClassPathXmlApplicationContext** | **从类路径下加载应用上下文配置文件** |
  | FileSystemXmlApplicationContext    | 从文件系统下读取的xml配置文件        |
  | XmlWebApplicationContext           | 用于执行从web应用下读取xml配置文件   |

## 8.3 SpringBean配置

### 8.3.1 基于配置文件的配置

通过 **bean** 标签把Java Bean注册到SpringIOC容器中

```xml
<beans ...>
	<bean id="user" class="cn.edu.User" scope="singleton">
	   <property name="name" value="Tome" />
	   <property name="age" value="12"/>
	   <property name="sex" value="man"/> 
	   <property name="classes" ref="cls"/> 
     </bean> 
</beans>
```

- **id**：指定Bean的标识，在整个应用必须唯一

- **scope：**Bean的作用域

  |     描述      | 含义                                                         |
  | :-----------: | :----------------------------------------------------------- |
  | **singleton** | Spring容器中只含有一个Bean实例，**Spring默认作用域**  （单例模式） |
  | **prototype** | 每次从容器中获取Bean实例是都是一个新的实例                   |
  |  **request**  | 当请求类型为http时会创建一个新实例，仅在基于Web的Spring上下文中有效 |
  |  **session**  | 针对每一次HTTP请求都会产生一个新的bean，同时该bean仅在当前HTTP session内有效  （**可用于替换servlet中的session**） |

- **class**：Bean的实现类

- **property**：为Bean的属性进行初始化

  - value：为常量
  - ref：对已注册bean的引用，其值为注册bean的id

### 8.3.2 基于注解的配置

**以下四种注解效果相同，仅仅是名字不同，用于区分组件类别**

| 注解名                                 | 说明                          |
| -------------------------------------- | ----------------------------- |
| @Controller或@Controller("Bean名称")   | 注解控制层组件,如Action       |
| @Service或@Service("Bean的名称")       | 注解业务层组件                |
| @Repository或@Repository("Bean的名称") | 注解数据访问组件，即DAO层组件 |
| @Component                             | 注解不好归类的组件            |

**@Scope("作用域")**：作用域注解

**基于注解的依赖注入**

- 在依赖的成员变量上添加如下注解，声明依赖关系
- **@Resource**：基于名称，若找不到名称则基于类型，**通常使用**

- **@Autowired**：基于类型

**使用注解时必须在配置文件中添加**

```xml
<!--设置使用注解开发-->
<context:annotation-config/>
<!--扫描软件包，进行自动装配-->
<context:component-scan base-package="com.dlct.model"/>
```



## 8.4 AOP——面向切片编程

- **AOP目的是将那些与业务无关，但可以为业务模块调用的逻辑封装**，便于减少代码的重复，增加系统的可操作性和可维护性
- Spring 通常通过AOP来处理一些具有**横切性质的系统服务**，如安全检查、日志、事务管理、权限验证等

**常用术语**

- **切面（Aspect）**：被抽取出来的具有横切性质的功能模块，它是一个OOP的类，**由通知（Advice）和切入点（PointCut）组成**
- **通知**：是切面功能的具体实现，是AOP执行的一个动作（方法）
- **连接点（JoinPoint）**：是目标对象中插入通知的地方（**一个业务方法**），及Advice应用的位置
- **切入点**：切面的一部分，对应一个 **表达式**，定义了Adivce应该插入到那些连接点上，即：Advice的应用范围
- **目标对象（Target Object）**：被通知的对象，也就是将被切入的对象

**AOP通知类型**

- **Around通知**：包围一个连接点的通知，即在一个业务方法被调用之前执行一些操作，在调用之后再执行一些操作
- **Before通知**： 在一个连接点之前执行的通知
- **After Returning通知**：在连接点正常完成执行后的通知
- **Throws通知**：在连接点抛出异常是执行的通知

**Spring AOP使用AspectJ的切入点语法定义**

- 语法格式：`[<修饰符>]<返回类型><包.类.方法(参数)>[<异常>]`

  - 修饰符、异常可选

  - 其中所有元素可以使用一下通配符进行描述：
    - `*`匹配任意字符，只匹配一个元素
    - `..`匹配任意字符，可以匹配多个元素 ，在表示类时，必须和 `*` 联合使用
    - `+`表示按照类型匹配指定类的所有类，必须跟在类名后面，如 `com.cad.Car+` ,表示继承该类的所有子类包括本身

- **切点函数**：execute：用于匹配方法的切点函数
- **示例：**
  - `execution(public * *(..))` ：匹配目标类的所有public方法，第一个*代表返回类型，第二个*代表方法名，..代表方法的参数*
  - `execution(* com.cad.demo.User.*(..))`：匹配 User 类里的所有方法
  - `execution(* com.cad.demo.User+.*(..)) `：匹配该类的子类包括该类的所有方法
  - `execution(* com.cad..*.*(..))`：匹配 com.cad 包下、子孙包下所有类的所有方法

**Spring AOP配置**

```xml
在Spring配置文件的beans中添加命名空间：
xmlns:aop="http://www.springframework.org/schema/aop"
并在xsi:schemaLocation中添加：
http://www.springframework.org/schema/aop
http://www.springframework.org/schema/aop/spring-aop.xsd
在<bean>标签体中添加：
<aop:aspectj-autoproxy />
```

### 8.4.1 基于配置文件的切面定义

```xml
<bean id=”target” class=”xxx” />        <!--目标被切对象-->
<bean id=”pointcut” class=”xxx” />    <!--切面对象-->
<aop:config>  <!--切面配置-->
	<aop:aspect ref=”pointcut”>
    <!--定义切点-->
    <aop:pointcut expression=”execution(* *.say(..))” id=”log” /> 
    <!--定义通知-->
    <aop:before method=”beforeSay”  pointcut-ref=”log” />  
   </aop:aspect>
</aop:config>
```

### 8.4.2 基于注解的切面定义

```java
@Aspect  	//定义为切面
@Component	//注册bean
public class ServiceAOP {
    @Pointcut(value = "execution(* com.service.*.*(..))")      //定义切点
    public void pointcut(){}
    @Around(value = "pointcut()")      //定义通知
    public Object doAround(ProceedingJoinPoint point) throws Throwable {
        System.out.println("before Around.....");
        Object obj = point.proceed();              // 执行目标业务方法
        System.out.println("after Around......");
        return obj;
    } 
}
```

**注：**

- before、after通知都会自动执行目标业务方法，但around通知必须显示调用**ProceedingJoinPoint的proceed()方法执行目标业务方法**

- **before和after通知必须由JoinPoint参数，可通过该参数获取方法信息**

```java
@Aspect     //声明为切面
@Component
public class cutPoint {
    @Pointcut(value = "execution(* com.dlct.model.*Service.*(..))")
    public void cutPoint(){}    //创建切点

    @After(value = "cutPoint()")
    public void log(JoinPoint point) throws SQLException, ClassNotFoundException {
        System.out.println(point.getSignature() + "方法被执行.....");    //获取正在执行的方法信息
        String log = point.getSignature() + "方法被执行.....";
        Date date = new Date();
        ApplicationContext context = new ClassPathXmlApplicationContext("spring-config.xml");
        UserLog bean = context.getBean(UserLog.class);  //使用spring获取对象
        bean.insertLog(log, date);  //插入对象
    }

}
```

# 第九章 Spring MVC

## 9.1 Spring MVC 概述

Spring MVC 是 Spring 提供的一个**基于 MVC 设计模式的轻量级 Web 开发框架**。在 Spring MVC 框架中，**Controller（控制器） 替换 Servlet 来担负控制器的职责**，用于接收请求，调用相应的 Model 进行处理，处理器完成业务处理后返回处理结果。Controller 调用相应的 View 并对处理结果进行视图渲染，最终客户端得到响应信息

**Spring MVC工作原理**

![image-20230206221146272](https://picogo-1314393134.cos.ap-nanjing.myqcloud.com/markdown/image-20230206221146272.png)

- **前端控制器DispatcherServlet**
  - DispatcherServlet 相当于一个转发器或中央处理器，控制整个流程的执行，对各个组件进行统一调度，以降低组件之间的耦合性，有利于组件之间的拓展
  - 由框架提供

- **处理器映射器HandlerMapping**
  - 作用是根据请求的 URL 路径，通过注解或者 XML 配置，寻找匹配的处理器（Handler）信息
  - 由框架提供

- **处理器适配器HandlerAdapter**
  - 作用是根据映射器找到的处理器（Handler）信息，按照特定规则执行相关的处理器（Handler）
  - 由框架提供

- **逻辑控制器Handler——一般来讲是controller**
  - **其作用是执行相关的请求处理逻辑，并返回相应的数据和视图信息，将其封装至 ModelAndView 对象中**
  - 需要用户完成
  - 简单理解：Handler 是用来干活的工具；HandlerMapping 用于根据需要干的活找到相应的工具；HandlerAdapter 是使用工具干活的人

- **视图解析器View Resolver**
  - 其作用是进行解析操作，通过 ModelAndView 对象中的 View 信息将逻辑视图名解析成真正的视图 View（如通过一个 JSP 路径返回一个真正的 JSP 页面）
  - 由框架提供

- **视图 View**
  - 返回给客户端的数据或页面。Spring MVC支持多种视图，默认为JSP
  - 需要用户完成

**具体流程**

1. 用户通过浏览器发起 HttpRequest 请求到前端控制器 (DispatcherServlet)。
2.  DispatcherServlet 将用户请求发送给处理器映射器 (HandlerMapping)。
3. 处理器映射器 (HandlerMapping) 会根据请求，找到负责处理该请求的处理器，并将其封装为处理器执行链 返回 (HandlerExecutionChain) 给 DispatcherServlet
4. DispatcherServlet 会根据 处理器执行链 中的处理器，找到能够执行该处理器的处理器适配器 (HandlerAdaptor)  -- 注，处理器适配器有多个
5. 处理器适配器 (HandlerAdaptoer) 会调用对应的具体的 Controller
6. Controller 将处理结果及要跳转的视图封装到一个对象 ModelAndView 中并将其返回给处理器适配器 (HandlerAdaptor)
7. HandlerAdaptor 直接将 ModelAndView 交给 DispatcherServlet ，至此，业务处理完毕
8. 业务处理完毕后，我们需要将处理结果展示给用户。于是 DisptcherServlet 调用 ViewResolver，将 ModelAndView 中的视图名称封装为视图对象
9. ViewResolver 将封装好的视图 (View) 对象返回给 DIspatcherServlet
10. DispatcherServlet 调用视图对象，让其自己 (View) 进行渲染（将模型数据填充至视图中），形成响应对象 (HttpResponse)
11. 前端控制器 (DispatcherServlet) 响应 (HttpResponse) 给浏览器，展示在页面上。

## 9.2 Spring MVC框架配置

1. **注册前端控制器**

   在 **web.xml** 文件中添加

   ```xml
   <servlet>
       <servlet-name>springMVC</servlet-name>
       <servlet-class> org.springframework.web.servlet.DispatcherServlet</servlet-class>
       <init-param>
           <param-name>contextConfigLocation</param-name>
           <!--配置文件-->
           <param-value>classpath:spring-config.xml</param-value>
       </init-param>
   </servlet>
   <servlet-mapping>
       <servlet-name>springMVC</servlet-name>
       <url-pattern>/</url-pattern>
   </servlet-mapping>
   ```

2. 在Spring配置文件的beans中添加命名空间和约束文件

   ```xml
   xmlns:mvc="http://www.springframework.org/schema/mvc"
   在xsi:schemaLocation添加：
   http://www.springframework.org/schema/mvc
   http://www.springframework.org/schema/mvc/spring-mvc.xsd
   ```

3. 注解驱动配置：添加注解驱动的目的是加载处理注解的映射器和适配器
4. 组件扫描：功能和spring一样，通过扫描自动注册通过注解注册的bean
5. 视图解析器配置：用于指定视图解析器的实现类及视图所在位置
6. 静态资源配置：默认Spring MVC的控制器会对所有的请求进行处理；但静态资源，如：CSS文件、js文件、图片等不需要服务器处理的资源，可通知控制器对这些请求直接放行

```xml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xmlns:mvc="http://www.springframework.org/schema/mvc"
       xmlns:context="http://www.springframework.org/schema/context"
       xsi:schemaLocation="http://www.springframework.org/schema/beans
       http://www.springframework.org/schema/beans/spring-beans.xsd
       http://www.springframework.org/schema/mvc
       http://www.springframework.org/schema/mvc/spring-mvc.xsd http://www.springframework.org/schema/context https://www.springframework.org/schema/context/spring-context.xsd">
    <!--1.注解驱动-->
    <mvc:annotation-driven/>

    <!--2.组件扫描-->
    <context:component-scan base-package="com.dlct.controller"/>

    <!--3.视图解析器-->
    <bean class="org.springframework.web.servlet.view.InternalResourceViewResolver">
        <property name="prefix" value="/WEB-INF/jsp/"/>
        <property name="suffix" value=".jsp"/>
    </bean>
    
    <!--4.静态资源过滤-->
    <!--本地路径的起点为工程的webapp目录-->
    <mvc:resources mapping="URL/**" location="本地路径" />
</beans>
```

## 9.3 Spring MVC 控制器

- **Spring MVC基于方法来处理客户端的请求，在同一个控制器中定义多个方法（Handler）来处理多中请求**
- 在Spring MVC中只需要通过 **@Controller** 进行注解，即可生成一个控制器
- 在控制器上，通过 **@RequestMapping** 来注解一个 **处理器（Handler）**

- **@Controller**

  注解类为一个控制器。在类名上进行注解，并放到Spring的扫描路径上。

- **@RequestMapping**

  注解控制器的方法为一个处理器（Handler），并指明一个请求路径（url）来处理客户端的一个请求。格式：

  1. **RequestMapping(“url”)**
  2. **RequestMapping({“url1”，“url2”...})**

```java
@Controller
public Demo{
	@RequestMapping(“/index”)
	public String index(){
		......
		return “index”;                 //返回一个逻辑视图
	}
}

@RequestMapping
另外，@RequestMapping也可以注解在类上；当注解在类上时，注解的“url”相当于一个目录，而该类中被注解的方法相当于文件。如：
@Controller
@RequestMapping(“/user”)
public UserController{
	@RequestMapping(“/add”)
	public String useradd(User user){....}
}
对useradd方法的访问路径为：
/user/add
```

**获取客户端参数**

- **单独参数获取**

  要求客户端参数名和方法名一致即可，控制器在获取参数前会对客户端参数按方法参数的类型进行转换,eg:

  ```java
  @RequestMapping("/deleteBook")
  public String deleteBook(int id){
      System.out.println("deleteBook=>"+id);
      bookService.deleteBook(id);
      //直接重定向到allBook界面，这样会像运行allBook的请求再进入界面
      return "redirect:/book/allBook";
  }
  <a href="${pageContext.request.contextPath}/book/deleteBook?id=${book.bookID}">
  ```

- **复合获取参数**

  要求方法参数为 **JavaBean**，客户端参数名与Bean属性名一致即可。若没有对应的客户端参数，BEan的属性值将为默认值

  ```java
  @RequestMapping("/updateBook")
  public String updateBook(Books books){
      System.out.println("updateBook=>"+books);
      bookService.updateBook(books);
      //直接重定向到allBook界面，这样会像运行allBook的请求再进入界面
      return "redirect:/book/allBook";
  }
  ```

  ```xml
  <form action="${pageContext.request.contextPath}/book/updateBook" method="post">
    <input type="text" name="bookID" value="${book.bookID}" readonly>
    <input type="text" name="bookName" value="${book.bookName}" required>
    <input type="text" name="bookCounts" value="${book.bookCounts}" required>
    <input type="text" name="detail" value="${book.detail}" required>
    <button type="submit" class="btn btn-default">确认修改</button>
  </form>
  ```

**向视图传值以及选择视图**

- **ModelAndVeiw**

  **ModelAndVeiw用于向视图传值并指明视图路径**。使用ModelAndVeiw向视图传值，要求处理方法的**返回值必须为ModelAndVeiw**

  ```java
  addObject(String attributeName，Object value);//向视图传值
  setViewName(String path);//指明视图路径
  //eg:
  @RequestMapping(value = "/say")
  public ModelAndView say() {
      ModelAndView mv = new ModelAndView();
      mv.addObject("message","Hello,SpringBoot");
      mv.setViewName("say");
      return mv;
  }
  ```

- **Model**

  Model只用于向视图传值。使用Model向视图传值，要求处理方法的返回值为String，即：视图路径。使用Model时，Model对象为处理方法的参数传入，即Model对象由Spring容器创建

  ```java
  addAttribute(String name,Object value);
  addAttributes(Map<String,?> map);// 向视图传值
  //eg:
  @RequestMapping("/allBook")
  public String list(Model model){
      List<Books> books = bookService.selectAllBook();
      model.addAttribute("list", books);
      return "allBook";
  }
  ```

**页面重定向**

- 场景：若处理方法在处理过程中出现错误，或不允许浏览相应视图，则需跳转到错误页面；处理方法：进行页面跳转
- 只需设置视图路径为： `redirect:新URL`

**向处理方法注入Servlet对象**

- Spring MVC对Servlet做了封装，在一般操作中不需要使用Servlet的对象，但在一下**特殊情况下需要直接操作Servlet对象（Request、Session）才能完成**。需要使用这些对象时，只要将需要的对象作为处理方法的参数传入即可
- 如：public String index(String uname, **HttpSession session**){}
- **其中session对象即servlet的会话对象**

## 9.4 Spring MVC 拦截器

- Spring MVC中存在大量的拦截器，主要完成对**用户请求进行预处理和拦截及后期处理**。如：**类型转换、请求参数注入**等

- 用户请求在到达处理Handler之前需经过一系列的拦截器

- **拦截器工作原理**：

  ![image-20230207194815992](https://picogo-1314393134.cos.ap-nanjing.myqcloud.com/markdown/image-20230207194815992.png)

**拦截器的实现**

- 实现一个拦截器只需实现 **HandlerInterceptor接口** 即可
- **接口方法**
  - **`boolean preHandle(HttpServletRequest req, HttpServletResponse res, Object handler)`**：在请求处理之前被调用；返**回true时继续后续连接器及处理方法的调用，若返回false则表示请求结束，后续的拦截器及处理方法则不再执行**。注意：**若在该方法中拦截了请求（返回false），则必须进行请求转发或重定向**
  - **`void postHandle(HttpServletRequest request, HttpServletResponse response, Object handler, ModelAndView modelAndView)`** 只有处理方法被执行后，该方法才会被执行；其功能用于视图处理
  - **`void afterCompletion(HttpServletRequest request, HttpServletResponse response, Object handler, Exception ex)`** 只有在相应的拦截器的prehandler返回true时才会被执行

**拦截器注册**

```xml
<mvc:interceptors>
    <mvc:interceptor>
        <mvc:mapping path="拦截路径"/>
        <bean class="实现类" />
    </mvc:interceptor>
</mvc:interceptors>
注：拦截路径一般需要使用通配符“*”；如：/* 表示对所有非静态资源进行拦截。
```

eg:

```java
public class LoginInterceptor implements HandlerInterceptor {
    @Override
    public boolean preHandle(HttpServletRequest request, HttpServletResponse response, Object handler) throws Exception {
        ApplicationContext applicationContext = new ClassPathXmlApplicationContext("applicationContext.xml");
        //使用Spring获取UserServiceImpl的对象
        UserServiceImpl userServiceImpl = (UserServiceImpl) applicationContext.getBean("userServiceImpl");
        //获取session
        HttpSession session = request.getSession();
        //已经登录直接放行
        if (session.getAttribute("login") != null){
            return true;
        }
        String name = request.getParameter("name");
        String pwd = request.getParameter("pwd");
        //未登录
        if(name == null){
            session.setAttribute("errorr","请先登录");
            System.out.println("无账号");
            response.sendRedirect( request.getContextPath() + "/");
            return false;
        }
        //进行登录判断
        String s = userServiceImpl.selectUserByName(name);
        if (s == null || !s.equals(pwd)){
            session.setAttribute("errorr","账号密码错误");
            System.out.println("账号密码错误");
            response.sendRedirect( request.getContextPath() + "/");
            return false;
        }else {
            session.setAttribute("login", true);
            System.out.println("账号密码正确");
            session.removeAttribute("error");
        }

        return true;
    }

    @Override
    public void postHandle(HttpServletRequest request, HttpServletResponse response, Object handler, ModelAndView modelAndView) throws Exception {
        System.out.println("-----------------登录拦截器即将运行-----------------");
    }

    @Override
    public void afterCompletion(HttpServletRequest request, HttpServletResponse response, Object handler, Exception ex) throws Exception {
        System.out.println("-----------------登录拦截器运行完毕-----------------");
    }
}
```

```xml
<!--登录拦截器-->
<mvc:interceptors>
    <mvc:interceptor>
        <mvc:mapping path="/book/*"/>
        <bean class="com.dlct.Interceptor.LoginInterceptor"/>
    </mvc:interceptor>
</mvc:interceptors>
```





# 第十章 SSM集成

- **SSM是指：Spring + Spring MVC + Mybatis**，是现下比较流行的一个框架组合
- **Spring**：管理整个系统所有对象的生命周期
- **Spring MVC**：处理系统的所有请求
- **Mybatis**：完成数据库的操作

<img src="https://picogo-1314393134.cos.ap-nanjing.myqcloud.com/markdown/image-20230207201202521.png" alt="image-20230207201202521" style="zoom:80%;" />

**Spring配置文件**

```xml
<!--Spring-->
<!--Spring包扫描注册-->
<context:component-scan base-package="com.controller,com.service" />
<!--加载属性文件-->
<context:property-placeholder location="classpath:db.properties" />
<!--数据库连接池-->
<bean id="datasource" class="org.apache.commons.dbcp.BasicDataSource" destroy-method="close">
    <property name="driverClassName" value="${driver}" />
    <property name="url" value="${url}" />
    <property name="username" value="${user}" />
    <property name="password" value="${passwd}" />
</bean>

<!--MyBatis-->
<!--MyBatis的会话工厂-->
<bean id="sqlSessionFactory" class="org.mybatis.spring.SqlSessionFactoryBean">
    <!--数据源（连接池）-->
    <property name="dataSource" ref="datasource" />
    <!--实体所在包-->
    <property name="typeAliasesPackage" value="com.entity" />
     <!--Mybatis的常量配置文件-->
    <property name="configLocation" value="classpath:mybatis-config.xml" />
     <!--Mapper配置文件-->
    <property name="mapperLocations" value="classpath:mapper/*.xml" />
</bean>
<!--Mybatis 会话管理-->
<bean class="org.mybatis.spring.mapper.MapperScannerConfigurer">
    <!--会话工厂-->
    <property name="sqlSessionFactoryBeanName" value="sqlSessionFactory" />
    <!--映射接口文件所在包-->
    <property name="basePackage" value="com.mapper" />
</bean>

<!--Spring MVC-->
<!--Spring MVC注解驱动-->   
<mvc:annotation-driven />
<!--Spring MVC视图解析器-->
<bean class="org.springframework.web.servlet.view.InternalResourceViewResolver">
    <property name="suffix" value=".jsp" />
    <property name="prefix" value="/views/" />
</bean>
<!--Spring MVC静态资源-->
<mvc:resources mapping="/lib/**" location="/lib/" />
<mvc:resources mapping="/images/**" location="/images/" />
```

**MyBatis配置文件**

```xml
<configuration>
    <!--引入外部配置文件-->
    <properties resource="db.properties"/>

    <!--为实体类起别名-->
    <typeAliases>
        <package name="com.dlct.pojo"/>
    </typeAliases>

    <!--配置环境-->
    <environments default="development">
        <environment id="development">
            <transactionManager type="JDBC"/>
            <dataSource type="POOLED">
                <property name="driver" value="${jdbc.driver}"/>
                <property name="url" value="${jdbc.url}"/>
                <property name="username" value="${jdbc.username}"/>
                <property name="password" value="${jdbc.password}"/>
            </dataSource>
        </environment>
    </environments>
    <mappers>
        <package name="com.dlct.Mapper"/>
    </mappers>
</configuration>
```

**web.xml文件**

```xml
<servlet>
   <!--注册Sping mvc控制器-->
    <servlet-name>ctrl</servlet-name>
    <servlet-class>org.springframework.web.servlet.DispatcherServlet</servlet-class>
    <!--加载Spring文件-->
    <init-param>
        <param-name>contextConfigLocation</param-name>
        <param-value>classpath:spring-config.xml</param-value>
    </init-param>
</servlet>
<servlet-mapping>
    <servlet-name>ctrl</servlet-name>
    <url-pattern>/</url-pattern>
</servlet-mapping>
```

