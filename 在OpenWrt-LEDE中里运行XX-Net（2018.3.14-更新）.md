经过众多同仁的协助、测试，目前可以在 OpenWrt 和 LEDE 中顺利运行。现将教程说明如下。

2018.3.14

### 需要的条件：
1. 首先你需要公网 IP。如果没有公网 IP，那么无法保证顺利运行。建议使用 IPv6。

2. 安装必要的插件
通过 SSH 运行：

```
opkg update
opkg install python-pyopenssl
```

### 具体步骤：
1. 下载 XX-Net。

2. 将 XX-Net 放到某个位置（下记 /XX-Net）

3. 修改 XX-Net 文件夹属性为 777。

4. 在「系统-启动项-本地启动脚本」的「exit 0」前面添加如下命令：

```
nohup /XX-Net/start >/dev/null 2>&1 &
```
然后 opkg install coreutils-nohup，以后 XX-net 就会跟随 OpenWrt/LEDE 一同启动。

5. 修改 /XX-Net/data/launcher/config.yaml：

```
modules:{
launcher:{ allow_remote_connect:1 }
```

6. 重启。


7. 在浏览器中打开：

```
http://[路由器 IP]:8085
```

8. 如果 XX-Net 未运行，可以通过 SSH 运行，输入命令：

```
/XX-Net/start
```

### 远程下载、导入证书
证书可以通过如下地址下载：

```
http://[路由器 IP]:8085/module/gae_proxy/control/download_cert
```

安装请见[这里](https://github.com/XX-net/XX-Net/wiki/GoAgent-Import-CA)。
