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

### 二 文件和目录操作

#### 1.创建目录

`mkdir /home/wc`
-p 创建多级目录

#### 2.删除文件或目录

`rm -rf /home/wc`
-r递归删除，-f强制删除 不加参数只能删除空目录

#### 3.复制文件或目录

`cp -rf /home/wc /home/wc2`
-r递归复制，-f强制复制

#### 4.移动文件或目录（可以改名）

`mv -rf /home/wc /home/wc2`
-r递归移动，-f强制移动

#### 5.修改文件或目录权限

`chmod o+w /home/wc/1.txt`
o表示其他用户(other)，+w表示可写 可以让别人也可以修改1.txt文件

`chmod a-w /home/wc/1.txt`
a表示所有用户(all)，-w表示不可写 可以让所有人不可修改1.txt文件

u表示当前用户，g表示组  
+r表示可读  
-r表示不可读  
+x表示可执行  
-x表示不可执行

#### 6.其它命令

##### echo命令
将内容输出到控制台  
`echo hello world!`
将内容输出到文件  
`echo hello world! > /home/wc/1.txt`
将内容追加到文件  
`echo hello world! >> /home/wc/1.txt`
将文件内容输出到控制台  

##### cat命令

`cat /home/wc/1.txt`
显示文件内容

##### head命令

`head -n 10 /home/wc/1.txt`
显示文件前10行内容  

#### tail命令

`tail -n 10 /home/wc/1.txt`
显示文件后10行内容  
`tail -f /home/wc/1.txt`
实时显示文件内容，当文件内容发生变化时，会实时显示  

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


### 八 其他实用指令

#### 1.日期命令

`date` 显示当前日期  
`date +%Y-%m-%d` 显示当前日期 以年-月-日格式显示  
`date "+%Y-%m-%d %H:%M:%S"` 显示当前日期和时间 以年-月-日 时:分:秒格式显示  
`date -s "2018-01-01 00:00:00"` 修改系统时间  

#### 2.查找指令

##### find命令

`find /home/wc -name "*.txt"`
/home/wc表示搜索的目录，-name表示搜索文件名，*.txt表示搜索txt文件  
`find /home/wc -size +100`
-size表示搜索文件大小，+100表示搜索大于100的文件  
`find ~ -size +20M`
+20M表示搜索大于20M的文件
`-atime 按放文件件 -ctime 按状态时间 -mtime 按修改时间 -type 按文件类型`


##### grep命令

在文件中搜索字符串
`grep "hello" /home/wc/1.txt`
/home/wc/1.txt表示搜索的文件，hello表示搜索的字符串
`grep wc /home/wc/1.txt`
/home/wc/1.txt表示搜索的文件，wc表示搜索的字符串
`-n 显示匹配行号`

#### 3.定时任务

##### 编辑计划文件

`crontab -e`
-e表示编辑计划文件

##### cron语法格式

`# m   h   dom   mon dow  command`  
`0-59 0-23 1-31 1-12 0-7  command`  
| 符号    | 含义                   | 取值范围 |
| ------- | ---------------------- | -------- |
| m       | 表示分钟               | 0-59     |
| h       | 表示小时               | 0-23     |
| dom     | day of month，表示日期 | 1-31     |
| mon     | month，表示月份        | 1-12     |
| dow     | day of week，表示星期  | 0-7      |
| command | 待执行的命令           | -        |

\* 代表所有值  
\/ 代表“每”  
\- 代表范围  
\, 分割数字  
 
##### 示例

指定具体执行时间  
`2   *  *  *  * ls` #每个小时的第 2 分钟执行一次 ls 命令  
`30  7  *  *  * ls` #每天 7：30 执行一次 ls 命令  
`30 20  *  *  2 ls` #每周二，20：30执行一次 ls 命令（0 和 7 表示星期天）  

指定间隔时间  
`*/2 *  *  *  * ls` #每隔 2 分钟执行一次 ls 命令  

指定时间段  
`30 7 3-6 *  * ls` #每个月的 3，4，5，6 号的 7：30 分各执行一次 ls 命令  

指定多个时间  
`30 7 3,6 *  * ls` #每月的 3 号和 6 号的 7：30 分各执行一次 ls 命令  

