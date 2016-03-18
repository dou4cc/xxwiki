### 说明如下：

![](https://cloud.githubusercontent.com/assets/17795455/13872209/b112be30-ed23-11e5-9d27-a5369c489daf.JPG)
![](https://cloud.githubusercontent.com/assets/17795455/13872210/b14b4142-ed23-11e5-8a53-c147dd834883.jpg)
![](https://cloud.githubusercontent.com/assets/17795455/13872212/b18c770c-ed23-11e5-8605-a21dd6224180.jpg)


* 本例中**“尚未建立连接”**为XX-net的运行状态，如显示**“XX-Net version(版本号)，一切正常，你可以访问真正的互联网了”**，即可访问GFW封锁的网址。

* **本地网络状态**
————本机局域网连接状态，OK即表示连接无问题

* **IP数量**
————XX扫描的能用IP总数，最高值3000

* **IP延迟**
————IP延迟时间，单位ms

* **连接池**
————数字均为零时不能翻墙，详见[“连接池帮助”](GoAgent Connection status)

* **浏览器代理设置**
————浏览器是否监听到GAE代理端口，默认端口127.0.0.1：8087，监听到值为“OK”否则为“Fail”

* **CA证书状态**
————检测GAE证书是否安装到浏览器，检测到值为“OK”否则为“Fail”，Fail时可手动[下载安装](http://127.0.0.1:8085/module/gae_proxy/control/download_cert)或重新运行XX－net下start.bat

* **扫描IP线程数**
————XX后台扫描线程数，默认50线程，可根据具体情况[设置](http://127.0.0.1:8085/?module=gae_proxy&menu=advanced#scan_ip)

* **屏蔽状态**
————与GAE服务器的联通状态，值为OK时可上网，Block倒计时需等待，详见[帮助](GoAgent-Blocked)