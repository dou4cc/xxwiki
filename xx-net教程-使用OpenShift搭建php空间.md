# 前言
### 写在最前面
我当初想写这个教程是因为发现openshift搭的php空间速度不错, 但是现在却感觉不太稳定.所以想测试速度之后再用的朋友, 可以按照本页的步骤"三, 修改php空间配置", 直接进行测试, 再决定是否自己申请openshift.
### 联系我
要联系我请用telegram, 找 @PeterPan_ID     
安利一下telegram的xx-net群组 : https://telegram.me/xxnet    
教程所有可能用到的文件都在云盘了 : 链接：http://pan.baidu.com/s/1bnoEoEz 密码：4jm1    
因为发现0fees的php空间今天开始出现使用的时候一直Checking your browser.., 尝试写一个openshift的教程吧(请先自备梯子)     

# 一, openshift相关
### 1. 注册
官方首页：https://www.openshift.com/    
打开OpenShift官方网站，点击右上角“Sign Up”，注册一个新账号。    
![注册页面](http://php-teluoka.rhcloud.com/os-photo/001signup.png)     
然后会发送邮件给你的注册邮箱, 请到你的邮箱中激活空间     
![激活空间](http://php-teluoka.rhcloud.com/os-photo/002vify.png)     
### 2. 创建php空间
点击验证链接后, 点击I accept下一步, 点击 Create your first application now     
出来一堆的选择, 下拉 选择**WordPress4**, 这样子我们就不用自己搭建php服务器了.    
![填写域名](http://php-teluoka.rhcloud.com/os-photo/003account1.png)  
下拉到最下方, create application    
然后 . Continue to the application overview page., 一个应用就建好了    
安装WordPress    
![安装WordPress](http://php-teluoka.rhcloud.com/os-photo/013wpinstall.png)    
下拉到最下方选择 简体中文, 然后填写一些注册信息.     
![设置登录信息](http://php-teluoka.rhcloud.com/os-photo/012wp.png)    
接下来按照提示登录就好了, 事实上你成功地建立了自己的博客.   

# 二, 上传所需的文件
因为我也是第一次用openshift, 貌似在openshift上管理文件只能通过公钥和密钥的方式.    
### 1. 公钥密钥的生成(WinSCP, PuTTYGen)
在我的百度云下载并安装 winscp575setup.exe    
打开PuTTYGen如图    
![在WinSCP中打开PuTTYGen](http://php-teluoka.rhcloud.com/os-photo/004winscp.png)    
点击Generate并且不断地移动鼠标     
![生成公钥密钥](http://php-teluoka.rhcloud.com/os-photo/005gen.png)   
生成之后点击Save private key, 提示选是, 自己保存ppk在一个记得住的地方   
### 2. ftp连接到openshift的应用中
![打开添加openshift公钥](http://php-teluoka.rhcloud.com/os-photo/006addpub.png)   
![复制公钥到openshift中](http://php-teluoka.rhcloud.com/os-photo/007copy.png)   
create 然后点击左上角的applications返回, 再单击你的应用, 进入应用中    
点击右侧的Want to log in to your application?    
现在可以不管PuTTYGen了, 我们回到之前打开的WinSCP界面中, 将应用中的ssh复制到WinSCP的主机名中, 如图    
![复制ssh到winscp中](http://php-teluoka.rhcloud.com/os-photo/008copy2.png)    
![打开高级页面](http://php-teluoka.rhcloud.com/os-photo/009winscp1.png)    
![添加保存的密钥文件](http://php-teluoka.rhcloud.com/os-photo/010winscp2.png)    
然后我们可以点击保存, 下次打开winscp可以直接连接到openshift中了. 点击登录, ftp链接到应用中, 有提示点击 是 就好了.登录后界面如图, 我记得会提示选择界面, 记得选择本地和远程的文件管理器同时打开的界面.     
![ftp界面](http://php-teluoka.rhcloud.com/os-photo/011login.png)     
### 3. 上传文件
进入到app-root/data/current, 这里就是WordPress项目的根目录了, 我们新建一个目录xxnet并进入其中, 上传一个hellowold.html测试一下, 访问链接 : http://php-mytlktest.rhcloud.com/xxnet/helloworld.html (改成你自己的应用域名)    
![创建目录](http://php-teluoka.rhcloud.com/os-photo/014cflod.png)     
![访问成功](http://php-teluoka.rhcloud.com/os-photo/015done.png)    
然后我们就可以上传xx-net的相关php空间文件了    
![上传1](http://php-teluoka.rhcloud.com/os-photo/016upload.png)    
![上传2](http://php-teluoka.rhcloud.com/os-photo/017up2.png)    

# 三, 修改php空间配置
(20150826更新, 发现修改本地文件如果更新xxnet的话会导致设置被覆盖, 所以还是用web页面配置吧)     
**不必退出**你的xx-net应用, 直接在xxnet的配置页面开启php模块, 如下           
![启动xx-net的php代理模块](http://php-teluoka.rhcloud.com/os-photo/020xxnet.png)    
然后, 在配置处填写你自己的php空间路径以及密码, 把我写教程的空间给你们用哈      
https://php-mytlktest.rhcloud.com/xxnet/index.php 123456 如下 
![配置页面](http://php-teluoka.rhcloud.com/os-photo/022php-ini.png)       
然后点击日志也可以看到这个样子      
![日志](http://php-teluoka.rhcloud.com/os-photo/021phpproxy.png)      

# 四, 测试是否可用
测试结果发现不太稳定, 有时候可用有时候不可用, 暂时不清楚原因.
另外, 默认的代理端口是127.0.0.1:8088, 建议配合SwitchyOmega使用哈!

# 五, 感谢(教程参考处)
http://www.freehao123.com/openshift-wp-dz/     
https://github.com/XX-net/XX-Net/wiki/xxnet-php搭建教程    