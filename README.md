# 三个步骤，快速在Ubuntu上部署LoRaWAN 应用 ChirpStack，即 loraserver

* 各组件默认版本为：NS v3.10, AS v3.15, Bridge v3.10

## 1、申请 Ubuntu 云服务器
- 通过腾讯云的活动页面，可以快速的以几十元获取一台不错的轻量级应用服务器一年。
https://curl.qcloud.com/1N0nA7hr
申请时，操作系统可以选择 Ubuntu 20 系统

- 购买完成后，在控制台配置防火墙，开放以下端口
TCP 端口：8080, 1883
UDP 端口：1700

## 2、安装部署与启动 

登录所申请的服务器，按序执行以下命令即可完成应该安装与部署。
```
sudo apt-get update
sudo apt install docker-compose
git clone https://github.com/triplestudio/chirpstack-docker.git
cd chirpstack-docker
```
启动应用，不同的 LoRaWAN 区域频段对应相应名称的子目录，目前仅配置部分区域频段，区域频段定义如下：
* AS923  
* EU868
* US915
以使用 AS923 为例启用，通过继续执行以下命令进行启动。
```
cd as923
sudo docker-compose up -d
```

## 3、运行及日志查看

浏览器打开 http://服务器IP:8080 
默认登录账号 admin
默认登录密码 admin

添加 Network-servers
`chirpstack-network-server:8000`

查看日志使用以下命令
```
sudo docker-compose logs
```

