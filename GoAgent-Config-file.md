### GoAgent配置说明：
+ 一般用户使用WebUI配置即可，不必修改配置文件  
+ WebUI的配置，保存到 `data/gae_proxy/config.ini`
+ `gae_proxy/local/proxy.ini` 会在升级时被覆盖，请不用修改  
+ 高级用户想修改某个参数，可以生成 `data/gae_proxy/manual.ini` 在里面放对应的配置   
  例如：将监听IP改为`0.0.0.0`，则在`manual.ini`中写下:   
```ini
   [listen]   
   ip = 0.0.0.0   
   port = 8087   
```

### 配置文件格式说明：  

```ini
[listen]  
ip = 127.0.0.1   <- GoAgent代理服务的监听绑定ip  
port = 8087      <- 代理绑定端口  

[gae]  
public_appid =  <-公共appid    
appid =         <-私人appid，可在web页面中部署，参见[[创建自己的appid|how to create my appids]]   
password =  
  
  
[hosts]  
; 目前支持模式：gae, fwd, direct  
; gae 即通过Goggle App Engine 进行转发，最稳定，但不支持OPTIONS等高级指令。  
; direct 即建立tcp链接后，交给浏览器自己握手通讯，不替换证书，容易被GFW检测到。  
; fwd 替换证书，修改连接握手过程，相对比较隐蔽，支持OPTIONS等高级指令  
scholar.google.com = direct  
code.google.com = direct  
clients5.google.com = direct  
clients6.google.com = direct  
upload.docs.google.com = direct  
mail.google.com = direct  
.commondatastorage.googleapis.com = gae  
;.g.cn = direct  

  
[autorange]  
; 分片下载，在服务端发现超出最大大小后，自动分片下载；  
threads = 3            <- 默认下载线程数  
maxsize = 1572864      <- 分片下载大小  
waitsize = 524288      <- 首次读写量，一般不要修改  
bufsize = 8192         <- 后续读写量，一般不要修改  

[pac]  
; 自动代理  
enable = 1  
ip = 127.0.0.1  
port = 8086  
file = proxy.pac <-可以替换成个人的pac文件，将个人编写的pac文件（例如myproxy.pac）放到code\default\gae_proxy\local文件夹中，此行改为“file =myproxy.pac”      
gfwlist = https://raw.githubusercontent.com/gfwlist/gfwlist/master/gfwlist.txt  
;adblock = http://adblock-chinalist.googlecode.com/svn/trunk/adblock.txt  
; adblock 项目已经停止维护更新  
expired = 86400  

[proxy]  
; 前置代理：有些公司需要通过代理才能上网  
enable = 0  
type = HTTP   <- 支持 HTTP/SOCKS4/SOCKS5  
host = 127.0.0.1  
port = 8888  
user =  
passwd =  

[control]  
; http 控制端口，配合launcher Web界面用  
enable = 1  
ip = 127.0.0.1  
port = 8084  

[google_ip]  
; ip扫描、管理模块  
use_ipv6 = 0                      <- 是否启用ipv6  
max_check_ip_thread_num = 20      <- 扫描 ip 的线程数  
max_good_ip_num = 3000            <- 最大保留ip 数  
ip_connect_interval = 10          <- 单个ip连接的间隔，太小容易被发现，太大影响性能，要根据自己的网络状态调  

[connect_manager]  
; 连接管理器的参数  
https_max_connect_thread = 10     <- https模式的最大发起连接，太大容易被封锁  
https_connection_pool_min = 10    <- 保持的最少可用连接数。 建立连接是耗时的过程  
                                     保持足够多的连接，能够在需要时就有连接可用  
https_connection_pool_max = 50    <- 最大链接池，超过部分不再维护  
https_keep_alive = 1              <- 是否保持链接  
forward_max_connect_thread = 10   <- fwd 模式的最大发起连接  

[love]  
; 保留GoAgent 的爱心广告  
enable = 0  
tip = \u8bf7\u5173\u6ce8\u5317\u4eac\u5931\u5b66\u513f\u7ae5~~  
```

External link: [为其他设备提供代理服务](https://github.com/XX-net/XX-Net/wiki/%E4%B8%BA%E5%85%B6%E4%BB%96%E8%AE%BE%E5%A4%87%E6%8F%90%E4%BE%9B%E4%BB%A3%E7%90%86%E6%9C%8D%E5%8A%A1)