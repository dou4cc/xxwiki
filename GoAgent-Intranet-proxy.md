### GAEProxy(XXNet/GoAgent) 的局域网代理（前置代理）

普通家庭用户大部分情况下是不需要设置的，只在某些需要通过内部代理（公司、企业内网、校园网等）访问外网的用户需要配置。



**普通用户（家庭光纤/ADSL）**

* 上网路径：
> 浏览器 -> 目标服务器

* 翻墙路径：
> 浏览器 -> XXNet/GoAgent -> Google App Engine -> 目标服务器

结构图如下：

![](https://cloud.githubusercontent.com/assets/17795455/13734940/48ef4a3c-e9de-11e5-9f98-12b77bfe9c06.jpg)


**内网（需要设置局域网）用户**

* 上网路径：
> 浏览器 -> 局域网代理 -> 目标服务器

* 翻墙路径：
> 浏览器 -> XXNet/GoAgent -> 局域网代理 -> Google App Engine -> 目标服务器

结构图如下：

![](https://cloud.githubusercontent.com/assets/17795455/13734951/85a76298-e9de-11e5-9315-2d52b199d1e3.JPG)


**功能特性：**

* HTTP/SOCKS4/SOCKS5
* 帐号认证支持

**配置页面：**

[GAEProxy局域网代理](http://127.0.0.1:8085/?module=launcher&menu=config)
