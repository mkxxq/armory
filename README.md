## 简介
本项目用来存放[xiaoqiang321](https://github.com/xiaoqiang321)个人的docker-compose配置文件

docker-compose是一个由docker官方提供的一个简易容器编排服务系统

docker-compose官方介绍[https://docs.docker.com/compose/overview/](https://docs.docker.com/compose/overview/)

## 基本设定
xxx/.data 是xxx的本地挂载地址,用来持久化数据

xxx/xxx.conf 是xxx的配置文件

## install docker
docker官方安装指南[https://docs.docker.com/compose/install/](https://docs.docker.com/compose/install/)

以下是脚本安装
```bash
# 获取安装脚本
$ curl -fsSL https://get.docker.com -o get-docker.sh
# 使用aliyun的源安装
$ sudo sh get-docker.sh --mirror Aliyun
```

## install docker-compose
docker-compose官方安装指南[https://docs.docker.com/compose/install/](https://docs.docker.com/compose/install/)

```bash
$ sudo curl -L "https://github.com/docker/compose/releases/download/1.25.4/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
$ chmod +x /usr/local/bin/docker-compose
```

## start postgresql example


```bash
cd postgresql
mkdir .data
sudo docker-compose up
```