## 三个步骤，快速在Ubuntu上部署LoRaWAN 应用 ChirpStack，即 loraserver

* 各组件默认版本为：NS v3.10, AS v3.15, Bridge v3.10

### 1、申请 Ubuntu 云服务器
- 通过腾讯云的活动页面，可以快速的以几十元获取一台不错的轻量级应用服务器一年。
https://curl.qcloud.com/Rxe8zPNx
申请时，操作系统可以选择 Ubuntu 20 系统

- 购买完成后，在控制台配置防火墙，开放以下端口
TCP 端口：8080, 1883
UDP 端口：1700

### 2、安装部署与启动 

登录所申请的服务器，按序执行以下命令即可完成应该安装与部署。
#### Ubuntu
```
sudo apt-get update
sudo apt install docker-compose
wget https://github.com/triplestudio/chirpstack-docker/archive/refs/heads/master.zip && unzip master.zip
cd chirpstack-docker-master
```
#### CentOS
```
sudo yum update
sudo yum install docker-compose
wget https://github.com/triplestudio/chirpstack-docker/archive/refs/heads/master.zip && unzip master.zip
cd chirpstack-docker-master
```
启动应用，不同的 LoRaWAN 区域频段对应相应名称的子目录，区域频段定义形如下：
* AS923  
* EU868
* US915
以使用 AS923 为例启用，通过继续执行以下命令进行启动。
```
cd as923
sudo docker-compose up -d
```

### 3、运行及日志查看

浏览器打开 http://服务器IP:8080 
默认登录账号 admin
默认登录密码 admin

添加 Network-servers
`chirpstack-network-server:8000`

查看日志使用以下命令
```
sudo docker-compose logs
```

注意：默认的配置文件适合快速测试，生产环境，则可能需要修改。

### 其它

**操作实践视频**：https://mp.weixin.qq.com/s/A0TjrIVbBWAC2CB2BMD4Sg

**LoRa Server 配置与管理**：https://blog.csdn.net/jiangjunjie_2005/article/details/96169551

**频段定义**：https://www.thethingsnetwork.org/docs/lorawan/frequency-plans/

**channels**
| Band         | Channels     |  
|--------------|-----------| 
| US915 | 8,9,10,11,12,13,14,15,65      |  
| EU868      | 0,1,2,3,4,5,6,7  | 
| AS923-AS2      | 0,1,2,3,4,5,6,7 | 
| AU915 | 8,9,10,11,12,13,14,15,65      |  
| KR920      | 0,1,2,3,4,5,6,7  | 
| IN865      | 0,1,2,3,4,5,6,7  | 

