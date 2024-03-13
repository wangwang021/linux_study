# 学习mysql的记录

## 1. mysql的安装

`sudo apt install mysql-server`

## 2. mysql的配置

## 3. mysql的登录

`mysql -u root -p`

## 4. mysql数据库操作命令

### 4.1 创建数据库

`create database test;`

### 4.2 删除数据库

`drop database test;`

### 4.3 查询所有数据库名

`show databases;`

### 4.4 切换到数据库

`use test;`

## 5. mysql表操作命令

### 5.1 查询数据库表名

`show tables;`

### 5.2 查询表结构

`desc test;`

### 5.3 创建表

```sql
create table test (
    id int, name varchar(20) comment 'id',
    name varchar(20) comment '姓名',
    age int comment '年龄',
    sex varchar(10) comment '性别',
    );
```

### 5.4 修改表

#### 添加字段

`alter table test add column address varchar(20) comment '地址';`

#### 修改字段

`alter table test modify column name varchar(20) comment '姓名';`
`alter table test change column name varchar(20) comment '姓名';`
`alter table test change name other_name varchar(30) comment '姓名';`

#### 删除字段

`alter table test drop column address;`

#### 修改表名

`alter table test rename to test1;`

### 5.5 删除表

`drop table test1;`

## 6. mysql数据操作命令

### 6.1 插入数据

`insert into test (id, name, age, sex) values (1, '张三', 18, '男');`

### 6.2 查询数据

`select * from test;`

### 6.3 更新数据

`update test set name='李四' where id=1;`

### 6.4 删除数据

`delete from test where id=1;`

## 7.mysql函数

### 7.1 字符串函数

#### concat字符串拼接

`select concat('hello', ' ', 'world');`
result : **hello world**

#### upper字符串转大写

`select upper('hello world');`
result : **HELLO WORLD**

#### lower字符串转小写

`select lower('HELLO WORLD');`
result : **hello world**

#### length字符串长度

`select length('hello world');`
result : **11**

#### substr字符串截取

`select substr('hello world', 1, 5);`
result : **hello**

#### lpad字符串填充

`select lpad('hello world', 10, '0');`
result : **0000hello**

#### rpad字符串填充

`select rpad('hello world', 10, '0');`
result : **hello world0**

### 7.2 数值函数

#### ceil向上取整

`select ceil(3.14);`
result : **4**

#### floor向下取整

`select floor(3.14);`
result : **3**

#### round四舍五入

`select round(3.14, 1);`
result : **3.1**

#### abs绝对值

`select abs(-3);`
result : **3**

#### rand随机数

`select rand();`
result : **0.324234**

#### mod取余数

`select mod(10, 3);`
result : **1**

### 7.3 日期函数

#### curdate获取当前日期

`select curdate();`
result : **2019-06-24**

#### curtime获取当前时间

`select curtime();`
result : **10:24:34**

#### now获取当前时间

`select now();`
result : **2019-06-24 10:24:34**

#### year获取年份

`select year('2019-06-24');`
result : **2019**

#### date_add日期加减

`select date_add('2019-06-24', interval 1 day);`
result : **2019-06-25**

#### datediff日期差

`select datediff('2019-06-25', '2019-06-24');`
result : **1**

### 7.4 流程控制函数

#### if判断

`select if(1=1, 'true', 'false');`
result : **true**

#### case判断

`select case when 1=1 then 'true' when 2=2 then 'false' else 'error' end;`
result : **true**
