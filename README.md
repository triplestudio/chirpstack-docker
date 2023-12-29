## 三个步骤，快速在 Linux 上部署 ChirpStack

* 各组件默认版本为：NS v3.10, AS v3.15, Bridge v3.10

### 1、端口配置
配置防火墙，开放以下端口
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
* 中国 CN470  
* 欧洲 EU868
* 美国 US915
  
以使用 CN470 为例启用，通过继续执行以下命令进行启动。
```
cd cn470
sudo docker-compose up -d
```

### 3、配置与管理

**配置 ChirpStack**：https://blog.csdn.net/jiangjunjie_2005/article/details/96169551

注意：通过 docker-compose 方式安装， Network-servers 默认请配置为 `chirpstack-network-server:8000`（不是 localhost:8000）：
```
chirpstack-network-server:8000
```

![image](https://github.com/triplestudio/chirpstack-docker/assets/31872313/03e9f86c-7462-4be0-9d1e-36ca3cbd9e1c)




