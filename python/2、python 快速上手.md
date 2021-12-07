## 1、编码

+ 编码必须要保持一致，保存和打开要一致，否则会乱码

+ 默认Python解释器以UTF-8的形式打开文件，如果想要修改Python默认解释器的编码，可以这样做：

  ```python
  # -*- coding:gbk -*-
  
  print("我是大哥大")
  ```

+ 建议：使用utf-8编码读取和保存

## 2、输出

将内容呈现给用户。

```python
print("当你老了") 
```

+ 默认 print 在尾部会加换行符：

  ```python
  print("当你老了") 
  print("头发白了")
  
  输出:
  当你老了
  头发白了
  ```

+ 取消默认换行

  ```python
  print("当你老了",end="") 
  print("头发白了",end="")
  
  输出:
  当你老了头发白了
  
  print("当你老了",end=",") 
  print("头发白了",end=",")
  
  输出:
  当你老了,头发白了,
  ```

## 3、初识数据类型

### 3.1 整型(int)

整型就是整数。

```python
print(2 + 10)
print(2 * 10)
print(10 / 2)
print(10 % 3)  # 10对3取余
print(2 ** 4)  # 2的4次方

结果：
12
20
5.0
1
16
```

### 3.2 字符串(str)

文本信息。

```python
# 单行字符串
name1 = "我的名字是mxn"

name2 = '我的名字是"mxn"'

name3 = "我的名字是'mxn'"

# 多行字符串
name4 = """我的
名字
是
mxn
"""

name5 = '''我的
名字
是
"mxn"
'''

print(name1)
print(name2)
print(name3)
print(name4)
print(name5)
```

字符串运算：

+ 加，字符串拼接

  ```python
  print("我是"+"一个好人")
  
  输出:
  我是一个好人
  ```

  

+ 乘，整型和字符串相乘，以实现让字符串重复出现N次并拼接起来

  ```python
  print(3 * "我是mxn")
  
  输出:
  我是mxn我是mxn我是mxn
  ```

### 3.3 布尔类型(bool)

布尔值有两个值：True / False

```python
print(1 > 2)
print(1 < 2)

输出:
False
True
```

### 3.4 类型转换

```pyt
# int() 方法可以将字符串转换成数字
print(int("333"))

# 如果没有办法正常转换 就会报错
# print(int("我是"))

# 非0即真
print(int(True)) # 1
print(int(False)) # 0

# str() 方法可以将数字转换成字符串
print(str(333))

print(str(True)) 
print(str(False))

# bool() 可以将其他类型转换成bool类型
print(bool(0)) # False
print(bool(1)) # True

print(bool("我")) # True
print(bool(None)) # False
print(bool("")) # False
```

说明：

+ 其他所有类型转换为布尔类型时，除了空字符串，None，0，其他都是True

+ 字符串转整型时，只有本身是整型的字符串才能转换，否则报错

+ 想要转换为哪种类型，包裹一下就可以转换

  ```python
  str(...)
  int(...)
  bool(...)
  ```

  

