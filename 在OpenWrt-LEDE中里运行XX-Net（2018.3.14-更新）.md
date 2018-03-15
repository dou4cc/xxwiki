经过众多同仁的协助

经过测试

目前可以在openwrt和lede中顺利运行

现将教程说明如下

2018.3.14

———————————————————————————————————

### 需要的条件:
1.首先你需要公网ip

如果没有公网ip

那么无法保证顺利运行

2.安装必要的插件
通过ssh运行
```
opkg update
opkg list-upgradable | awk -F ' - ' '{print $1}' | xargs opkg upgrade
opkg install python-pyopenssl
opkg install 6to4
opkg install luci-i18n-upnp-zh-cn
```

### 具体步骤：
1.下载XX-Net


2.通过ssh将xx-net到OpenWrt/lede的根目录下面  


3.修改xx-net文件夹属性为 八进制表0777


4.通过lede界面在网络-防火墙-自定义规则下面添加如下命令

```
ip6tables -t nat -A POSTROUTING -o [intf] -j MASQUERADE
iptables -I INPUT -p tcp --dport 8087 -j ACCEPT
iptables -I INPUT -p tcp --dport 8086 -j ACCEPT
iptables -I INPUT -p tcp --dport 8085 -j ACCEPT
```

【intf】是你lan口名字 

一般是eth0或者eth1或者eth0.2之类的


5.在系统-启动项 exit 0前面添加如下命令
```
sleep 10
nohup /usr/bin/python /XX-Net/code/default/launcher/start.py >/dev/null 2>&1 &
```
以后xx-net就会跟随OpenWrt/lede一同启动（待证实，本人未成功）


6.通过ssh修改XX-Net/data/launcher/config.yaml 
```
modules:{
launcher:{ allow_remote_connect:1 }
```


7.重启OpenWrt/lede


8.在浏览器中打开
```
http://OpenWrt_ip:8085
```  


9.如果xx-net未运行，可以通过ssh运行 ，输入命令
```
python /XX-Net/code/default/launcher/start.py
```


### 远程下载、导入证书  
在状态页中，有证书下载链接（如何安装待补充）



