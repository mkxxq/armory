## 简介
本项目用来存放xiaoqiang321个人的docker-compose配置文件

docker-compose是一个由docker官方提供的一个简易容器编排服务系统

docker-compose官方介绍[https://docs.docker.com/compose/overview/](https://docs.docker.com/compose/overview/)

## 基本设定
xxx/.data 是xxx的本地挂载地址,用来持久化数据

xxx/xxx.conf 是xxx的配置文件

## install docker
docker官方安装指南[https://docs.docker.com/compose/install/](https://docs.docker.com/compose/install/)
以下是apt系简单安装
```bash
sudo apt install docker.io
```

## install docker-compose
docker-compose是一个由docker官方提供的一个简易容器编排服务系统
docker-compose官方介绍[https://docs.docker.com/compose/overview/](https://docs.docker.com/compose/overview/)
docker-compose官方安装指南[https://docs.docker.com/compose/install/](https://docs.docker.com/compose/install/)

```bash
curl -L https://github.com/docker/compose/releases/download/1.14.0/docker-compose-`uname -s`-`uname -m` > /usr/local/bin/docker-compose
chmod +x /usr/local/bin/docker-compose
```

## start postgresql example


```bash
cd postgresql
mkdir .data
sudo docker-compose up
```