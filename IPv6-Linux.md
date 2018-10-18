## 1.安装虚拟网卡miredo
`sudo apt-get install miredo`

## 2.查看网卡配置
`ifconfig` 

在结果中应该能看见一个叫 teredo 的虚拟网卡

## 3.启动miredo（重启后有可能需要手动启动）
`sudo miredo`

注：来源于这个帖子http://www.linuxidc.com/Linux/2013-03/80479.htm

其他linux系统也应该能安装这个包，操作差不多。自己查询一下就好了

## 4.启动systemd miredo.service 服务，实现开机自动运行

这里有个小bug，具体请看这个帖子：
https://bugs.launchpad.net/ubuntu/+source/miredo/+bug/1482069

修改miredo.service

`sudo vim /lib/systemd/system/miredo.service`

修改成 After=**network-online**.target 并且保存

修改/etc/miredo.conf,配置你需要的服务器名称

最后
`sudo systemctl enable miredo.service && sudo systemctl start miredo`

启动服务，这样就可以开机网络连通后运行该服务了。

## deepin 系统问题解决：  
 https://github.com/XX-net/XX-Net/issues/10008