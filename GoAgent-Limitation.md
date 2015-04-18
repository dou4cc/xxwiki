
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