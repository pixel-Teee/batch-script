# Arrays



数组的每个元素被定义，通过set命令。

for循环将被去请求通过数组的值。



## Creating an Array

一个数组被创建，通过使用如下的set命令。

```bash
set a[0]=1
```



另一种方式去实现数组，是去定义一个值的列表，并且迭代它，通过列表的值。

```bash
@echo off
set list = 1 2 3 4
(for %%a in (%list%) do(
	echo %%a
))
```



注意a的前面是两个%%



## Accessing Arrays

从一个数组取得一个值，通过使用子索引标签。



```bash
@echo off
set a[0]=1
echo %a[0]%
```

## Modifying an Array

加到末尾和修改某个值，都使用set。



## Itearting Over an Array

```bash
@echo off 
setlocal enabledelayedexpansion 
set topic[0]=comments 
set topic[1]=variables 
set topic[2]=Arrays 
set topic[3]=Decision making 
set topic[4]=Time and date 
set topic[5]=Operators 

for /l %%n in (0,1,5) do ( 
   echo !topic[%%n]! 
)
```



for循环对于/L参数，用于移动，通过一个范围，被用于迭代一个数组。



## Length of an Array

只能通过迭代数组获取长度。



```bash
@echo off 
set Arr[0]=1 
set Arr[1]=2 
set Arr[2]=3 
set Arr[3]=4 
set "x = 0" 
:SymLoop 

if defined Arr[%x%] ( 
   call echo %%Arr[%x%]%% 
   set /a "x+=1"
   GOTO :SymLoop 
)
echo "The length of the array is" %x%
```



## Creating Structures in Array



```bash
@echo off 
set obj[0].Name=Joe 
set obj[0].ID=1 
set obj[1].Name=Mark 
set obj[1].ID=2 
set obj[2].Name=Mohan 
set obj[2].ID=3 
FOR /L %%i IN (0 1 2) DO  (
   call echo Name = %%obj[%%i].Name%%
   call echo Value = %%obj[%%i].ID%%
)
```







