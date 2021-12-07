## 列表

列表，是一个且可变的容器，在里面可以存放多个不同类型的元素。

## 1 定义

```python
user_list = ["苍老师","有坂深雪","大桥未久"]
num_list = [98,88,666,12,-1]
data_list = [1,True,"mxn","宝强","贾乃亮"]
```

## 2 独有功能

+ ### 追加 在原有列表的尾部追加值

  ```python
  data_list = []
  data_list.append("1")
  data_list.append(2)
  data_list.append(True)
  print(data_list) # "1",2,True
  ```

+ ### 批量追加

  ```python
  data_list = [1,3,4]
  data_list1 = [2,5,6]
  data_list.extend(data_list1)
  
  print(data_list) # 1,3,4,2,5,6
  ```

+ ### 插入

  ```python
  data_list = [1,3,4]
  data_list.insert(1,10)
  data_list.insert(10,2 )
  print(data_list)  # 1，10，3，4，2 如果索引位置不存在 如果大于最大值就往后面放，如果小于最小值就往前面放
  ```

+ ### 删除

  ```python
  data_list = [1,2,3,4,5]
  data_list.remove(1)
  # data_list.remove(0) #如果你删除的值不在列表中 会报错
  if(2 in data_list):
      data_list.remove(2)
  print(data_list) # [3, 4, 5]
  ```

+ ### 根据索引删除

  ```python
  data_list = [1,2,3,4,5,6]
  print(data_list.pop())
  print(data_list.pop(2))
  print(data_list)
  输出：
  6
  3
  [1, 2, 4, 5]
  ```

+ ### 清空列表

  ```python
  data_list = [1,2,3,4,5]
  data_list.clear()
  print(data_list) # []
  ```

+ ### 根据值获取索引

  ```python
  data_list = [1,2,3,4,5,1,6]
  print(data_list.index(1)) # 0
  # print(data_list.index(10)) #如果不在列表里面 会报错
  ```

+ ### 列表排序

  ```python
  data_list = [2,1,5,3,7,4,6]
  data_list.sort()
  print(data_list) # 1,2,3,4,5,6,7
  data_list.reverse()
  print(data_list) # 7,6,5,4,3,2,1
  ```

  如果列表中数据类型不一样并且不能进行比较的时候，就会报错

+ ### 反转列表

  ```python
  data_list = [1,4,2,6,3]
  data_list.reverse()
  print(data_list)  #[3, 6, 2, 4, 1]
  ```

## 3 公共功能

+ ### 相加

  ```python
  data_list = [1,2]
  data_list1 = [2,3]
  print(data_list+data_list1) # 1,2,2,3
  ```

+ ### 相乘

  ```python
  data_list = [1,2]
  print(data_list * 3) #[1, 2, 1, 2, 1, 2]
  ```

+ ### 运算符 in , not in

  ```python
  data_list = [1,2,3,4,5]
  print(1 in data_list) # True
  print(1 not in data_list) # False
  ```

+ ### 获取长度

  ```python
  data_list = [1,2,3,4,5]
  print(len(data_list)) # 5
  ```

+ ### 索引 获取值和修改值

  ```python
  data_list = [1,2,3,4,5,6]
  print(data_list[0]) # 1
  print(data_list[1]) # 2
  data_list[0] = 100
  data_list[1] = 101
  print(data_list) # 100,101,3,4,5,6
  del data_list[0] # 101,3,4,5,6
  ```

  注意：超出索引范围会报错

  提示：由于字符串是不可变类型，所以他只有索引读的功能，而列表可以进行读，改，删

+ ### 切片 获取切片和修改切片

  ```python
  data_list = [1,2,3,4,5]
  print(data_list[0:4:2])
  print(data_list[:4:2])
  print(data_list[::2])
  print(data_list[::-1])
  #写
  data_list[0:2] = [110,111]
  print(data_list)
  data_list[2:3]=[222,333,444]
  print(data_list)
  del data_list[0:2]
  print(data_list)
  输出：
  [1, 3]
  [1, 3]
  [1, 3, 5]
  [5, 4, 3, 2, 1]
  [110, 111, 3, 4, 5]
  [110, 111, 222, 333, 444, 4, 5]
  [222, 333, 444, 4, 5]
  ```

+ ### for循环

  ```python
  data_list = [1,2,3,4,5]
  for item in data_list:
      print(item)
  输出：
  1
  2
  3
  4
  5
  ```

  注意：不要在列表循环的过程中删除数据，否则会出现意外

  ```python
  data_list = ["刘德华", "范德彪", "刘华强", "刘尼古拉斯赵四", "宋小宝", "刘能"]
  for index in range(len(data_list) - 1, -1, -1):
      item = data_list[index]
      if item.startswith("刘"):
          data_list.remove(item)
  print(data_list) # ['范德彪', '宋小宝']
  ```

## 4 转换

+ ### int bool 无法转换成list

+ ### str

  ```python
  name = "mxn"
  data = list(name)
  
  print(data) #['m', 'x', 'n']
  ```

+ ### 元祖

  ```python
  v1 = (1,3,5,67) # 元祖
  v2 = list(v1)
  print(v2) #[1, 3, 5, 67]
  ```

+ ### 集合

  ```python
  v2 = {"a","b","c"}
  print(list(v2)) # ['b', 'c', 'a'] 
  ```

## 5 其他

+ 列表嵌套

  列表属于容器，内部可以存放各种数据，所以他也支持列表的嵌套，如：

  ```python
  data = ["1",["2","3","4"],"5","6","7"]
  print(data)
  ```

## 