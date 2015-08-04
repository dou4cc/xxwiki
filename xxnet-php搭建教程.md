# 本文以0fees举例说明xxnet php搭建方法
帐号注册  [http://0fees.us/signup.php](http://0fees.us/signup.php)

然后把xxnet/php_proxy/server目录下的所有文件（共4个）传到网站根目录

最后启用xxnet php代理模式，然后修改xxnet/php_proxy/local目录下的proxy.ini

(web界面有bug，修改后。还需要改一下xxnet/data/php_proxy目录下的config.ini中enable，改成1.所以还是直接改proxy.ini)

然后重启xxnet搞定

# 图文教程
## 免费空间获取

本文以0fees为例，讲解xxnet php 搭建全过程

## 空间部署php服务端

帐号注册 [http://0fees.us/signup.php](http://0fees.us/signup.php)

* * *

[![xxnetphp](http://wallfans.eu.org/wp-content/uploads/2015/08/xxnetphp.png)](http://wallfans.eu.org/wp-content/uploads/2015/08/xxnetphp.png)

* * *

[![xxnetphp2](http://wallfans.eu.org/wp-content/uploads/2015/08/xxnetphp2.png)](http://wallfans.eu.org/wp-content/uploads/2015/08/xxnetphp2.png)

* * *

[![xxnetphp3](http://wallfans.eu.org/wp-content/uploads/2015/08/xxnetphp3.png)](http://wallfans.eu.org/wp-content/uploads/2015/08/xxnetphp3.png)

* * *

[![xxnetphp4](http://wallfans.eu.org/wp-content/uploads/2015/08/xxnetphp4.png)](http://wallfans.eu.org/wp-content/uploads/2015/08/xxnetphp4.png)

* * *

[![xxnetphp5](http://wallfans.eu.org/wp-content/uploads/2015/08/xxnetphp5.png)](http://wallfans.eu.org/wp-content/uploads/2015/08/xxnetphp5.png)

* * *

[![xxnetphp6](http://wallfans.eu.org/wp-content/uploads/2015/08/xxnetphp6.png)](http://wallfans.eu.org/wp-content/uploads/2015/08/xxnetphp6.png)

* * *

[![xxnetphp7](http://wallfans.eu.org/wp-content/uploads/2015/08/xxnetphp7.png)](http://wallfans.eu.org/wp-content/uploads/2015/08/xxnetphp7.png)

* * *

[![xxnetphp8](http://wallfans.eu.org/wp-content/uploads/2015/08/xxnetphp8.png)](http://wallfans.eu.org/wp-content/uploads/2015/08/xxnetphp8.png)

* * *

[![xxnetphp9](http://wallfans.eu.org/wp-content/uploads/2015/08/xxnetphp9.png)](http://wallfans.eu.org/wp-content/uploads/2015/08/xxnetphp9.png)

* * *

[![xxnetphp10](http://wallfans.eu.org/wp-content/uploads/2015/08/xxnetphp10.png)](http://wallfans.eu.org/wp-content/uploads/2015/08/xxnetphp10.png)

* * *

<span style="color: #ff0000;">此处有问题，改密码的文件为index.php</span>

[![xxnetphp11](http://wallfans.eu.org/wp-content/uploads/2015/08/xxnetphp11.png)](http://wallfans.eu.org/wp-content/uploads/2015/08/xxnetphp11.png)

* * *

<span style="color: #ff0000;">此处有问题，改密码的文件为index.php</span>

[![xxnetphp12](http://wallfans.eu.org/wp-content/uploads/2015/08/xxnetphp12.png)](http://wallfans.eu.org/wp-content/uploads/2015/08/xxnetphp12.png)

<span style="color: #ff0000;">此处有问题，改密码的文件为index.php</span>

* * *

[![xxnetphp13](http://wallfans.eu.org/wp-content/uploads/2015/08/xxnetphp13.png)](http://wallfans.eu.org/wp-content/uploads/2015/08/xxnetphp13.png)

* * *

[![xxnetphp14](http://wallfans.eu.org/wp-content/uploads/2015/08/xxnetphp14.png)](http://wallfans.eu.org/wp-content/uploads/2015/08/xxnetphp14.png)

* * *

[![xxnetphp16](http://wallfans.eu.org/wp-content/uploads/2015/08/xxnetphp16.png)](http://wallfans.eu.org/wp-content/uploads/2015/08/xxnetphp16.png)

* * *
最后，火狐浏览器用户请手动导入 `XX-Net\php_proxy\local` 中的证书 `CA.crt` 到浏览器中。导入方法见 [goproxy/InstallGuide.md](https://github.com/phuslu/goproxy/blob/wiki/InstallGuide.md#%E4%B8%89%E8%BF%90%E8%A1%8C%E5%AE%A2%E6%88%B7%E7%AB%AF)

教程结束，现在8087（goagent模式、自动切换模式） 8088端口（pass模式）就都可以用了

# 补充说明
上传的四个文件中relay.php是做中继用的，可以上传到某个国内服务器。让国内服务器跟国外服务器通信，再转发到本地。
这里我就不多说了，找个国外免费的就够费劲了。。。。。。
还有，我文章的0fees不支持看youtube，你们权当练手了

* * *
附：其他云计算平台的 PHP 部署
===================

OpenShift & Heroku
----------------------------

特点：能看 YouTube 视频，移动等宽带用户能满速

### 部署过程

[将 GoProxy 的 php fetchserver 部署在云平台上并用其翻墙](https://github.com/phuslu/goproxy/issues/64)

### 在客户端使用

同 [图文教程](#图文教程)