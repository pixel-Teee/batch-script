# Decision Making

## If Statement

```bash
@echo off 
SET /A a = 5 
SET /A b = 10 
SET /A c = %a% + %b% 
if %c%==15 echo "The value of variable c is 15" 
if %c%==10 echo "The value of variable c is 10"
```



```bash
@echo off 
SET /A a = 5 
SET /A b = 10
SET /A c = %a% + %b% 
if %c%==15 (echo "The value of variable c is 15") else (echo "Unknown value") 
if %c%==10 (echo "The value of variable c is 10") else (echo "Unknown value")
```



## Goto Statement

```bash
goto :label
...some commands
:label
...some other commands
```



