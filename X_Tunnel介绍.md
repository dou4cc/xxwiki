#### 原理
使用GAE作为隧道，对应用提供socks5服务。  

#### 优点：
+ 不怕服务器ip被封
+ 完全的tcp代理，没有证书问题，支持非http协议

#### 匿名性
+ 两跳，第一跳是google，大部分情况下可与tor媲美
+ 通讯过程拆分、合并
  多个socks5通讯会合并到一起传输
  一个socks5通讯会分解到多个tcp传输，以提高大流量下的性能
  附带的安全效果：难以通过对单个连接的传输指纹分析通讯的内容

#### 数据传输过程
客户端的 socks5 请求，封装成 http 协议数据，通过 GAE 转发到 x_tunnel 服务器，然后 x_tunnel 服务器还原 socks5 协议，连接目标网站，然后再把目标网站数据封装成 http 协议数据，通过 GAE 传回客户端，再还原成 socks5 协议，返回给PC机，可以解决 SS 的直连模式造成的服务器IP被封问题。
（此处应有一结构图）
![](https://drive.google.com/file/d/0B_zCT0lTm5wFMTExU05TVC1hWkU/view?usp=sharing)