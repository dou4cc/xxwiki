### 路径：
`data/x_tunnel/client.json`


### 内容：
```
{
  "socks_host" : "127.0.0.1",
  "socks_port" : 1080,
  "server_host": "1234.xx-net.net",
  "server_port": 443,
  "login_account": "xxnet@github.org",
  "login_password": "MTIzNDU2Nzg5MA"
}
```

### 说明：
***socks_host***  
  绑定监听的ip，改为0.0.0.0 可向其他设备提供代理

***socks_port***  
  绑定监听的端口，修改端口号可避免端口冲突（SOCKS5代理常用端口1080）

***server_host***
  X-Tunnel服务器