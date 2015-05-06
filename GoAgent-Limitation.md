
###GoAgent限制：  
+ Facebook 上传文件：图片/视频等  
  原因: Facebook上传文件，采用HTTP OPTIONS指令  
  不在GAE的支持范围  

+ Twitter上传大文件/图片  
  GoAgent 对上传超过64k的数据存在问题  
  GAE的限制是10M  
  因此有可能解决，还有待研究  

+ Pinterest 无法访问  
  原因：Pinierest 屏蔽了GAE的访问  

+ Youtube部分视频无法访问  
  是Youtube的限制  
  解决方案是采用其他方案，比如PHP_proxy  

+ http://www.eyny.com   
  无限重定向循环  
  原因怀疑是网站本身对GAE处理有问题  

+ xvideo  
 部分视频无法观看，怀疑是视频播放插件Flash中的代码，绕开了代理
  
+ vpngate的官方网站，安装包无法下载  
  GAE每次支持下载4M大小的数据，vpngate服务器不支持分段下载。  

+ 苹果日报的视频无法播放  
  http://hk.dv.nextmedia.com/actionnews/index/  
  视频文件可以下载，但网页上播放显示异常。  
  是由flash控制，内部配合问题，暂时没有找到根本原因。  

+ soundcloud 很多异常  
  大量使用了OPTIONS指令，GAE不支持