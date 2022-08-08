# Creating Files

创建文件，通过重定向过滤器>。



```bash
@echo off
echo "Hello">C:\new.txt
```



# Writing to Files

```bash
@echo off
dir C:\>C:\new.txt
```



dir C:\是C目录下的所有目录列表，然后写入到文本中。



# Appending to Files

双重定向过滤器>>。这个过滤器可以被用于追加任何输出到一个文件。



```bash
@echo off
echo "This is the directory listing of C:\ Drive">C:\new.txt
dir C:\>>C:\new.txt
```



# Reading from Files

通过FOR循环命令，去获取每一行。



```bash
@echo off
FOR /F "tokens=* delims=" %%x in (new.txt) DO echo %%x
```



delims参数被用于去打碎文本到不同的tokens或者words。

每个word或者token被存储在变量x里面。对于每个从文件中读取的work，一个echo被用去打印word去控制台输出。



# Deleting Files

对于删除文件，Batch Script提供DEL 命令。

```bash
DEL [/P] [/F] [/S] [/Q] [/A[[:]attributes]] names
```



下面的，是选项的描述，可以出现在DEL命令中。



Names，描述一系列一个或多个文件或者目录。通配符会被用来去删除

多个文件。如果一个目录被描述，所有的文件在目录里面的也会被删除。



/A，选择文件去删除基于属性。



attributes，R 只读文件，S 系统文件，H 隐藏文件，一个文件准备同步文档。



# Renaming Files

对于重命名文件，Batch脚本提供了REN或者RENAME命令。



```bash
RENAME [drive:][path][directoryname1 | filename1] [directoryname2 | filename2]
```



# Moving Files

对于移动文件，Batch Script提供了MOVE命令。



```bash
MOVE [/Y | /-Y] [drive:][path]filename1[,...] destinationxxxxxxxxxx MOVE [/Y | /-Y] [drive:][path]filename1[,...] destinationMOVE [/Y | /-Y] []
```



# Files Pipes

管道操作符|获取一个命令行的输出还有重定向它到另一个命令的输入(默认情况下，STDIN)，

如下的命令排序了目录C:\的内容。



```bash
dir C:\ | sort
```



两个命令同时执行，但是排序命令暂停了它直到它接受了dir命令的输出。

排序命令使用了dir命令的输出作为它的输入，并且发送它到句柄1(那个是STDOUT)。



如下的是pipe命令的另一个例子。在这个例子，文件C:\new.txt的内容被发送到sort命令，通过pipe过滤器。

```bash
@echo off
TYPE C:\new.txt | sort
```



# Combining Commands with Redirection Operators

```bash
dir C:\ | find "txt" > AllText.txt
```



如上的命令行，将首先输入所有定义在C:\中的文件，然后使用pipe命令，将找寻所有带.txt扩展的文件。

它将采取这个输入，然后打印到文件AllText.txt中。















