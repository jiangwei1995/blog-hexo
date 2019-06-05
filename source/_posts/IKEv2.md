---
title: Docker部署IKEv2协议VPN
---

## 快乐到起飞

### 下载镜像

``` bash
$ docker pull gaomd/ikev2-vpn-server
```

### 启动服务

``` bash
$ docker run -d --name ikev2-vpn-server --restart=always --privileged -p 500:500/udp -p 4500:4500/udp gaomd/ikev2-vpn-server
```

### 生成vpn配置文件“ikev2-vpn-iphone.mobileconfig”

``` bash
$ 1. docker run -i -t --rm --volumes-from ikev2-vpn-server -e "HOST=vpn.example.com" gaomd/ikev2-vpn-server generate-mobileconfig > ikev2-vpn-iphone.mobileconfig
```

注:替换HOST为自己的域名或IP地址

### 导入配置文件

``` bash
$ mac电脑直接打开一步一步安装就可以，苹果手机通过AirDrop传到手机上，安装即可
```