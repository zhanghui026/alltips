# 创建数据库与用户


## 创建数据库与用户

```
1、create schema [数据库名称] default character set utf8 collate utf8_general_ci;--创建数据库

　　采用create schema和create database创建数据库的效果一样。

2、create user '[用户名称]'@'%' identified by '[用户密码]';--创建用户

　　密码8位以上，包括：大写字母、小写字母、数字、特殊字符

　　%：匹配所有主机，该地方还可以设置成‘localhost’，代表只能本地访问，例如root账户默认为‘localhost‘

3、grant select,insert,update,delete,create on [数据库名称].* to [用户名称];--用户授权数据库

　　*代表整个数据库

4、flush  privileges ;--立即启用修改

5、revoke all on *.* from tester;--取消用户所有数据库（表）的所有权限

6、delete from mysql.user where user='tester';--删除用户

7、drop database [schema名称|数据库名称];--删除数据库
```



mysql8

```sql

create user 'antman_opr'@'%' identified WITH mysql_native_password by 'antman_pass';


grant select,insert,update,delete,create on antman.* to antman_opr;
```

