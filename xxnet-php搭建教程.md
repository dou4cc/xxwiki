# 本文以0fees举例说明xxnet php搭建方法
帐号注册  [http://0fees.us/signup.php](http://0fees.us/signup.php)
然后把xxnet/php_proxy/server目录下的所有文件（共4个）传到网站根目录
最后启用xxnet php代理模式，然后修改xxnet/php_proxy/local目录下的proxy.ini(web界面有bug，修改后。还需要改一下xxnet/data/php_proxy目录下的config.ini中enable，改成1.所以还是直接改proxy.ini)
然后重启xxnet搞定
# 图文教程
在这上图比较麻烦，直接看我的博客链接吧 [http://wallfans.eu.org/xxnet_for_php/](http://wallfans.eu.org/xxnet_for_php/)
# 补充说明
上传的四个文件中relay.php是做中继用的，可以上传到某个国内服务器。让国内服务器跟国外服务器通信，再转发到本地。
这里我就不多说了，找个国外免费的就够费劲了。。。。。。
还有，我文章的0fees不支持看youtube，你们权当练手了