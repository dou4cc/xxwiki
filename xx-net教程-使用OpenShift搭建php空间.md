# 前言
要联系我请用telegram, 找@teluoka<br/>
安利一下telegram中文站 : http://telegram-china.org/index.html<br/>
教程所有可能用到的文件都在云盘了 : 链接：http://pan.baidu.com/s/1bnoEoEz 密码：4jm1 <br/>
因为发现0fees的php空间今天开始出现使用的时候一直Checking your browser.., 尝试写一个openshift的教程吧(请先自备梯子)<br/>

# 一, openshift相关
### 1. 注册
官方首页：https://www.openshift.com/<br/>
打开OpenShift官方网站，点击右上角“Sign Up”，注册一个新账号。<br/>
![注册页面](http://php-teluoka.rhcloud.com/os-photo/001signup.png)<br/>
然后会发送邮件给你的注册邮箱, 请到你的邮箱中激活空间.<br/>
![激活空间](http://php-teluoka.rhcloud.com/os-photo/002vify.png)\<br/>
### 2. 创建php空间
点击验证链接后, 点击I accept下一步, 点击 Create your first application now<br/>
出来一堆的选择, 下拉 选择**WordPress4**, 这样子我们就不用自己搭建php服务器了.<br/>
![填写域名](http://php-teluoka.rhcloud.com/os-photo/003account.png)<br/>
下拉到最下方, create application<br/>
然后 . Continue to the application overview page., 一个应用就建好了<br/>
安装WordPress<br/>
![安装WordPress](http://php-teluoka.rhcloud.com/os-photo/013wpinstall.png)\<br/>
下拉到最下方选择 简体中文, 然后填写一些注册信息. <br/>
![设置登录信息](http://php-teluoka.rhcloud.com/os-photo/012wp.png)\<br/>
接下来按照提示登录就好了, 事实上你成功地建立了自己的博客.<br/>

# 二, 上传所需的文件
因为我也是第一次用openshift, 貌似在openshift上管理文件只能通过公钥和密钥的方式.<br/>
### 1. 公钥密钥的生成(WinSCP, PuTTYGen)
在我的百度云下载并安装 winscp575setup.exe<br/>
打开PuTTYGen如图<br/>
![在WinSCP中打开PuTTYGen](http://php-teluoka.rhcloud.com/os-photo/004winscp.png)<br/>
点击Generate并且不断地移动鼠标<br/>
![生成公钥密钥](http://php-teluoka.rhcloud.com/os-photo/005gen.png)<br/>
生成之后点击Save private key, 提示选是, 自己保存ppk在一个记得住的地方<br/>
### 2. ftp连接到openshift的应用中
![打开添加openshift公钥](http://php-teluoka.rhcloud.com/os-photo/006addpub.png)<br/>
![复制公钥到openshift中](http://php-teluoka.rhcloud.com/os-photo/007copy.png)<br/>
create 然后点击左上角的applications返回, 再单击你的应用, 进入应用中<br/>
点击右侧的Want to log in to your application? <br/>
现在可以不管PuTTYGen了, 我们回到之前打开的WinSCP界面中, 将应用中的ssh复制到WinSCP的主机名中, 如图<br/>
![复制ssh到winscp中](http://php-teluoka.rhcloud.com/os-photo/008copy2.png)<br/>
![打开高级页面](http://php-teluoka.rhcloud.com/os-photo/009winscp1.png)<br/>
![添加保存的密钥文件](http://php-teluoka.rhcloud.com/os-photo/010winscp2.png)<br/>
然后我们可以点击保存, 下次打开winscp可以直接连接到openshift中了. 点击登录, ftp链接到应用中, 有提示点击 是 就好了.登录后界面如图, 我记得会提示选择界面, 记得选择本地和远程的文件管理器同时打开的界面.<br/>
![ftp界面](http://php-teluoka.rhcloud.com/os-photo/011login.png)<br/>
### 3. 上传文件
进入到app-root/data/current, 这里就是WordPress项目的根目录了, 我们新建一个目录xxnet并进入其中, 上传一个hellowold.html测试一下, 访问链接 : http://php-mytlktest.rhcloud.com/xxnet/helloworld.html (改成你自己的应用域名)<br/>
![创建目录](http://php-teluoka.rhcloud.com/os-photo/014cflod.png)<br/>
![访问成功](http://php-teluoka.rhcloud.com/os-photo/015done.png)<br/>
然后我们就可以上传xx-net的相关php空间文件了<br/>
![上传1](http://php-teluoka.rhcloud.com/os-photo/016upload.png)<br/>
![上传2](http://php-teluoka.rhcloud.com/os-photo/017up2.png)<br/>

# 三, 修改本地文件
先退出你的xx-net应用, 修改对应路径下的proxy.ini, 然后重启xx-net, 开启php, 如下<br/>
![proxy.ini的位置](http://php-teluoka.rhcloud.com/os-photo/018ini.png)<br/>
![修改](http://php-teluoka.rhcloud.com/os-photo/019ini2.png)<br/>
![启动xx-net的php代理模块](http://php-teluoka.rhcloud.com/os-photo/020xxnet.pngg)<br/>
![日志](http://php-teluoka.rhcloud.com/os-photo/021phpproxy.png)<br/>

# 四, 测试是否可用
测试结果发现不太稳定, 有时候可用有时候不可用, 暂时不清楚原因.

# 五, 感谢(教程参考处)
http://www.freehao123.com/openshift-wp-dz/