# Function Definition

```bash
:function_name
Do_something
EXIT /B 0
```



调用一个函数

```bash
call:function_name
```



/B %ERRORLEVEL%



# Functions with Parameters

```bash
Call :function_name parameter1, parameter2… parametern
```



在函数内引用参数的操作：

```bash
@echo off
SETLOCAL
CALL :Display 5 , 10
EXIT /B %ERRORLEVEL%
:Display
echo The value of parameter 1 is %~1
echo The value of parameter 2 is %~2
EXIT /B 0
```



# Local Variables in Functions

SETLOCAL命令第一次被用于去保证命令处理器获取一份环境变量的备份。

变量可以被恢复，通过调用ENDLOCAL命令。





