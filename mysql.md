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

## 5. mysql表操作命令
### 5.1 查询数据库表名
`show tables;`

### 5.2 查询表结构
`desc test;`

### 5.3 创建表
`create table test (
    id int, name varchar(20) comment 'id',
    name varchar(20) comment '姓名',
    age int comment '年龄',
    sex varchar(10) comment '性别',
    );`

## 6. mysql数据操作命令

### 6.1 插入数据
`insert into test (id, name, age, sex) values (1, '张三', 18, '男');`

### 6.2 查询数据
`select * from test;`

### 6.3 更新数据
`update test set name='李四' where id=1;`

### 6.4 删除数据
`delete from test where id=1;`
