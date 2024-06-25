查看容器
docker container ls -a

终止容器
docker container stop

进入容器
docker exec -it 69d1 bash

-v文件目录挂载
docker run --name mynginx -p 8087:80 -v /E/docker/nginx:/usr/local/nginx  -d nginx

查看获取容器内网IP地址

docker inspect --format='{{.NetworkSettings.IPAddress}}' php


本地仓库镜像提交到远程仓库：
 
1. 修改镜像仓库 docker tag openresty-1.19.3.1 yuhang0385/openresty:v1.19.3.1
2. 上传镜像：docker push adoph/openresty:v1.19.3.1

容器与主机之间数据拷贝 : docker cp RS-MapReduce 30026605dcfe:/home/cloudera    
提交保存镜像：docker commit falcon myfalcon
创建bridge网络：docker network create testnet
运行容器连接到testnet网络: docker run -it --name <容器名> ---network <bridge> --network-alias <网络别名> <镜像名>
复制保存镜像：docker save myfalcon -o ./myfalcon.tar

启动多个端口映射：
docker run -p <host_port1>:<container_port1> -p <host_port2>:<container_port2>
es:
docker run --name falconnew -dit -p 8081:8081 -p 8082:8080 -p 3308:3306 -p 5050:5050 -p 5090:5090 -p 6030:6030 -p 6060:6060 myfalcon

新增网络：
docker network create --driver overlay serv-net

win10 Hyper-V创建虚拟机:cmd 管理员权限
docker-machine create -d hyperv --hyperv-virtual-switch "Primary Virtual Switch" worker1
docker-machine create -d hyperv --hyperv-virtual-switch "Primary Virtual Switch" docker

解决Windows下Docker启动Elasticsearch报max virtual memory areas vm.max_map_count [65530] is too low, increase to at least [262144]的报错
先打开 powershell或者cmd
执行：
wsl -d docker-desktop
sysctl -w vm.max_map_count=262144