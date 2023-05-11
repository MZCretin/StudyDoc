## 1、插入数据

```sql
insert into 表(列名1,列名2,列名3) values (值1,值2,值3);
insert into 表 values （值1,值2,值3);

insert into student(sid,name,gender) values(1001,'mxn','男');
insert into student values(1001,'mxn','男');
```

## 2、数据修改

```sql
update 表名 set 字段名=值,字段名2=值2;
update 表名 set 字段名=值,字段名2=值2 where 条件;

update student set address = '重启';
update student set address = '广州' where id = 1001;
```

## 3、数据删除

```sql
delete from 表名 [where 条件]
truncate table 表名 或者 truncate 表名;

delete from student where sid = 1001;
delete from student;
truncate table student;
truncate student;
```

