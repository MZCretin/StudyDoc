## 集合

集合是一个无序，键不重复，且元素只能是键值对的可变的容器。

## 1 定义

```python
v1 = {"k1":1,"k2":2}
v2 = {}
v3 = dict()
v4 = {
  "age": 12,
  "status": True,
  "name": "wupeiqi",
  "hobby": [ '篮球','足球' ]
}
v5 = {
  "穆仙念": 29,
  True: 5,
  123: 5,
  (11,22,33): ["alex","eric"]
}
```

+ ### 是一个容器，可以存储多组数据

+ ### 元素必须是键值对

+ ### 键不重复，重复则会被覆盖

  ```python
  data = { "k1":1, "k1":2 }
  print(data) # { "k1":2 }
  ```

+ ### 无序（在Python3.6+字典就是有序了，之前的字典都是无序）

  ```python
  data = { "k1":1, "k2":2 }
  print(data)
  ```

字典中对键值得要求：

+ 键：必须可哈希。目前为之学到的可哈希的类型，int/bool/str/tuple 不可哈希的类别：list/set/dict。
+ 值：任意类型

一般在什么情况下会用到字典呢？

当我们想要表示一组固定信息时，用字典可以更加的直观，例如：

```python
user_list = [("alex","123"),("admin","666")]
user_list = [{"name":"alex","pwd":"123"},{"name":"alex","pwd":"123"}]
```

## 2 独有功能

+ ### 获取值

  ```python
  v1 = set()
  v1.add(1)
  v1.add("1")
  print(v1) # {1, '1'}
  ```

+ ### 删除元素

  ```python
  v1 = {"1",2,3,4}
  v1.discard("1")
  print(v1) # {2, 3, 4}
  ```

+ ### 交集

  ```python
  s1 = {"刘能","赵四","皮长山"}
  s2 = {"刘科长","冯乡长","皮长山"}
  s3 = s1 & s2
  s4 = s1.intersection(s2)
  print(s3) # {'皮长山'}
  print(s4) # {'皮长山'}
  ```

+ ### 并集

  ```python
  s1 = {"刘能","赵四","皮长山"}
  s2 = {"刘科长","冯乡长","皮长山"}
  s3 = s1 | s2
  s4 = s1.union(s2)
  print(s3) # {'赵四', '冯乡长', '刘能', '刘科长', '皮长山'}
  print(s4) # {'赵四', '冯乡长', '刘能', '刘科长', '皮长山'}
  ```

+ ### 差集

  ```python
  s1 = {"刘能","赵四","皮长山"}
  s2 = {"刘科长","冯乡长","皮长山"}
  s3 = s1 - s2
  s4 = s1.difference(s2)
  print(s3) # {'赵四', '刘能'}
  print(s4) # {'赵四', '刘能'}
  ```

## 3 公共功能

+ ### 减 计算差集

  ```python
  s1 = {"刘能","赵四","皮长山"}s2 = {"刘科长","冯乡长","皮长山"}s3 = s1 - s2print(s4) # {'赵四', '刘能'}
  ```

+ ### & 计算交集

  ```python
  s1 = {"刘能","赵四","皮长山"}s2 = {"刘科长","冯乡长","皮长山"}s3 = s1 & s2print(s3) # {'皮长山'}
  ```

+ ### | 计算并集

  ```python
  s1 = {"刘能","赵四","皮长山"}s2 = {"刘科长","冯乡长","皮长山"}s3 = s1 | s2print(s3) # {'赵四', '冯乡长', '刘能', '刘科长', '皮长山'}
  ```

+ ### 长度

  ```python
  v1 = {"1","2","3"}print(len(v1)) # 3
  ```

+ ### for循环

  ```python
  v1 = {"1","2","3"}for item in v:  	print(item)输出：123
  ```

## 4 转换

其他类型如果想要转换为集合类型，可以通过set进行转换，并且如果数据有重复自动剔除。

提示：int/list/tuple/dict都可以转换为集合。

```python
v1 = "mxn"v2 = set(v1)print(v2) # {"m","x","n"}v1 = [1,2,3,4,5,6,7,7,1]v2 = set(v1)print(v2) # {1, 2, 3, 4, 5, 6, 7}v1 = {11,22,33}v2 = set(v1)print(v2) # {11,22,33}
```

去重的一个重要手段

## 5 其他

+ ### 集合的存储原理

  ![image-20211003224526820](/Users/cretin/document/StudyDoc/python/images/image-20211003224526820.png)

+ ### 元素必须可哈希

  因存储原理，集合的元素必须是可以hash的值，即：内部通过哈希函数把值转换成一个数字。

  ![image-20211003225659699](/Users/cretin/document/StudyDoc/python/images/image-20211003225659699.png)

  目前可哈希的数据类型：int、bool、str、tuple、而list，set是不可哈希的。

  总结：集合的元素只能是 int、bool、str、tuple

  + 转换成功

    ```python
    v1 = [1,2,3,4,5,6,7]v2 = set(v1)print(v2) # {1, 2, 3, 4, 5, 6, 7}
    ```

  + 转换失败

    ```python
    v1 = [11,22,["a","x"],33,44]v2 = set(v1)print(v2) 输出：Traceback (most recent call last):  File "/Users/cretin/code_project/python/day01/列表.py", line 179, in <module>    v2 = set(v1)TypeError: unhashable type: 'list'
    ```

+ ### 查找速度很很快

  因特殊存储原理，集合的查找效率非常高。

+ ### 对比和嵌套

  ![image-20211003230304589](/Users/cretin/document/StudyDoc/python/images/image-20211003230304589.png)

  注意：由于True和False本质上存储的是1和0，而集合又不允许重复，所以在整数0，1，和False、True出现在集合中会出现如下现象:

  ```python
  v1 = {True,1}print(v1) # {True}v2 = {1,True}print(v2) #{1}v3 = {0,False}print(v3) # {0}v4 = {False,0}print(v4) # {False}
  ```

  

