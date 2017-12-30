### GoAgent配置文件说明：

- 建议使用Notepad2或Notepad++等支持代码高亮的编辑器。

- 一般用户使用Web UI进行配置即可，不必手动修改配置文件。

- Web UI的配置，会自动保存在`data/gae_proxy/config.ini`（请勿手动修改）。

- 默认设置保存在`code/gae_proxy/local/proxy.ini`，在升级时会被覆盖，请不要修改。

- 高级用户想手动修改某个参数，可以创建`data/gae_proxy/manual.ini`，在里面添加对应的配置项。

  例如：将监听IP改为`0.0.0.0`，端口改为8087，则在`manual.ini`中增加：

```ini
    [listen]   
     ip = 0.0.0.0   
     port = 8087   
```

### 配置文件格式：

```ini
[listen]
ip = 127.0.0.1  ;<- 代理服务监听的IP
port = 8087     ;<- 代理服务监听的端口

[gae]
public_appid =  ;<- 公共AppID
appid =         ;<- 私人AppID，可在Web UI中部署，参见[[创建自己的appid|how to create my appids]]   
password =      ;<- AppID的密码
validate = 1    ;<- GAEProxy服务端开启https

[hosts]
; 目前支持模式：gae,fwd,direct
; gae 通过Goggle App Engine进行转发，最稳定，但不支持OPTIONS等高级指令。
; direct 建立TCP连接后，交给浏览器自己握手通讯，不替换证书，容易被GFW检测到。
; fwd 替换证书，修改连接握手过程，相对比较隐蔽，支持OPTIONS等高级指令。
scholar.google.com = direct
code.google.com = direct
clients5.google.com = direct
clients6.google.com = direct
upload.docs.google.com = direct
mail.google.com = direct
.commondatastorage.googleapis.com = gae
;.g.cn = direct

[br_sites]
; simple work arround:
; site return br encoding, will not send gzip in Accept-Encoding except browser support br.
webcache.googleusercontent.com = br

[autorange]
; 分片下载：在服务端发现超出最大大小后，自动分片下载。
threads = 3            ;<- 默认下载线程数  
maxsize = 1572864      ;<- 分片下载大小  
waitsize = 524288      ;<- 首次读写量，一般无需修改  
bufsize = 8192         ;<- 后续读写量，一般无需修改  

[pac]
; 自动代理
enable = 1
ip = 127.0.0.1
port = 8086
file = proxy.pac  ;<- 可替换为个人的pac文件：将个人的pac文件（例如myproxy.pac）放到code\default\gae_proxy\local文件夹下，此行改为“file = myproxy.pac”
gfwlist = https://raw.githubusercontent.com/gfwlist/gfwlist/master/gfwlist.txt
;adblock = http://adblock-chinalist.googlecode.com/svn/trunk/adblock.txt
;adblock 项目已经停止维护更新
expired = 86400

[proxy]
; 局域网代理/前置代理：一般无需设置，只有那些需要通过内部代理访问外网的用户才需要设置。
enable = 0            ;<- 是否启用
type = HTTP           ;<- 代理类型，支持 HTTP/SOCKS4/SOCKS5
host = 127.0.0.1      ;<- 代理服务器地址
port = 8888           ;<- 代理服务器端口
user =                ;<- 代理用户名
passwd =              ;<- 代理密码

[control]
; http控制，配合launcher Web UI使用。
enable = 1
ip = 127.0.0.1
port = 8084

[switch_rule]
; 若proxy_hosts_only非空，则仅代理这些hosts。
proxy_hosts_only =     

[google_ip]
; IP扫描、管理模块
ip_source = ip_range               ;<- IP源：可选ip_range,ip_pool（仅IPv4时有效）
use_ipv6 = auto                    ;<- 使用IPv6情况：可选auto,force_ipv4,force_ipv6
ipv6_scan_ratio = 50               ;<- 扫描IPv6的比例（仅use_ipv6 = auto时有效）
auto_adjust_scan_ip_thread_num = 1 ;<- 是否自动调整扫描线程数
max_scan_ip_thread_num = 10        ;<- 扫描IP的最大线程数
max_good_ip_num = 3000             ;<- 保留的最大IP数
max_links_per_ip = 1               ;<- 每个IP保留的最大连接数
ip_connect_interval = 5            ;<- 单个IP连接的间隔：太小容易被发现，太大影响性能，要根据自己的网络状态调整
record_ip_history = 0              ;<- 记录IP历史

[connect_manager]
; 连接管理器的参数
https_max_connect_thread = 10      ;<- https模式的最大连接数：太大容易被封锁
https_new_connect_num = 3          ;<- https模式的新连接数
https_connection_pool_min = 1      ;<- https模式的连接池最小连接数：建立连接需要耗时，保持足够多的连接，在需要时有连接可用；0表示不维护新ssl连接
https_connection_pool_max = 30     ;<- https模式的连接池最大连接数：超过最大值时，put ssl to worker.
keep_active_timeout = 600          ;<- 连接池保持连接超时
https_keep_alive = 5               ;<- 重复使用连接的时间间隔：丢弃或发送新请求使保活
connect_interval = 40              ;<- 单个IP连接的时间间隔
forward_max_connect_thread = 10    ;<- fwd模式的最大连接数

[system]
log_file = 0
do_profile = 0

[love]
; 保留GoAgent的爱心广告
enable = 0
tip = \u8bf7\u5173\u6ce8\u5317\u4eac\u5931\u5b66\u513f\u7ae5~~
```



补充：[为其他设备提供代理服务](https://github.com/XX-net/XX-Net/wiki/%E4%B8%BA%E5%85%B6%E4%BB%96%E8%AE%BE%E5%A4%87%E6%8F%90%E4%BE%9B%E4%BB%A3%E7%90%86%E6%9C%8D%E5%8A%A1)