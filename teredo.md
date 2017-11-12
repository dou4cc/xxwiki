https://zh.wikipedia.org/wiki/Teredo隧道

以管理员身份运行 CMD/PowerShell

输入命令（XP需要先运行`netsh interface ipv6 install`）
```
netsh interface ipv6 set teredo enterpriseclient servername=teredo.remlab.net 30 clientport=default
ping -6 [2001:470:1:18::125]
netsh int ipv6 show teredo state 
```

其中servername可以自行择优选择(https://zh.wikipedia.org/wiki/Teredo%E9%9A%A7%E9%81%93#.E6.9C.8D.E5.8A.A1.E5.99.A8)
1. `netsh interface ipv6 set teredo servername=teredo.remlab.net`
2. `netsh interface ipv6 set teredo servername=teredo.trex.fi`
3. `netsh interface ipv6 set teredo servername=win10.ipv6.microsoft.com`


注：
1. 在 win10专业版、win7旗舰版、xp家庭版测试通过
2. 本方法只能为 xx-net/ipv6-hosts 提供基本支持，若要直接域名访问IPV6网站还需其他设置