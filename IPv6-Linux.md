## 1.安装虚拟网卡miredo
`sudo apt-get install miredo`

## 2.查看网卡配置
`ifconfig` 

在结果中应该能看见一个叫 teredo 的虚拟网卡

## 3.启动miredo（重启后有可能需要手动启动）
`sudo miredo`

***
注：来源于这个帖子http://www.linuxidc.com/Linux/2013-03/80479.htm

其他linux系统也应该能安装这个包，操作差不多。自己查询一下就好了

Miredo已经正常开启了但是ipv6-test却超时，有可能是网卡的ipv6已经从路由器等地方获取了，只需禁用即可

打开 /etc/sysctl.conf 然后添加以下内容：
```# 禁用某一个指定接口的IPv6(例如：eth0, lo)
net.ipv6.conf.eth0.disable_ipv6 = 1```

在 /etc/sysctl.conf 使这些更改生效，运行以下命令：
```sudo sysctl -p /etc/sysctl.conf```