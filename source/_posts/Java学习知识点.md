title: Java学习

tags: 

- Java
- 面试

categories:

- 面试

top:2

type:

- picture

description: <center><h4>Java知识点总结</h4></center>

photo:  

- http://image.mabiao.xyz/blog/20151031_124258.jpg

---

<!-- more -->

---

# Java基础

#### 1. JVM 内存可简单分为三个区：

1、**堆区（heap）**：用于存放所有对象，是线程共享的（注：数组也属于对象）

2、**栈区（stack）**：用于存放基本数据类型的数据和对象的引用，是线程私有的（分为：虚拟机栈和本地方法栈）

3、**方法区（method）**：用于存放类信息、常量、静态变量、编译后的字节码等，是线程共享的（也被称为非堆，即 None-Heap）

**Java 的垃圾回收器（GC）主要针对堆区**

### 2. 抽象类和接口对比



![img](http://image.mabiao.xyz/blog/14928266-97ae19da2cc6279a)

# Java Web

## 一、Servlet/JSP/Tomcat

###  1.什么是Servlet

>  Servlet定义：Servlet 是在服务器上运行的小程序。一个 servlet 就是一个 Java 类，并且可以通过 “请求—响应” 编程模式来访问的这个驻留在服务器内存里的 servlet 程序。

Servlet类继承关系图如下：

<img src ="http://image.mabiao.xyz/blog/1535532891036.png" alt="Servlet类继承关系图" width="50%" height="50%" align="middle" />



Servlet三种实现方式：

- 实现javax.servlet.Servlet接口
- 继承javax.servlet.GenericServlet类
- 继承javax.servlet.http.HttpServlet类

> **通常会去继承HttpServlet类来完成Servlet。**

### 2.Servlet执行过程

> 主要描述了从浏览器到服务器，再从服务器到浏览器的整个执行过程，分以下几个步骤：
>
> 1. 浏览器请求
> 2. 服务器创建对象
> 3. 调用init方法
> 4. 调用service方法
> 5. 向浏览器响应

**浏览器请求过程**

<img src="http://image.mabiao.xyz/blog/20180521175251513.png" width="50%" />

浏览器向服务器请求时，服务器不会直接执行我们的类，而是到 web.xml 里寻找路径名 :

① 浏览器输入访问路径后，携带了请求行，头，体 

② 根据访问路径找到已注册的 servlet 名称

③ 根据映射找到对应的 servlet 名 

④ 根据根据 servlet 名找到我们全限定类名，即我们自己写的类

> 总结：根据URL找到已经注册的servlet名称，根据servlet名称找到相应的全限定类

**服务器创建对象**

<img src="http://image.mabiao.xyz/blog/20180521182037787.png" alt="img " style="zoom:50%;" />

① 服务器找到全限定类名后，通过反射创建对象，同时也创建了 servletConfig，里面存放了一些初始化信息（**注意服务器只会创建一次 servlet 对象，所以 servletConfig 也只有一个**）

> 总结：服务器找到全限定类名后通过**反射**创建类的对象，同时创建servletConfig（放一些初始化信息）

**调用init方法**

<img src="http://image.mabiao.xyz/blog/20180521183945631.png" alt="img" style="zoom:50%;" />

① 对象创建好之后，首先要执行 init 方法，但是我们发现我们自定义类下没有 init 方法，所以程序会到其父类 HttpServlet 里找

② 我们发现 HttpServlet 里也没有 init 方法，所以继续向上找，即向其父类 GenericServlet 中继续寻找,在 GenericServlet 中我们发现了 init 方法

③ 则执行 init 方法（对接口 Servlet 中的 init 方法进行了重写）

>  注意： 在 GenericServlet 中执行 public void init(ServletConfig config) 方法的时候，又调用了自己无参无方法体的 init() 方法，其目的是为了方便开发者，如果开发者在初始化的过程中需要实现一些功能，可以重写此方法。

> 总结：调用init方法，通过继承关系，逐层向上找，在GenericServlet 类中找到(重写了servlet接口中的init方法)

**调用service方法**

<img src="http://image.mabiao.xyz/blog/20180521212619975.png" alt="img" style="zoom:50%;" />

接着，服务器会先创建两个对象：ServletRequest 请求对象和 ServletResponse 响应对象，用来封装浏览器的请求数据和封装向浏览器的响应数据

 ① 接着服务器会默认在我们写的类里寻找 service(ServletRequest req, ServletResponse res) 方法，但是 DemoServlet 中不存在，那么会到其父类中寻找 

② 到父类 HttpServlet 中发现有此方法，则直接调用此方法，并将之前创建好的两个对象传入

 ③ **然后将传入的两个参数强转，并调用 HttpServlet 下的另外个 service 方法** 

④ 接着执行 `service(HttpServletRequest req, HttpServletResponse resp)`方法，在此方法内部进行了判断请求方式，并执行doGet和doPost，但是doGet和doPost方法已经被我们自己重写了，所以会执行我们重写的方法 看到这里，你或许有疑问：为什么我们不直接重写service方法？ 因为如果重写service方法的话，我们需要将强转，以及一系列的安全保护判断重新写一遍，会存在安全隐患。

> 总结：服务器按照继承关系寻找service(ServletRequest req, ServletResponse res) 方法，对对象进行强转，再将强转对象传到另一个service方法中，调用service方法，此方法中doGet和doPost被我们重写，因此执行我们重写的方法

**向浏览器响应**

<img src="http://image.mabiao.xyz/blog/20180521214423142.png" alt="img" style="zoom:50%;" />

> 总结：将doGet和doPost方法返回的内容传给浏览器

### 3.Servlet生命周期

<img src="http://image.mabiao.xyz/blog/1535535812505.png" alt="img" style="zoom:50%;" />

- `void init(ServletConfig servletConfig)`：Servlet对象创建之后马上执行的初始化方法，只执行一次；
- `void service(ServletRequest servletRequest, ServletResponse servletResponse)`：每次处理请求都是在调用这个方法，它会被调用多次；
- `void destroy()`：在Servlet被销毁之前调用，负责释放 Servlet 对象占用的资源的方法；

**总结（面试会问）：**　　　

1）Servlet何时创建

```html
默认第一次访问servlet时创建该对象（调用init()方法）
```

2）Servlet何时销毁

```html
服务器关闭servlet就销毁了(调用destroy()方法)
```

3）每次访问必须执行的方法

```html
public void service(ServletRequest arg0, ServletResponse arg1)
```