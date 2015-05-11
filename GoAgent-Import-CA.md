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