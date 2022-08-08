批处理文件会被cmd.exe执行。



Batch文件可以在命令提示符或Start-Run中运行。在这样的情况下，完整的路径名必须被使用，

除非文件路径在环境变量中。



可以把batch文件的路径添加到系统变量路径下，或者找到这个批处理文件，自己执行。



# Commands

|             |                                                              |
| ----------- | ------------------------------------------------------------ |
| VER         | 这个batch命令表示你使用的MS-DOS的版本                        |
| ASSOC       | 用于将扩展名和文件类型相互关联，显示现存的关联，或者删除一个关联 |
| CD          | 改变目录，或者显示现在的目录                                 |
| CLS         | 清屏                                                         |
| COPY        | 拷贝文件从一个地方到另一个地方                               |
| DEL         | 删除文件                                                     |
| DIR         | 展示目录的内容                                               |
| DATE        | 找到系统时间                                                 |
| ECHO        | 显示消息，或者打开或关闭命令回显                             |
| EXIT        | 退出DOS控制台                                                |
| MD          | 创建一个新目录在当前的位置                                   |
| MOVE        | 移动文件或者目录在目录之间                                   |
| PATH        | 显示或者设置PATH变量                                         |
| PAUSE       | 提示用户，并且等待一行输入                                   |
| PROMPT      | 改变或者重置cmd.exe提示                                      |
| RD          | 移除目录，但是目录需要是空的，在移除之前                     |
| REN         | 重命名文件和目录                                             |
| REM         | 命令行被用来去标记批处理文件，防止注释的内容被执行           |
| START       | 开始一个新程序在一个新窗口，或者打开一个文档                 |
| TIME        | 设置或显示时间                                               |
| TYPE        | 打印一个文件的内容或者文件到输出                             |
| VOL         | 显示磁盘的卷标                                               |
| ATTRIB      | 显示或者设置文件的属性在当前的目录                           |
| CHKDSK      | 检查磁盘，对于任何问题                                       |
| CHOISE      | 提供一系列选项给用户                                         |
| CMD         | 调用另一个命令提示符的实例                                   |
| COMP        | 比较两个文件基于大小                                         |
| CONVERT     | 转换一个卷从FAT16或者FAT32文件系统到NTFS文件系统             |
| DRIVERQUERY | 展示所有安装的磁盘驱动和它们的属性                           |
| EXPAND      | 抽取文件从压缩的.cab cabinet文件                             |
| FIND        | 查询一个文件在文件或者输入，输出匹配行                       |
| FORMAT      | 格式化一个磁盘，去使用基于window的文件系统，比如FAT，FAT32或者NTFS，从而覆盖磁盘先前的内容 |
| HELP        | 展示windows提供的命令行                                      |
| IPCONFIG    | 显示windows IP配置，展示配置，通过连接，还有连接的名字       |
| LABEL       | 添加，设置或者移除一个磁盘标签                               |
| MORE        | 显示一个文件或者多个文件的内容，一个屏幕在一个时间           |
| NET         | 提供不同的网络服务，依赖于命令行的使用                       |
| PING        | batch命令发送IMCP/IP "echo"包到网络，到指定的地址            |
| SHUTDOWN    | 命令关闭一个电脑，或者logs off现在的用户                     |
| SORT        | 从源文件获取输入，排序它的内容，基于字典序地                 |
| SUBST       | 赋值一个驱动字母到一个本地文件夹，显示现在的任务，或者移除一个任务 |
| SYSTEMINFO  | 命令行显示一个电脑的配置还有它的操作系统                     |
| TASKKILL    | 关闭一个或者多个任务                                         |
| TASKLIST    | 显示任务，包括任务名和进程ID                                 |
| XCOPY       | 拷贝文件和目录在一个更高级的方式                             |
| TREE        | 显示现在目录的子目录的树到任何递归或者深度的层次             |
| FC          | 展示不同在两个文件之间                                       |
| DISKPART    | 展示和配置磁盘分割的属性                                     |
| TITLE       | 设置标题显示在当前的控制台窗口                               |
| SET         | 显示当前系统的环境变量                                       |



# Files

创建，保存，执行，还有修改批处理文件。



## Creating Batch Files



```bash
:: deletes all files in the current directory
@ECHO OFF
DEL .
DR
```

删除当前目录下的所有文件



```bash
@echo off
```

默认情况下，执行一条命令就显示一条，这个会关闭命令的显示



通常也会输入REM，跟着REM后面的是提示内容。



```c++
@echo off
Rem This is for listing down all the files in the directory Program files
dir "C:\Program Files" > C:\lists.txt
echo "The program has completed"
```



dir重定向"C:\Program Files"到C:\lists.txt，输出一个字符串到这个文件中。



# Variables

在batch文件中，有两种变量，一种对于参数，可以被传递，当batch文件被调用的时候，还有一种通过设置命令行。



## Command Line Arguments

批处理脚本提供命令行参数的概念，参数可以被传递到批处理文件，当调用的时候。

参数可以被调用从batch files，通过变量%1，%2，%3。



## Set Command

通过set命令初始化。



```bash
set /A variable-name=value
```

variable-name你想设置的变量的名字

value是值，要被设置的

/A 这是一个开关，如果值本身为数值，需要使用这个



```bash
@echo off
set message=Hello World
echo %message%
```



## Working with Numeric Values

```bash
@echo off
SET /A a = 5
SET /A b = 10
SET /A c = %a% + %b%
echo %c%
```

使用/A开关，可以和数值进行操作。



```bash
@echo off
set globalvar = 5
SETLOCAL
set var = 13145
set /A var = %var% + 5
echo %var%
echo %globalvar%
ENDLOCAL
```

var会在ENDLOCAL结束后，销毁，局部变量在SETLOCAL和ENDLOCAL之间。



## Working with Environment Variables

如果你有变量，被用于整个批处理文件，最好使用环境变量。

```bash
@echo off
echo %JAVA_HOME%
```



# Comments

为创建的脚本添加添加注释或者文档是一种很好的方法。



## Comments Using the Rem Statement



这里有两种方式去创建注释在Batch Script中，第一种，是通过Rem命令。



## Comments Using the :: Statement

任何在::语句后的，将会被对待为注释，并且不会被执行。



























