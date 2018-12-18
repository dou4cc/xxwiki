# 如何导入证书

说明：
======== 
GoAgent对https网站，是通过GAE服务获取到内容，再重新加密返回浏览器的。  
因此https的证书必须重新生成。 

浏览器需要导入GoAgent的证书，否则会遇到[[证书错误]]。 
- CA status: Fail 不一定是证书错误，可能是浏览器缓存问题。
- Chrome：Ctrl + F5 ；
    其他浏览器：[绕过浏览器缓存](https://zh.wikipedia.org/wiki/Help:%E7%BB%95%E8%BF%87%E6%B5%8F%E8%A7%88%E5%99%A8%E7%BC%93%E5%AD%98)

GoAgent证书的路径：  
 第一次启动后，会生成data\gae_proxy\CA.crt证书。  
 一般情况下，XX-Net会导入证书到浏览器中，如果浏览器已经启动，请试试重启浏览器。  

 某些情况下，导入失败（比如windows系统下的Firefox浏览器,比如linux没有安装nss3-tools），需要手动导入证书。  

PHP_proxy的证书是独立的，在data\php_proxy下，如果使用PHP，并提示证书问题，请同样导入PHP_proxy的证书。  

# windows手动导入证书
1. 如果自动导入存在问题，打开XX-Net文件夹，找到 data\gae_proxy 目录下的 "CA.crt" 证书，双击打开
2. 安装证书<br>
![打开后显示证书信息](http://image17.poco.cn/mypoco/myphoto/20150516/11/17431385420150516111506097.png)
3. 下一步<br>
![点击下一步](http://image17.poco.cn/mypoco/myphoto/20150516/11/17431385420150516111607063.png)
4. 选择 “将所有的证书放入下列存储” - 浏览<br>
![选择 “将所有的证书放入下列存储” - 浏览](http://image17.poco.cn/mypoco/myphoto/20150516/11/17431385420150516111634031.png)
5. 选择 “受信任的根证书发布机构”<br>
![选择 “受信任的根证书发布机构”](http://image17.poco.cn/mypoco/myphoto/20150516/11/1743138542015051611165202.png)
6. 点击确定，完成。你可能需要重启浏览器或操作系统。<br>
![完成](http://image17.poco.cn/mypoco/myphoto/20150516/11/17431385420150516111732088.png)

# ubuntu手动导入证书
1. 如果自动导入存在问题，针对Chrome浏览器可以采用手动导入的方式。
2. 点击浏览器的“settings”选项
3. 选择“HTTP/SSL”选项下的“Manage Certificating”
4. 选择“Authorities”，点击“Import”，到XX-Net解压文件夹下，找到 GoAgent\Data\GoAgent 目录下的 "CA.crt" 证书，导入即可。

# Linux 导入 root 证书

```sh
sudo trust anchor --store /opt/XX-Net/data/gae_proxy/CA.crt
```

# Linux 手动处理用户级别证书

创建文件夹

    mkdir -p ~/.pki/nssdb

手动导入证书到数据库

    certutil -d sql:. -A -t "C,," -n "GoAgent XX-Net - GoAgent" -i "/pathto/CA.crt"

若失败,可尝试更改证书数据库密码,可改为空

    modutil -changepw "NSS Certificate DB" -dbdir ~/.pki/nssdb


查看证书:

    certutil -L -d sql:~/.pki/nssdb

若要删除证书:

    certutil -d sql:~/.pki/nssdb -D -n "GoAgent XX-Net - GoAgent"

# Android手动导入证书
1. 打开设置-系统安全-从SD卡安装凭据（证书）.
2. 依次进入 XX-Net/data/gae_proxy , 选择该目录下的 CA.crt , 输入任意名称 , 按确定即可. 
3. 若以上方法导入的证书无效，可下载 Root Certificate Manager ， 使用该软件将证书导入系统

# IPAD/IPHONE手动导入证书
说明：Ios移动端只能通过自带邮件程序打开邮件附件的CA.crt，才能安装证书。经验证浏览器登录邮箱无法打开附件的CA.crt。
1. 在其它设备（PC端）登录邮箱，将CA.crt以附件的方式发送到其它邮箱。CA.crt地址： XX-Net/data/gae_proxy/CA.crt。
2. 在IPAD/IPHONE “邮件”程序设置账号为第一步的邮箱账号， 等待自动同步邮件到本地。
3. 找到第一步发送的邮件，点击附件，自动提示安装，需要输入IPAD/IPHONE的密码，确认后即可安装成功。

# 在浏览器中手动导入的方式

Firefox（火狐）浏览器：详细图文指导参见[[使用Firefox浏览器#手动导入证书]]。

Chrome（谷歌）浏览器：详细图文指导参见[[使用Chrome浏览器#手动导入证书]]。

通用步骤：

1. 点击浏览器的菜单按钮（一般在右上角），找到浏览器的"首选项"或者“设置”
2. 找到"证书"或者“安全性”相关的设置（可能隐藏在“高级”选项卡中），点击"查看证书"，在证书管理器中选中"证书机构"，点击“导入”。
3. 在XX-Net文件夹下，找到 data\gae_proxy 目录下的 "CA.crt" 证书，导入即可。
4. 在弹出的窗口中，选择"信任使用此CA标识的网站"，确定。
5. 尝试访问[[https://www.google.com/]]或[[https://www.facebook.com/]]，检验证书是否导入成功。

# 亚全局
 在 Unix 和 GNU/Linux 中，大多 HTTP 应用程序均支持调用环境变量 http_proxy 和 https_proxy 进行代理。此外该环境变量的大小写其实并没有统一标准，有个别程序就只支持全大写的环境变量。所以为方便起见，直接在 ~/.bash_profile 或 ~/.zshenv 添加以下即可： 
   export http_proxy=http://127.0.0.1:8087/
   export https_proxy=$http_proxy
   export HTTP_PROXY=$http_proxy
   export HTTPS_PROXY=$HTTP_PROXY

 再执行以下命令，导入证书以archlinux为例：
```
 ln -s /opt/XX-Net/data/gae_proxy/CA.crt  /etc/ca-certificates/trust-source/anchors/GoAgent.crt
 trust extract-compat
```
 