思路:
因为学校里面内网是互通的（看学校交换机分配范围），利用SS搭建代理服务器就可以了，
因为是搭建服务器来共享的 ，理论上来说同个内网的客户端都能用（包括校园WIFI，手机安装移动端SS即可）

优点：有线接入时延迟低，无线接入时利用学校WIFI能大范围分享

配置文件:config.json
``` 
	"server":"0.0.0.0",  
    "server_port":8023,  
    "local_address":"127.0.0.1",  
    "local_port":1080,  
    "password":"00001111",  
    "timeout":600,  
    "method":"aes-256-cfb",  
    "http_proxy": false,  
    "auth": false  

```
服务器地址填写::表示同时监听所有IPv4和所有IPv6地址
注意 method 加密类型

shadowsocks.bat为启动脚本
```
@echo off  
shadowsocks-libqss.exe -c config.json -S  

```

## 服务端
1.运行启动脚本即可，停止运行关闭命令行窗口即可

2.查询主机IP并记下来

## 客户端
1.在Shadowsocks里面填写之前设置的相关信息  

2.启动代理并设置代理模式  
	右下 SS右键 -启动系统代理
	系统代理模式 - 全局模式