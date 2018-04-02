配置后，只有X-Tunnel 模块运行正常。如何使用这个已经正常的模块呢？
有能用的请出来冒个泡。
😂
1、3.10.4版GAE与X-Tunnel运行正常，只有Smart-Router不正常（关闭后前二者正常代理）。
2、http://127.0.0.1:8085/?module=launcher&menu=config 通用——允许远程访问控制页——ON
3、https://github.com/XX-net/XX-Net/wiki/%E4%B8%BA%E5%85%B6%E4%BB%96%E8%AE%BE%E5%A4%87%E6%8F%90%E4%BE%9B%E4%BB%A3%E7%90%86%E6%9C%8D%E5%8A%A1 
安卓4.2.2联想手机，设置为静态地址，采用GAEPROXY需要先导入证书 http://PC-IP:8085/module/gae_proxy/control/download_cert
4、支持设置代理的APP：
A、Twidere for Twitter 8087/1080 代理正常，8086没网速？
B、Twitter 8087/1080 网速太小无法代理，8086没网速？
😂😂
https://github.com/XndroidDev/Xndroid 稳定版1.1.9 (XX 3.10.4)默认允许远程访问
安卓4.2.2联想手机：运行异常，执行3、
安卓4.4.2小米手机：运行正常，未启用X-Tunnel，结果显而易见：
A、Twidere for Twitter 8087 代理正常
B、Twitter 8087 网速太小无法代理