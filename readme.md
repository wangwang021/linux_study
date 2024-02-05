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
-p 创建多级目录

#### 2.删除目录

`rm -rf /home/wc`
-r递归删除，-f强制删除 不加参数只能删除空目录

#### 3.复制目录

`cp -rf /home/wc /home/wc2`
-r递归复制，-f强制复制

#### 4.移动目录

`mv -rf /home/wc /home/wc2`
-r递归移动，-f强制移动

#### 5.修改权限

`chmod o+w /home/wc/1.txt`
o表示其他用户(other)，+w表示可写 可以让别人也可以修改1.txt文件

`chomd a-w /home/wc/1.txt`
a表示所有用户(all)，-w表示不可写 可以让所有人不可修改1.txt文件

u表示当前用户，g表示组  
+r表示可读  
-r表示不可读  
+x表示可执行  
-x表示不可执行

### 三 归档压缩

#### 1.创建归档包

`tar -cvf example.tar example`
-c创建，-v显示过程，-f指定归档包名
example 可以是文件夹或者文件 也可以是多个文件 以空格分开

#### 2.解开归档包

`tar -xvf example.tar`
-x解压缩，-v显示过程，-f指定归档包名

`tar -xvf example.tar -C /home/wc`
-C指定解压缩目录

#### 3.创建压缩包

`tar -czvf example.tar.gz example`
-c创建，-z压缩，-v显示过程，-f指定归档包名

#### 4.解压缩压缩包

`tar -xzvf example.tar.gz -C /home/wc`
-x解压缩，-z解压缩，-v显示过程，-f指定归档包名，-C指定解压缩目录

### 四 软链接

#### 1.创建软链接

`ln -s /home/wc /home/wc2`
-s表示软链接 软链接就是文件的快捷方式

### 五 用户管理

#### 1.创建用户

`sudo useradd -m wc1`
-m表示在/home下创建用户目录

#### 2.修改用户密码

`sudo passwd wc1`

#### 3.删除用户

`sudo userdel wc1`

#### 4.给root用户设置密码

`sudo passwd root`

#### 5.切换到root用户

`su root`

### 六 环境变量

#### 1.定义一个变量

`NAME=value`
NAME表示变量名，value表示变量值，等号两边不要加空格

#### 2.使用一个变量

`${NAME}`
例如 echo ${NAME}

#### 3.环境变量

当前环境存在的变量，最常用的环境变量，如：PATH，JAVA_HOME，HOME等

定义环境变量  只能在当前终端窗口中存在，关闭则消失
`export NAME=value`  

显示环境变量  
`echo ${NAME}`  

查看所有环境变量  
`printenv`  

可以再终端中使用，也可以在脚本中使用  

#### 4.打开用户环境变量

用`ls ~ -la` 显示当前用户文件夹下面的所有文件 .开头的文件名为隐藏文件  
.profile 为用户环境变量文件  里面添加变量即不会消失  
如在文件里面添加 `export NAME=value` 
用户打开终端时，会自动运行.profile文件，即自动加载变量  

#### 5.系统环境变量

定义在`/etc/profile`文件中的变量，系统启动时自动加载变量  
官方建议在profile.d文件夹中创建一个脚本来添加自定义的环境变量  
系统登录时会自动读取profile.d中的所有脚本，加载环境变量  

#### 6.PATH环境变量

PATH环境变量表示当前用户可以使用的命令的路径  
`export PATH=$PATH:/home/wc`  
在/etc/profile文件中添加变量，表示当前用户可以使用wc下面的路径  
: 表示路径分隔符    
修改环境变量后，注销重新登陆才回生效  

### 七 进程管理

#### 1.查看进程

`ps -ef`  
-e表示显示所有进程，f表示显示详细信息  

`ps -ef | grep java`
grep表示过滤，java表示过滤条件，|表示管道，将前面的命令的输出作为后面命令的输入  

#### 2.实时查看进程

`top`
实时查看进程  

`top -p NNNN`
NNNN表示进程号，可以指定进程号，不指定默认查看当前用户所有进程  

#### 3.结束进程
`kill -9 NNNN`
NNNN表示进程号，可以指定进程号，不指定默认查看当前用户所有进程  

