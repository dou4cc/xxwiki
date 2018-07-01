经过众多同仁的协助、测试，目前可以在 OpenWrt 和 LEDE 中顺利运行。现将教程说明如下。

2018.3.14

———————————————————————————————————

### 需要的条件：
1. 首先你需要公网 IP。如果没有公网ip，那么无法保证顺利运行。

2.安装必要的插件
通过 SSH 运行：

```
opkg update
opkg list-upgradable | awk -F ' - ' '{print $1}' | xargs opkg upgrade
opkg install python-pyopenssl
opkg install luci-i18n-upnp-zh-cn
```

### 具体步骤：
1. 下载 XX-Net。

2. 将 XX-Net 放到某个位置（下记 /XX-Net）


3. 修改 XX-Net 文件夹属性为 777。

4. 在 /etc/init.d 执行：

```
ln -s /XX-Net/xx_net.sh xx_net
```

并且启用服务，以后 XX-net 就会跟随 OpenWrt/LEDE 一同启动。


5. 修改 /XX-Net/data/launcher/config.yaml：

```
modules:{
launcher:{ allow_remote_connect:1 }
```

6. 重启。


7. 在浏览器中打开：

```
http://[OpenWrt_IP]:8085
```

8. 如果 XX-Net 未运行，可以通过 SSH 运行，输入命令：

```
/XX-Net/start
```

### 远程下载、导入证书
请见[这里](https://github.com/XX-net/XX-Net/wiki/GoAgent-Import-CA)。
