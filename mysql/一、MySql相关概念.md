### 一、sql、DB、DBMS分别是什么，他们之间的关系？

+ DB

  DataBase（数据库，数据库实际上在硬盘上以文件的存在）

+ DBMS

  DataBase Management System （数据库管理系统，常见的有：MySQL Oracle DB2 Sybase SqlServer）

+ SQL

  结构化查询语言，是一门标准通用的语言，标准的sql适用于所有的数据库产品。

  SQL属于高级语言，只要能看懂英语单词的，写出来的sql语句，可以读懂什么意思。

  SQL语句在执行的时候，实际上内部也会先进行编译，然后再执行sql。（sql语句的编译由DBMS完成）

+ DBMS负责语句的执行，通过执行sql语句来操作DB当中的数据

+ DBMS-（执行）-> SQL -（操作）-> DB

### 二、数据库表table

table是数据库的基本组成单元，所有的数据都以表格的形式组织，目的是可读性强

一个包括行和列：

行：被称为数据/记录 data

列：被称为字段（column）

| 学号（int） | 姓名（varchar） | 年龄（int） |
| ----------- | --------------- | ----------- |
| 110         | 张三            | 20          |
| 120         | 李四            | 21          |

每一个字段应该包括哪些属性：

字段名、数据类型、相关的约束

### 三、sql分类

+ DQL (数据查询语言)：查询语句，凡是select语句都是DQL
+ DML (数据操作语言)：insert delete update 对表当中的数据进行增删改
+ DDL (数据定于语言)：create drop alter 对表结构的正删改
+ TCL (事务控制语言)：commit 提交事务、rollback回滚事务，（TCL中的T是Transaction）
+ DCL (数据控制语言)：grant授权、revoke撤销权限

### 四、导入数据

+ 1、登录管理系统

  mysql -u root -p

+ 2、查看有哪些数据库

  show database：（这个不是SQL语句，属于MySql的命令） 

  select database(); //查看当前使用的数据库

+ 3、创建属于我们自己的数据库

  create datebase [if not exists] mxn [default charset 字符集] [collate 排序规则]; （这个不是SQL语句，属于MySql命令）

+ 4、使用mxn数据

  use mxn;（这个不是SQL语句，属于MySql命令）

+ 5、查看当前使用的数据库中有哪些表

  show tables;（这个不是SQL语句，属于MySql命令）

+ 6、初始化数据

  source xxxx.sql 

### 五、sql脚本文件

当前一个文件的扩展名是.sql，并且该文件中编写了大量的sql语句，我们称这样的文件sql脚本。

使用sourse命令可以直接执行sql，sql脚本中的数据量太大的时候，无法打开，请使用source命令完成初始化。

### 六、删除数据库

drop datebase mxn;

### 七、查看表结构

desc mxn_user;

### 八、查看当前使用的数据库

select database()

### 九、查看当前使用的数据库版本

select version()

### 十、终止一条语句

\c

### 十一、退出mysql

exit

### 十二、查看建表语句

show create table mxn;

