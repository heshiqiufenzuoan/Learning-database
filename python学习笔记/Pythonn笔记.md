

> #                                       **Python笔记**

## 一. python语言的简介及运行机制

### 1. **python语言简介：**

- 面向对象的跨平台（可在任何系统上运行python代码）编程语言，一切皆对象；

- 解释型编程语言；

- 是一种交互式语言，即在终端中进行命令编程，可在提示符后直接执行代码；

- python具有强大而又丰富的库，又称为胶水语言，看可以把其他语言写的模块轻松的结合在一起；

- 支持广泛的程序开发，从简单到文字处理到WWW浏览器再到游戏开发，无所不能；

  **总之来说python是一门面向对象弱类型解释型动态语言**

### 2. python优缺点：

- 易于维护和学习；
- 提供了大量的工具库；
- 可扩展且支持GUI图形化界面的编程；
- 对于大多数数据库都有相应的接口；

### 3. **python IDE（Intergreated Development Environment集成开发环境）安装**：

- Windows x86-64 embeddable zip file为可嵌入式安装文件；
- Windows x86-64 executable installer为可执行的安装文件；
- Windows x86-64 web based installer为基于Web的安装文件；

### 4. pycharm软件界面设置与配置

1. pycharm软件介绍：

   基于eclipse开发的开源软件，适用于整体开发较大项目。负责繁琐的工作细节，节省宝贵的时间，善用以键盘操作为主的编程方法， pycharm完全理解代码的每个面向，依靠它的智能化代码补全，实时检查和快速修复等功能，轻松进行项目导航。其有以下优点：

   集成python需要的模块，方便开发；

   语法高亮，快速识别代码，方便开发；

   代码提示。

2. 搭建pycharm软件的开发环境：

   首先安装JDK（JDK是整个java开发的核心，它包含了JAVA的运行环境，JAVA工具和JAVA基础的类库。） / 官网下载 （大约270M）/ 按步提示骤安装。

   手动卸载 /  360软件 / 电脑管家卸载 ， 在手动卸载中需要把所有相关文件卸载干净，否则再次安装的时候会出现兼容性等问题。

3. 界面初始化：

   当各种配置之后页面较混乱时，只需要在C盘 / 用户 / 29172（账户）/ 删除“.pycharm.2019.2(或其他版本)”。

### 5.python运行平台：

1. ​     通过win+R得到的框输入cmd进入python控制台（也 称为REPL环境，R=read读; E=eval 执行; P=print 输出; L=Loop循环）；
2. ​     通过python软件
3. ​     通过pycharm软件

### 6. python代码在计算机中的执行过程：

​      源码编译成字节码（也就是.pyc格式）------>进入python虚拟机------>执行编译好的字节码------>

​        在了解python代码执行过程，首先应该理解PyCodeProject文件和Pyc文件，首先pyc文件包含pycodeproject文件，pycodeproject文 包含python程序运行时保存的编译的结果，而pyc文件则包含python解释器写入的pycodeproject文件。

1. 当python文件第一次运行时，首先将python文件编译成pycodeproject文件运行，运行后保存在pyc文件中。
2. 当python文件第二次运行时，只需要寻找pyc文件即可，如果找不到则按第一次执行的步骤运行。

------

------

------

