## 1.安装虚拟网卡miredo
`sudo apt-get install miredo`

## 2.查看网卡配置
`ifconfig` 

在结果中应该能看见一个叫 teredo 的虚拟网卡

## 3.启动miredo （重启系统之后，需要重新开启miredo）
`sudo miredo`

***
注：来源于这个帖子http://www.linuxidc.com/Linux/2013-03/80479.htm

其他linux系统也应该能安装这个包，操作差不多。自己查询一下就好了