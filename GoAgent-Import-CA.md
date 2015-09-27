#如何导入证书GoAgent 

说明：
======== 
GoAgent对https网站，是通过GAE服务获取到内容，再重新加密返回浏览器的。  
因此https的证书必须重新生成。 

浏览器需要导入GoAgent的证书，否则会提示红色叉叉。  

GoAgent证书的路径：  
 第一次启动后，会生成data/goagent/CA.crt证书。  
 一般情况下，XX-Net会导入证书到浏览器中，如果浏览器已经启动，请试试重启浏览器。  

 某些情况下，导入失败（比如windows+firefox,比如linux没有安装nss3-tools），需要手动导入证书。  
 请搜索对应浏览器如何导入证书。  

 （wiki待完善：各常见的浏览器导入证书的图文教程）  

PHP_proxy的证书是独立的，在data/php_proxy下，如果使用PHP，并提示证书问题，请同样导入PHP_proxy的证书。  

# windows手动导入证书
1. 如果自动导入存在问题，打开XX-Net文件夹，找到 GoAgent\Data\GoAgent 目录下的 "CA.crt" 证书，双击打开
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
3. 选择“HTTP/SSL”选项下的“Managene Certificating”
4. 选择“Authorities”，点击“Import”，到XX-Net解压文件夹下，找到 GoAgent\Data\GoAgent 目录下的 "CA.crt" 证书，导入即可。

Firefox浏览器手动导入的方式
1. 选择浏览器的"首选项"
2. 选择"高级"中的"证书"
3. 选择"查看证书"
4. 选择证书管理器中的"证书机构"
5. 点击"导入"，到XX-Net解压文件夹下，找到 GoAgent\Data\GoAgent 目录下的 "CA.crt" 证书，导入即可。
注意：导入时候会出现下载证书的选项需要选择"信任使用次CA标识的网站"
