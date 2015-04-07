##概述：

部署服务端时，需要跟appengine.google.com通讯，如果是直连，会被GFW检测到，影响部署过程。  
新版采用GAE代理，但是通过公共appid，有cookie泄漏的担忧。  

##解决方案：
+ 对大多数用户，系统默认使用GAE代理appengine.google.com，提高部署成功率
+ 对于隐私敏感用户，可以在配置中的高级选项，取消GAE代理appengine.google.com
