GoAgent 连接状态
================

状态页面上的connected link，表示已建立的有效连接数。  
目前有两个数字，解释如下：  
+ google 服务器在建立ssl握手之后，允许保持240秒。  
+ 一个ssl一旦使用来访问某个host，就不能更换其他host  

因此建立了2个重要的连接池：  
+ 未用过的ssl连接池  
+ 通用的gae连接池  

规则如下：  
+ gae连接可以循环使用，只要使用过程没有出现异常。  
+ 未用过的连接池，可以在需要时，被gae连接使用，也可以被Direct模式使用，即Host为www.googleapi.com之类的网站。  

只要这两个连接池有可用连接，即可正常使用。