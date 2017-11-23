扫描IP已调整至[[“高级”页面]]

### 说明如下：
扫描IP是指XX会在后台自动扫描，这是XX的核心，GAE之所以能翻墙就是利用扫描谷歌在全球的IP。刚部署并配置好的PC扫描半小时左右就可以翻墙，如不急可把PC开个三天三夜，会自动找到更多好IP，您就可以畅享自由的互联网了。默认扫描线程数是50，如觉得PC资源占用太大可适当将扫描线程数改小点选择“更新”就行。
* 设置：
![设置](https://cloud.githubusercontent.com/assets/17795455/14109189/764d700a-f5f3-11e5-938c-1258fe23c4df.jpg)
* **自动调整扫描线程数**<br>
————根据实际能使用的IP数量及延迟情况自动调整线程多少，详见[帮助](https://github.com/XX-net/XX-Net/wiki/GoAgent-Auto-adjust-scan-ip-thread-num)<br>**(On)（打开）**_软件自动调整<br>**(Off)（关闭）**根据下面设定的数字确定线程数，不改变

* **最大扫描线程数**<br>
————自动调整扫描线程数的上限，手动调整后要点击更新

* **IP段列表**<br>
————扫描IP的范围，详见[支持格式](https://github.com/XX-net/XX-Net/wiki/GoAgent-Scan-Ip-Range-Format)

* 日志：
![日志](https://cloud.githubusercontent.com/assets/17795455/14109190/7654ec36-f5f3-11e5-9a00-519fc0d00a2f.jpg)
————日志中显示的是关于获得IP的时间、IP地址、延迟、类型等信息