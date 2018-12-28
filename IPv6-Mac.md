## 概述：
 Mac 下有3种方法获得IPv6


## teredo
下载安装miredo https://github.com/darconeous/miredo-osx    
最新版 miredo 1.2.6 下载地址 https://github.com/bit/miredo-osx/releases  
可以避免 Mac10.14 安装失败问题

下载安装tuntaposx： https://sourceforge.net/projects/tuntaposx/  

注： 很多反馈Mac10.13 安装不了，是系统保护，关闭就好了：   
`command+R`  
`csrutil disable`  
`reboot`  
重新安装  
 
相关讨论：   
https://github.com/XX-net/XX-Net/issues/8045  
https://github.com/XX-net/XX-Net/issues/8425  


## isatap
https://github.com/tuna/ipv6.tsinghua.edu.cn/blob/master/isatap.md#mac-os-x环境  
只适合教育网用户  

编写脚本 /usr/local/bin/thu6tunnel.sh，加入以下内容
```
#!/bin/sh 
#清除IPV6路由表 
route delete -inet6 default  
ifconfig gif0 destroy
EN0_IP=`ifconfig en0 | grep inet | grep -v inet6 | awk '{print $2}'` 
EN1_IP=`ifconfig en1 | grep inet | grep -v inet6 | awk '{print $2}'`  
if [ -n “$EN0_IP” ]; then 
    LOCAL_IP=$EN0_IP 
else 
    LOCAL_IP=$EN1_IP 
fi  
if [ -n "$LOCAL_IP" ]; then 
    ifconfig gif0 create
    ifconfig gif0 tunnel $LOCAL_IP 166.111.21.1 
    ipconfig set gif0 MANUAL-V6 2402:f000:1:1501:200:5efe:$LOCAL_IP 64
    route add -inet6 ::/0 -interface gif0
fi
```
设置权限

`sudo chmod +x /usr/local/bin/thu6tunnel.sh`

用root权限运行脚本

`sudo /usr/local/bin/thu6tunnel.sh`

或者，打开终端，单独输入以下命令:

IP4="我的IPv4地址"  # 这里不能有空格
```
sudo ifconfig gif0 create
sudo ifconfig gif0 tunnel $IP4 166.111.21.1
sudo ipconfig set gif0 MANUAL-V6 2402:f000:1:1501:200:5efe:$IP4 64
sudo route add -inet6 ::/0 -interface gif0
```

这样 ISATAP就配置好了！

注意，OS X 中 safari 对于 ISATAP 的 IPv6 接入不友好，仍然会打开 IPv4 地址。

 请通过`ping6 ipv6.tsinghua.edu.cn`验证接入。


## 6to4
https://support.apple.com/kb/PH25406?locale=zh_CN  
说明：需要外网IP地址，大部分用户不具备  

如果您需要连接到 IPv6 地址，但您的网络不提供 IPv6 连接，则可以设置 6to4 网络端口配置。

1. 选取苹果菜单 >“系统偏好设置”，然后点按“网络”。

1. 点按添加按钮 ，点按“接口”弹出式菜单，然后选取“6to4”。

1. 为该配置指定名称，然后点按“创建”。

1. 如果您获得了一个中转地址，点按“配置”弹出式菜单，选取“手动”，然后输入该地址。否则，保留设置为“自动”。
