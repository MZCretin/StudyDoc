### 1、定义

Lua是一个简洁轻量可扩展的脚本语言

### 2、nginx+lua优势

充分的结合Nginx的并发处理epoll优势和Lua的轻量实现简单的功能和高并发的场景

### 3、基础语法

```java
yum install lua
//运行
lua 
> print("Hi I'm jeson")
lua ./test.lua
//注释
-- 行注释
--[[
  块注释
--]]
//变量
a = 'alo\n123'
a = 'alo\n123\'
a = '\97lo\10\04923'
a = [[alo
     123]]
布尔类型只有nil和false false 数字0，空字符串，都是true。
lua中的变量如果没特殊说明，全是全局变量。局部变量前面加local
//while
sum = 0
num = 0
while num < 100 do
  sun = sum + 1
  num = num + 1
end
print("sum=",sum)
lua中没有++或者是+=
//for循环
sum = 0
for i = 1,100 do
  sum = sum + 1
end
//判断
if age == 40 and sex == "Male" then
  print("大于40岁的男人")
elseif age > 60 and sex ~= "Female" then
  print("非女人而且大于60")
else local age = io.read()
  print("Your age is ",age)
end
```



### 4、Nginx+Lua环境

```java
1、LuaJIT
2、ngx_devel_kit 和 lua-nginx-module
3、重新编译nginx
```



### 5、实战-灰度发布

按照一定的关系区别，分部分的代码进行上线，使代码的发布能平滑过渡上线