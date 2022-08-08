# Strings

## Create String

```bash
set message = Hello World
```



## Empty String

一个empty string可以被创建在DOS脚本，通过赋值它没有值，在它初始化的期间，如下：

```c++
Set a=
```



比较的话，必须用[]括起来：

```bash
[%a%]==[]
```



## String Interpolation

这是一种方式，去构造一个新的字符串值从常量，变量，字面值，还有表达式的混合，通过包含它们的值在一个字符串字面值里面。



在DOS脚本，string interpolation可以被使用，使用set命令，并且

排列数值定义的变量，或者任何字面值在一行，当使用set命令的时候。



```bash
@echo off
SET a = Hello
SET b = World
SET /A d = 50
SET c=%a% and %b% %d%
echo %c%
```



```bash
Hello and World 50
```



## String Concatenation

```bash
@echo off
SET a = Hello
SET b = World
SET c = %a% and %b%
echo %c%
```



可以使用set运算符去连接两个字符串，或者一个字符串和一个字母，

或者两个字母。



## String Length



这里有自定义的函数，可以被用于测量长度。

```bash
@echo off
set str = Hello World
call :strLen str strlen
echo String is %strlen% characters long
exit /b

:strLen
setlocal enabledelayedexpansion

:strLen_Loop
   if not "!%1:~%len%!"=="" set /A len+=1 & goto :strLen_Loop
(endlocal & set %2=%len%)
goto :eof
```



找到字符串的实际代码定义在:strLen块里面。

字符串的长度被保存在变量len里面。



## toInt

使用/A转换成数值。

```bash
@echo off
set var = 13145
set /A var=%var% + 5
echo %var%
```



## Align Right

这被用来对齐文本到右边，通常被用来去提升number columns的可读性。



```bash
@echo off
set x = 1000
set y = 1
set y = %y%
echo %x%

set y = %y:~4%
echo %y%
```

空格被添加到变量y，这种情况下，我们添加了9个空格到变量y。



我们使用~4选项去展示字符串y的后4个字符。



注意，=两边不能有空格，不让会赋值出错，教程不知道为啥两侧有空格。



## Left String

抽取字符串前面的部分



```bash
set str=Helloworld
echo.%str%
set str=%str:~0,5%
echo.%str%
```



~0,5描述字符0位置到5位置被显示。



## Remove

```bash
@echo off 
set str = Batch scripts is easy. It is really easy. 
echo %str% 

set str = %str:is = % 
echo %str%
```



is全被移除了。



## Remove Both Ends

用于移除一个字符串的第一个和最后一个字符。

```bash
@echo off 
set str = Batch scripts is easy. It is really easy 
echo %str% 

set str = %str:~1,-1% 
echo %str%
```



## Rmove All Spaces

移除所有的空格通过替换

```bash
@echo off 
set str = This string    has    a  lot  of spaces 
echo %str% 

set str=%str:=% 
echo %str%
```



## Replace is String

替换字符串。

```bash
@echo off 
set str=This message needs changed. 
echo %str% 

set str=%str:needs=has% 
echo %str%
```



## Right String

```bash
@echo off 
set str = This message needs changed. 
echo %str% 

set str = %str:~-8% 
echo %str%
```



获取剩下的8个字符。









