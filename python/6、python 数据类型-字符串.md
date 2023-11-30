## 字符串类型

## 1. 定义

字符串就是一个文本

## 2 独有功能

```python
# 1、判断字符串是否以XX开头？得到一个bool值
v1 = "叨逼叨的一天，烦死了"
print("你是不是骂人了："+str(v1.startswith("叨逼叨")))
输出：
你是不是骂人了：True

# 2、判断字符串是否以XX结尾
v1 = "叨逼叨的一天，烦死了"
print(str(v1.endswith("烦死了")))
输出：
True

# 3、判断字符串是否为十进制数字
v1 = "111"
print(v1.isdecimal())
输出：
True

# 4、去除字符串两边的空白，它会去除空格，换行符，制表符 lstrip() 去除左边的空格，rstrip() 去除右边的空格
v1 = "   13213   "
print(v1.strip())
print(v1.strip().isdecimal())
输出：
13213
True

# 5、去除字符串两边指定的内容，lstrip() 去除左边的内容，rstrip() 去除右边的内容
v1 = "#我是一个小可爱#"
print(v1.strip("#"))
输出：
我是一个小可爱

# 6、字符串大写小写转换
v1 = "i am Hero"
print(v1.upper())
print(v1.upper().lower())
输出：
I AM HERO
i am hero

# 7、字符串内容替换
v1 = "你是个好人，但是好人不适合我"
print(v1.replace("好人","贱人"))
输出：
你是个贱人，但是贱人不适合我

# 8、字符串切割
v1 = "1|2|3|4|5|6"
print(v1.split("|"))
print(v1.split("|",2)) #指定切几个
print(v1.rsplit("|",1)) #指定切割方向

#应用场景：通过文件路径获取后缀名
file_path = "xxx/xxx/xxx/xxxx/xxx.mp4"
date_list = file_path.rsplit(".",1)
print(date_list[0])
print(date_list[1])
输出：
['1', '2', '3', '4', '5', '6']
['1', '2', '3|4|5|6']
['1|2|3|4|5', '6']
xxx/xxx/xxx/xxxx/xxx
mp4

# 9、字符串拼接
v1 = ["mxn","是","大可爱"]
print("*".join(v1))
输出：
mxn*是*大可爱

# 10、字符串格式化
此处略，看上面专题

# 11、字符串转换为字节类型
data = "嫂子" # unicode 字符串类型
data.encode("utf-8") # utf-8 字节类型
data.encode("gbk") # gbk 字节类型

# 字节转换成字符串
data.encode("utf-8").decode("utf-8")
data.encode("gbk").decode("gbk")

# 12、将内容居中，居左，居右展示
v1 = "隔壁老王"
print(v1.center(20,"*")) #凑够20个长度，前后位置加填充字符
print(v1.ljust(20,"*")) #凑够20个长度，右边位置加填充字符
print(v1.rjust(20,"*")) #凑够20个长度，左边位置加填充字符
输出：
********隔壁老王********
隔壁老王****************
****************隔壁老王

# 13、字符串填充0
v1 = "mxn"
print(v1.zfill(10)) # 左边填充0
# 应用场景 处理二进制数据
data = "101" #"00000101
v1 = data.zfill(8)
print(v1)
输出：
0000000mxn
00000101
```

## 3 公共功能

+ ### 相加

  ```python
  v1 = "mxn"+"大sb"
  print(v1)
  输出：
  mxn大sb
  ```

+ ### 相乘

  ```python
  data = "mxn" * 3
  print(data) #mxnmxnmxn
  ```

+ ### 长度

  ```python
  data = "mxn"
  print(len(data)) # 6
  ```

+ ### 获取字符串的字符 索引 字符串中能通过索引取值，不能修改值

  ```python
  message = "来点py交易"
  print(message[0]) # 来
  print(message[1]) # 点
  print(message[2]) # p
  
  print(message[-1]) # 易
  print(message[-2]) # 交
  print(message[-3]) # y
  ```

+ ### 获取字符串中的子序列，切片

  ``` python
  message = "来点py交易"
  
  print(messqge[0:2]) # 来点
  print(message[3:]) # y交易
  print(message[:3]) # 来点p
  print(message[3:-1]) # y交
  ```

  注意：在字符串切片只能读取数据，不能修改数据

+ ### 步长 跳着取字符串的内容

  ```python
  name = "生活不是电影，生活比电影苦"
  
  # 前取后不取
  print(name[0:5:2]) # 生不电
  print(name[:8:2]) # 生不电，
  print(name[2::3]) # 不影活影
  print(name[::2]) # 生不电，活电苦
  print(name[8:1:-1]) # 活生，影电是不 倒序取值
  ```

## 4 转换

```python
num = 999
data = str(num)
print(data) # "999"
```

一般情况下都是数字转字符串

## 5 其他

+ 字符串不可被更改