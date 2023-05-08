### 1、数据类型

| 分类       | 类型         | 大小             | 描述                             |
| ---------- | ------------ | ---------------- | -------------------------------- |
| 数值类型   | tinyint      | 1字节            | 小整数值                         |
| 数值类型   | smallint     | 2字节            | 大整数值                         |
| 数值类型   | mediumint    | 3字节            | 大整数值                         |
| 数值类型   | int或integer | 4字节            | 大整数值                         |
| 数值类型   | bigint       | 8字节            | 极大整数值                       |
| 数值类型   | float        | 4字节            | 单精度浮点数值                   |
| 数值类型   | double       | 8字节            | 双精度浮点数值                   |
| 数值类型   | decimal      |                  | 小数值（精确定点数）             |
| 字符串类型 | char         | 0-255字节        | 定长字符串                       |
| 字符串类型 | varchar      | 0-65535字节      | 变长字符串                       |
| 字符串类型 | tinyblob     | 0-255字节        | 不超过255字符的二进制数据        |
| 字符串类型 | tinytext     | 0-255字节        | 短文本字符串                     |
| 字符串类型 | blob         | 0-65535          | 二进制形式的长文本数据           |
| 字符串类型 | text         | 0-65535字节      | 长文本数据                       |
| 字符串类型 | mediumblob   | 0-16777215字节   | 中等长度二进制                   |
| 字符串类型 | mediumtext   | 0-16777215字节   | 中等长度文本                     |
| 字符串类型 | longblob     | 0-4294967295字节 | 极大二进制                       |
| 字符串类型 | longtext     | 0-4294967295字节 | 极大字符串                       |
| 日期类型   | date         | 3                | yyyy-mm-dd 日期值                |
| 日期类型   | time         | 3                | Hh:mm:ss 时间值或持续时间        |
| 日期类型   | year         | 1                | yyyy 年份值                      |
| 日期类型   | datetime     | 8                | yyyy-MM-dd HH:mm:ss 混合日期时间 |
| 日期类型   | timestamp    | 4                | yyyy-MM-dd HH:mm:ss 混合时间戳   |

### 2、创建表

```sql
create table xxx (属性名 属性类型 长度 字段注释)
```

### 3、修改表

添加字段

```sql
ALTER TABLE 表名 ADD 字段名 类型(长度) [COMMENT 注释] [约束];
```

修改字段数据类型

```sql
ALTER TABLE 表名 MODIFY 字段名 新数据类型(长度);
```

修改字段名和字段类型

```sql
ALTER TABLE 表名 CHANGE 旧字段名 新字段名 类型(长度) [COMMENT 注释] [约束];
```

删除字段

```sql
ALTER TABLE 表名 DROP 字段名
```

修改表名

```sql
ALTER TABLE 表名 RENAME TO 新表名
```

删除表

```sql
DROP TABLE[if exists] 表名
//删除指定表，并重新创建该表
TRUNCATE TABLE 表名
```

