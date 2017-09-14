#### 原理
HTTP隧道，实现socks5代理服务。  
目前以来cloudflare作为前端，不再依赖GAE。  

#### 优点：
+ 不怕服务器ip被封
+ 完全的tcp代理，没有证书问题，支持非http协议

#### 性能：
  多个socks5通讯会合并到一起传输，提高通讯的效率  
  一个socks5通讯会分解到多个tcp传输，以提高下载/上传的性能  
  短时的网络中断，不会影响tcp的传输，更高的稳定性  

#### 匿名性
+ 两跳
  第一跳是cloudflare，难以在一个点上追踪ip  
+ 通讯过程拆分、合并  
  到一个目标主机的通讯，会分解成多个ip的通讯  
  多条链路通讯，会混在多个链路中  
  因此难以通过对单个连接的传输指纹分析通讯的内容  
+ 外在特征
  没有类似Tor的通讯特征  
  和普通的上网类似  

#### 数据传输过程
客户端的 socks5 请求，封装成 http 协议数据，通过 cloudflare 转发到 x_tunnel 服务器，然后 x_tunnel 服务器还原 socks5 协议，连接目标网站，然后再把目标网站数据封装成 http 协议数据，通过 cloudflare 传回客户端，再还原成 socks5 协议，返回给PC机，可以解决 SS 的直连模式造成的服务器IP被封问题。

结构图如下：
![Xtunnel_GAE结构图](https://cloud.githubusercontent.com/assets/13867479/13545797/b4a18032-e2d2-11e5-8b30-a26e76d7dbce.JPG)