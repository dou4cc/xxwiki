https://en.wikipedia.org/wiki/Teredo_tunneling

以管理员身份运行 CMD/PowerShell

输入命令（XP需要先运行`netsh interface ipv6 install`）
```
netsh interface ipv6 set teredo enterpriseclient teredo.remlab.net 30 default
ping -6 [2001:470:1:18::125]
netsh int ipv6 show teredo state 
```

其中servername可以自行择优选择(https://en.wikipedia.org/wiki/Teredo_tunneling#Servers)

例： `netsh interface ipv6 set teredo servername=win10.ipv6.microsoft.com`

也可尝试[@chendaihang的小工具](https://github.com/XX-net/XX-Net/files/1584162/teredo.zip)

注：
1. 在win10专业版、win7旗舰版、xp家庭版测试通过
2. teredo方法只能为IP访问提供基本支持，若要直接域名访问IPv6网站还需其他设置
3. 耐心等待teredo建立链接，可多次执行ping命令