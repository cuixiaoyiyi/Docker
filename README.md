# Docker
# Docker 是用来替代虚拟机在服务器做程序运行环境的工具(类似于虚拟机，但本质并不是虚拟机操作系统)

我在实验室使用docker主要是为了解决占用系统资源过高的问题。如CPU、MEM

Docker的介绍和安装请移步
https://www.docker.com/

服务器已经安装好docker，因此只需要部署自己的环境
```
docker pull hub.c.163.com/library/ubuntu:latest
```
可以使用以下命令查看已安装镜像
```
docker images 
```
查看正在运行的docker
```
docker ps 
```
docker 启动
```
docker run -m 50G --cpus=46 -it -v /:/HostServer c-ubuntu-01:latest  /bin/bash
docker run -m 50G --cpuset-cpus="0,1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,20,21,22,23,24,25,26,27,28,29,30,31,32,33,34,35,36,37,38,39" -it -v /:/HostServer c-ubuntu-01:latest  /bin/bash

// -m 50G 内存上限50G
// --cpus=46 CPU 核数上限
// -v /:/HostServer  将原目录挂载在docker目录下   /原目录:/docker目录
// docker与宿主机内共享文件夹
// c-ubuntu-01:latest docker名称:版本号
```
docker 之内类似于Linux，需要自己安装。 <br />
若与宿主机共享文件夹，可以与宿主机配置类似的环境变量<br />

```
vim /etc/profile
JAVA_HOME = ''
PATH = :
```
想保存配置，可执行 docker commit id
```
退出后台运行 ctrl+q+p
退出不后台运行 exit
重新进入政正在运行的docker
docker attach id
```
