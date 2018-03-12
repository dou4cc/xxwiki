本文方法已经无效

由于当前ipv4地址已经失效

且openwrt和lede均不支持ipv6

故本文方法已经无法生效

如有人成功试验其他方法

敬请修改本帖

谢谢

2018.3.12

———————————————————————————————————

### 需要的条件:
安装python2.7运行环境和pyOpenSSL库。  
`opkg install python-pyopenssl`  

### 具体步骤：
拷贝XX-Net到OpenWrt  
登陆OpenWrt控制台  
启动XX-Net  
`cd XX-Net`   
`./start.sh`  
  
### 远程访问状态管理页面
**允许远程访问Web界面：**  
修改 XX-Net/data/launcher/config.yaml  
  `modules:{`  
  ` launcher:{ allow_remote_connect:1 }`  
  
**[允许GAE_proxy提供远程代理服务：](https://github.com/XX-net/XX-Net/wiki/%E4%B8%BA%E5%85%B6%E4%BB%96%E8%AE%BE%E5%A4%87%E6%8F%90%E4%BE%9B%E4%BB%A3%E7%90%86%E6%9C%8D%E5%8A%A1)**  
  修改 XX-Net/data/gae_proxy/manual.ini    
```
[listen]
ip = 0.0.0.0

[pac]
ip = 0.0.0.0
```

**允许远程访问X-Tunnel 代理：**  
修改 data/x_tunnel/client.json  
```
{ "socks_host" : "0.0.0.0", "socks_port" : 1080 }  
```

重启XX-Net  
  
**浏览器中打开**
```http://OpenWrt_ip:8085```  

### 远程下载、导入证书  
  在状态页中，有证书下载链接  



