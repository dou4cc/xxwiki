### 说明如下：

![](https://cloud.githubusercontent.com/assets/17795455/13872209/b112be30-ed23-11e5-9d27-a5369c489daf.JPG)

* 本例中**“尚未建立连接”**为XX-net的运行状态，如显示**“XX-Net version(版本号)，一切正常，你可以访问真正的互联网了”**，即可访问GFW封锁的网址。

* **本地网络状态**<br>
————本机局域网连接状态，OK即表示连接无问题

* **IP数量**<br>
————XX扫描的能用IP总数，最高值3000

* **IP延迟**<br>
————IP延迟时间，单位ms

* **连接池**<br>
————数字均为零时不能翻墙，详见[“连接池帮助”](GoAgent Connection status)

* **浏览器代理设置**<br>
————浏览器是否监听到GAE代理端口，默认端口127.0.0.1：8087，监听到值为“OK”，否则为“Fail”

* **CA证书状态**<br>
————检测GAE证书是否安装到浏览器，检测到值为“OK”，否则为“Fail”，Fail时可手动[下载安装](http://127.0.0.1:8085/module/gae_proxy/control/download_cert)或重新运行XX－net下start.bat

* **扫描IP线程数**<br>
————XX后台扫描线程数，默认50线程，可根据具体情况[设置](http://127.0.0.1:8085/?module=gae_proxy&menu=advanced#scan_ip)

* **屏蔽状态**<br>
————与GAE服务器的联通状态，值为OK时可上网，Block倒计时需等待，详见[帮助](GoAgent-Blocked)

![](https://cloud.githubusercontent.com/assets/17795455/13872210/b14b4142-ed23-11e5-8a53-c147dd834883.jpg)

* **监听代理**<br>
————本机监听代理端口，默认端口127.0.0.1：8087，可修改为0.0.0.0:8087，作为其它设备的代理翻墙，配置方法详见[为其他设备提供代理服务](为其他设备提供代理服务)

* **PAC自动代理地址**<br>
————代理自动配置列表的位置

* **IPv6**<br>
————默认禁用，教育网等特殊情况使用。在[配置](http://127.0.0.1:8085/?module=gae_proxy&menu=config)页面中“高级选项”进行开关设置

* **当前工作AppID**<br>
————使用中的APPID，最好用自己申请的可以看youtube不限流量，且相对保证私密性，公共APPID只能浏览网页。

    拥有并使用自己的AppID步骤：1. [注册](how-to-create-my-appids)2. [部署](“部署服务端”页面)3. [配置](“Goagent配置”页面)

* **XX-Net Version**<br>
————XX版本号

* **Python Version**<br>
————Python版本号

* **System Platform**<br>
————系统平台

![](https://cloud.githubusercontent.com/assets/17795455/13872212/b18c770c-ed23-11e5-8605-a21dd6224180.jpg)

* **OS System**<br>
————操作系统类型

* **OS Version**<br>
————操作系统版本

* **OS Release**<br>
————操作系统发行版本

* **OS Detail**<br>
————操作系统详细说明

* **Language**<br>
————操作系统语言

* **Architecture**<br>
————系统架构

* **Browser**<br>
————浏览器版本

* **诊断信息**<br>
————主要信息，遇到问题可复制粘贴到[github](https://github.com/XX-net/XX-Net/issues)或[google](https://groups.google.com/forum/#!forum/xx-net)讨论组，让大家帮助解决

* **显示详细信息**<br>
————显示详细信息**(On)**
**（显示）**以上所有状态信息<br>
————显示详细信息**(Off)**
**（不显示）**以上所有状态信息