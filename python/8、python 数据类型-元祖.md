## 元祖

是一个有序且不可变的容器。在里面可以存放多个不同类型的元素。

## 1 定义

```python
v1 = (11,22,33)
v2 = ("mxn","zp")
v3 = (True,123,"mxn",[1,2,3,4,5])

#建议：在元祖的最后多加一个逗号
v3 = ("1","2",)
```

## 2 独有功能

无

## 3 公共功能

+ ### 相加

  ```python
  data = (1, 2, 3,)
  data2 = (4, 5, 6,)
  print(data + data2) # (1, 2, 3, 4, 5, 6)
  ```

+ ### 相乘

  ```python
  data = (1, 2, 3,)
  print(data * 3) # (1, 2, 3, 1, 2, 3, 1, 2, 3)
  ```

+ ### 获取长度

  ```python
  data = (1, 2, 3,) 
  print(len(data)) # 3
  ```

+ ### 索引

  ```python
  data = ("1","2","3",)
  print(data[0]) # "1"
  print(data[1]) # "2"
  print(data[2]) # "3"
  ```

+ ### 切片

  ```python
  data = (1,2,3,4,)
  print(data[0:2]) #(1, 2)
  ```

+ ### 步长

  ```python
  data = (1,2,3,4,)
  print(data[::-1]) #(4, 3, 2, 1)
  ```

+ ### for循环

  ```python
  data = [1,2,3,4,5,]
  for item in data:
    	print(item)
  ```

## 4 转换

其他类型转换为元祖，使用`tuple(其他类型)`,目前只有字符串和列表可以转换为元祖。

```python
name = "mxn"
print(tuple(name)) #('m', 'x', 'n')

name = ["mxn","zp",1,]
print(tuple(name)) #('mxn', 'zp', 1)
```

## 5 其他

+ ### 嵌套

  ```python
  tu = ('今天姐姐不在家','姐夫和小姨子在客厅聊天',('姐夫文问小姨子税后多少钱','小姨子低声说到和姐夫还提钱',),)
  print(tu[0])
  print(tu[1])
  print(tu[2][0])
  print(tu[2][1])
  
  输出：
  今天姐姐不在家
  姐夫和小姨子在客厅聊天
  姐夫文问小姨子税后多少钱
  小姨子低声说到和姐夫还提钱
  ```

## 