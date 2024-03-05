# docker学习

## ubuntu安装docker

1. 卸载自带的docker
```shell
apt remove docker docker-engine docker.io containerd runc
```

2. 更新Ubuntu软件包列表和已安装软件的版本
```shell
sudo apt update
```

3. 安装docker依赖
```shell
apt install ca-certificates curl gnupg lsb-release
```

4. 添加Docker官方GPG密钥
```shell
curl -fsSL http://mirrors.aliyun.com/docker-ce/linux/ubuntu/gpg | sudo apt-key add -
```

5. 添加Docker的软件源
```shell
sudo add-apt-repository "deb [arch=amd64] http://mirrors.aliyun.com/docker-ce/linux/ubuntu $(lsb_release -cs) stable"
```

6. 安装Docker
```shell
apt install docker-ce docker-ce-cli containerd.io
```

7. 配置用户组
默认情况下，只有root用户和docker组的用户才能运行Docker命令。我们可以将当前用户添加到docker组，以避免每次使用Docker时都需要使用sudo。命令如下：
```shell
sudo usermod -aG docker $USER
```

8. 运行Docker
```shell
systemctl start docker
```
![1709125975857](image/docker/1709125975857.png)

9. 安装工具
```shell
apt -y install apt-transport-https ca-certificates curl software-properties-common
```

10. 重启Docker
```shell
systemctl restart docker
```

11. 验证是否成功
```shell
sudo docker run hello-world
```
![1709126139214](image/docker/1709126139214.png)

12. 查看docker版本
```shell
sudo docker version
```
![1709126231551](image/docker/1709126231551.png)


## docker操作

1. 查看镜像
```shell
sudo docker images
```

2. 拉取镜像
```shell
# 搜索是否存在nginx的镜像
sudo docker search nginx
# 拉取nginx镜像
sudo docker pull 
```
![1709132157113](image/docker/1709132157113.png)

3. 运行容器
```shell
# 运行容器
sudo docker run -d -p 81:80 nginx
# 运行并进入容器
sudo docker run -d -p 81:80 -it nginx bash
# -d 参数让容器在后台运行
# --rm 容器执行结束后自动从历史记录中删除这容器
# -p 参数让容器的80端口映射到主机的81端口  -p 宿主机端口：容器暴露端口
```

4. 查看运行中的容器
```shell
sudo docker ps
```

5. 停止容器
```shell
sudo docker stop 容器ID
```

6. 进入一个运行着的容器
```shell
sudo docker exec -it 容器ID bash
```
![1709212513477](image/docker/1709212513477.png)

7. 删除镜像
```shell
sudo docker rmi 镜像ID
```

删除镜像之前，不能有依赖的容器记录，需要先删除容器记录可以先用`docker ps -a`查询容器记录

![1709303539941](image/docker/1709303539941.png)

8. 删除容器记录
```shell
sudo docker rm 容器ID
```
![1709303569941](image/docker/1709303569941.png)

9. 导出镜像
```shell
docker image save hello-world > /opt/hello-world.tar
```

10. 导入镜像
```shell
docker image load -i /opt/hello-world.tar
```

11. 查看容器日志
```shell
sudo docker logs -f 容器ID
# -f 参数让容器日志实时输出
```
