## 手动设置GoAgent配置文件   
  
###目前GoAgent配置文件有：  
+ 默认配置文件 gae_proxy/local/proxy.ini，随版本升级更新。（非专家请勿编辑此文件。需使用ANSI编码）  
+ web_ui生成的用户配置文件： data/gae_proxy/config.ini，UI配置后，会刷新  
  
为了方便手动设置更多高级参数，增加了一个手动配置文件：  
data/gae_proxy/manual.ini  
  这个文件默认不存在，需要手动创建。  
  格式和前面两个一样，采用ini格式。  
  在这里面的配置项，会叠加到前面的配置上生效。  
  
###例子：  
比如设置后端扫描google ip的线程数，默认是5.  
为了提高扫描的速度，用文本文件，编辑内容如下：  
==============分割线===============      
    [google_ip]  
    max_check_ip_thread_num = 5  
==============分割线===============   
保存为data/gae_proxy/manual.ini，重启GoAgent模块。  

配置文件的详细说明：
https://github.com/XX-net/XX-Net/wiki/GoAgent-Config-file