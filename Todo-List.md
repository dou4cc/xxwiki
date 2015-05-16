+ Windows 下托盘菜单状态  
 选择了不同代理模式（全局GoAgent/Pac模式/取消代理），  
 前面能够显示一个勾  
 难度：中

+ Mac 下的托盘图标，采用黑白模式  
 已经有网友提供黑白的logo:  
 https://github.com/XX-net/XX-Net/issues/420  
 难度：低

+ TLS 1.2  
 OpenSSL 库，升级到最新版，支持TLS 1.2  
 最新版pyopenssl 是平台无关的；但以来cryptograph库，是平台相关的。  
 需要收集cryptograph库：Windows/Linux/Mac  
 难度：中

+ 某些网站需要限定ip访问  
 某些网站发现客户端ip变更，会认为需要重新登录  
 比如：http://www.sis001.com/forum/index.php  
 可以通过建立白名单机制  
 难度：高  

+ Windows + Firefox自动导入证书  
  发现到Windows下有firefox，启动线程，下载NSS库，然后导入证书。  
  NSS库已经准备好：https://github.com/XX-net/nss/releases  
  压缩包大小约2M  
  导入后，提示firefox需要重启。  
  难度：中