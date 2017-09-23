写了个把XX-Net和Entware-Ng包含在一起的懒人脚本，教程如下。懒人脚本会自动修改路由器的XX-Net自动开机启动和其他配置。安装完成后，用户只需要直接开启配置页面按照XX-Net Wiki继续配置就可以了。请务必保证格式化Jffs和U盘为ext2/3/4否则，不能保证脚本顺利运行。

1. 准备一个U盘，容量至少64M。如果有工具可以在PC上先格式化成Ext3或者Ext2的文件系统，清空U盘。插入到R6300V2的任一个USB口当中，如果你还在拿路由器上当NAS的话，最好别插在USB3.0的接口上。插入之后，路由器的系统应该会自动 Mount这个U盘。
2. 到路由器的高级系统设置里面打开”Enable JFFS Partition”, “Enable JFFS custom scripts and configs” 和 “Enable SSH”,应用设置之后重启。
3. 重启完成之后Telenet或者putty连接到R6300V2。先输入mount命令，检查一下U盘Mount的情况。如果U盘已经格式化为ext3或者ext2，那么直接跳过这一步：如果U盘显示为非ext3和ext2，先输入umount /dev/sda1或者sdb1（看系统把你的U盘分配到哪个上面）再输入mkfs.ext3 /dev/sda1或者sdb1，然后请等待命令执行完，可能时间比较长。最后mount /dev/sda1 /mnt/sda1
4.下载XX-Net+Entware-NG二合一安装脚本 [Intstall_xxnet](https://drive.google.com/open?id=0B1SYsraWbW-rRDYzMGdGaFNpVXM) （建议手动修改[软件包下载地址](https://gist.github.com/onplus/d4983ad5ad63596f7784d55ca7addc9f#file-install_xxnet-sh-L304)为[稳定版或测试版](https://github.com/XX-net/XX-Net/blob/master/code/default/update_version.txt)，）。然后用WINSCP上传到到路由器的/tmp/目录下
5. 输入命令
`sh /tmp/install_xxnet.sh`
如果正常会出现选择分区的画面，选择你希望安装的那个分区代号，然后回车。

在下载和安装完Entware-ng之后(时间会比较长，取决于网络速度，还有DNS的情况，建议安装的时候把DNS改为114.114.114.114，有遇到过运营商的DNS不能解析entware-ng下载地址的情况），会出现建议你生成交换分区的画面，如果内存太小，小于等于64M，建议做一个交换分区。可以选择1G 512M和256M。
脚本会自动下载最新的XX-Net并安装到U盘，脚本会自动生成manual.ini和开启远程配置页面。
在脚本执行完之后你可以访问http://路由器IP:8085 来进一步配置XX-Net。