# 学习linux的记录

## 命令

### 一 显示文件和文件夹 

#### 1 普通显示  
`ls /home/wc`

#### 2 详细模式查看  
`ls -l /home/wc`

#### 3 显示当前目录
`pwd`

#### 4 切换目录
`cd /home/wc`

### 二 目录操作

#### 1 创建目录
`mkdir /home/wc`
> -p 创建多级目录

#### 2 删除目录

`rm -rf /home/wc`
> -r递归删除，-f强制删除 不加参数只能删除空目录

#### 3 复制目录
`cp -rf /home/wc /home/wc2`
> -r递归复制，-f强制复制

#### 4 移动目录
`mv -rf /home/wc /home/wc2`
> -r递归移动，-f强制移动

