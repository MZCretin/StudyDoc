## 1、介绍

Python的创始人为吉多·范罗苏姆。1989年的圣诞节期间，Guido开始写Python语言的编辑器。Python这个名字，来自Guido所挚爱的电视剧Monty Python‘s Flying Circus。他希望这个新的语言能符合他的理想，创作一种c和shell之间，功能全面，易学易用，可拓展的语言。

全球众多编程语言，为何Python语言可以脱颖而出成为业界炙手可热的语言？

原因如下：

+ 语法简洁&适合小白
+ 类库的强大
+ 开发效率高

## 2、Python解释器种类

由于Python太火爆了，所以很多公司都开发了Python解释器（用来翻译python代码成为计算机能够识别的命令）

+ CPython【主流】：底层是由C语言开发出来的Python解释器

+ JPython，是由Java语言开发出来的Python的解释器，方便与Python和java做集成

+ IronPython：是基于C#语言开发出来的Python解释器，方便代码与C#做集成

+ RubyPython

+ PyPy：是对CPython的优化，他的执行效率提高了，引入编辑器的功能，本质上将Python代码进行编译，再去执行编译后的代码

+ ...

  注意：我们常说的Python解释器就是CPython解释器。

## 3、CPython解释器的版本

CPython解释器主要有两大版本：

+ 2.x 目前最新的Python 2.7.18  2020后不再维护 
+ 3.x 目前最新的是3.9.0版本

## 4、环境搭建

### 4.1 安装Python解释器

1、下载解释器 3.9.0

```shell
官网：https://www.python.org/
下载地址：https://www.python.org/downloads/release/python-390/   ，在Files下面找到你对应的系统的安装包
```

2、安装

​	双击下载的安装包，一路下一步下一步就好了

​	Mac默认安装目录：

```shell
/Library/Frameworks/Python.framework/Versions/3.9

在bin目录下，有一个python3.9文件，他就是解释器的启动文件。
```

3、运行Hello验证环境

```python
print("hello world")
```

### 4.2 安装Pycharm编辑器

好处：

+ 帮助我们快速编写代码，用Pycharm可以大大提高写代码的效率，

+ 运行代码

使用：

+ 下载Pycharm

  https://download.jetbrains.com/python/pycharm-professional-2020.1.dmg

+ 安装

+ 破解

  下载破解文件，安装完成之后将破解文件.zip拖入到编辑器内，进行破解

  链接: https://pan.baidu.com/s/1CdvDyRpT1LPzpacHyplIzw 提取码: vcq8 