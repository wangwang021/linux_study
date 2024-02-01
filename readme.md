# 学习linux的记录

## 命令

### 一 显示文件和文件夹

#### 1.普通显示  

`ls /home/wc`

#### 2.详细模式查看

`ls -l /home/wc`

#### 3.显示当前目录

`pwd`

#### 4.切换目录

`cd /home/wc`

### 二 目录操作

#### 1.创建目录

`mkdir /home/wc`
> -p 创建多级目录

#### 2.删除目录

`rm -rf /home/wc`
> -r递归删除，-f强制删除 不加参数只能删除空目录

#### 3.复制目录

`cp -rf /home/wc /home/wc2`
> -r递归复制，-f强制复制

#### 4.移动目录

`mv -rf /home/wc /home/wc2`
> -r递归移动，-f强制移动

### 三 归档压缩

#### 1.创建归档包

`tar -cvf example.tar example`
> -c创建，-v显示过程，-f指定归档包名
example 可以是文件夹或者文件 也可以是多个文件 以空格分开

#### 2.解开归档包

`tar -xvf example.tar`
> -x解压缩，-v显示过程，-f指定归档包名

`tar -xvf example.tar -C /home/wc`
> -C指定解压缩目录

#### 3.创建压缩包

`tar -czvf example.tar.gz example`
> -c创建，-z压缩，-v显示过程，-f指定归档包名

#### 4.解压缩压缩包

`tar -xzvf example.tar.gz -C /home/wc`
> -x解压缩，-z解压缩，-v显示过程，-f指定归档包名，-C指定解压缩目录

### 四 软链接

#### 1.创建软链接

`ln -s /home/wc /home/wc2`
> -s表示软链接 软链接就是文件的快捷方式

### 五 用户管理

#### 1.创建用户

`sudo useradd -m wc1`
> -m表示在/home下创建用户目录

#### 2.修改用户密码

`sudo passwd wc1`

#### 3.删除用户

`sudo userdel wc1`

#### 4.给root用户设置密码

`sudo passwd root`

#### 5.切换到root用户

`su root`

