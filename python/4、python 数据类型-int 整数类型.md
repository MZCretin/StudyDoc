## int 整数类型

## 1 定义

整型就是十进制整数的统称

## 2 独有功能

无

## 3 公共功能

加减乘除

## 4 类型转换

```python
# bool 转 整型
n1 = int(True)
# 字符串 转 整型
n2 = int("186",base=10)
n2 = int("0b1001",base=2)
n2 = int("0o144",base=8)
n2 = int("0x59",base=16)
# 浮点型 转 整型
n1 = int(8.7) # 结果 8
```

## 5 其他

### **5.1 长整型**

+ Python3：只有整型
+ Python2：整型和长整型 

在python2中跟整型相关的数据类型有2种：int（整型）、long（长整型）,他们都是整数只不过能标识的值范围不同。

![image-20211003134946247](/Users/cretin/document/StudyDoc/python/images/image-20211003134946247.png)

在python3中取出了long只剩下int，并且int长度不再进行限制。

### **5.2 地板除**

+ Python3

  ```python
  v1 = 9/2
  print(v1) # 4.5
  ```

+ Python2

  ```python
  v1 = 9/2
  print(v1) # 4
  
  #如果需要带小数
  from __future__ import division
  v1 = 9/2
  print(v1) # 4.5
  ```

## 