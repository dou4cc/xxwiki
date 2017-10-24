### 1.开启本地路由器UPnP服务，如有光猫请设置成桥接使用自己的路由器拨号<br>
下图为IPv6成连接后的路由器显示<br>
![路由器UPnP](https://user-images.githubusercontent.com/31415872/31861133-0dc36056-b75a-11e7-8faf-af3ae5eff830.PNG)
### 2.恢复IPv6组策略默认设置<br>
开始——运行——输入“gpedit.msc”(引号里内容)<br>
参照下图依次打开：计算机配置——管理模板——网络——TCPIP设置——IPv6转换技术，如有已配置或禁用、启用等均修改为“未配置”
![IPv6组策略](https://user-images.githubusercontent.com/19790792/31531180-110454b2-b018-11e7-8d87-0bda5c0fc4f8.jpg)
### 3.恢复防火墙默认设置<br>
开始——控制面板——查看方式“大图标”——windows防火墙——还原默认设置
![防火墙设置](https://user-images.githubusercontent.com/19790792/31532888-71595d30-b022-11e7-83b5-c75e3452dbc0.jpg)
### 4.设置本地连接IPV4 和 IPV6 的DNS<br>
IPV4 DNS：（参考 [http://ip.cn/dns.html](http://ip.cn/dns.html) ）<br>
![IPv4设置](https://user-images.githubusercontent.com/19790792/31531466-ddbc34e2-b019-11e7-902f-b9c97b7ccb34.jpg) <br>
IPV6 DNS：<br>
![IPv6设置](https://user-images.githubusercontent.com/19790792/31531486-039ad5b0-b01a-11e7-84ff-8bf9da24fe89.jpg)
### 5.执行一键批处理开启 IPV6 操作<br>
* 请将下列命令保存成 IPV6_1.bat 文件并**以管理员权限**执行<br>
其中的**网络连接**请根据自己实际使用情况**修改**为您本机上述第三步配置DNS的网络连接，如**网络连接**或**网络连接2**、**网络连接3**……<br>

@echo off<br>

net start "ip helper"<br>
netsh int ipv6 reset<br>

netsh int teredo set state default<br>
netsh int 6to4 set state default<br>
netsh int isatap set state default<br>
netsh int teredo set state server=teredo.remlab.net<br>
netsh int ipv6 set teredo enterpriseclient<br>
netsh int ter set state enterpriseclient<br>
route DELETE ::/0<br>
netsh int ipv6 add route ::/0 "网络连接"<br>
netsh int ipv6 set prefix 2002::/16 30 1<br>
netsh int ipv6 set prefix 2001::/32 5 1<br>
Reg add HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\services\Dnscache\Parameters /v AddrConfigControl /t REG_DWORD /d 0 /f<br>

netsh int teredo set state default<br>
netsh int 6to4 set state default<br>
netsh int isatap set state default<br>
netsh int teredo set state server=teredo.remlab.net<br>
netsh int ipv6 set teredo enterpriseclient<br>
netsh int ter set state enterpriseclient<br>
route DELETE ::/0<br>
netsh int ipv6 add route ::/0 "网络连接"<br>
netsh int ipv6 set prefix 2002::/16 30 1<br>
netsh int ipv6 set prefix 2001::/32 5 1<br>
Reg add HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\services\Dnscache\Parameters /v AddrConfigControl /t REG_DWORD /d 0 /f<br>

ipconfig /all<br>
ipconfig /flushdns<br>
netsh int ipv6 show teredo<br>
netsh int ipv6 show route<br>
netsh int ipv6 show int<br>
netsh int ipv6 show prefix<br>
netsh int ipv6 show address<br>
route print<br>
cmd<br>

* 请将下列命令保存成 IPV6_2.bat 文件并**以管理员权限**执行<br>

@echo off<br>

net start "ip helper"<br>
netsh int ipv6 reset<br>

netsh int teredo set state default<br>
netsh int 6to4 set state default<br>
netsh int isatap set state default<br>
netsh int teredo set state server=teredo.remlab.net<br>
netsh int ipv6 set teredo enterpriseclient<br>
netsh int ter set state enterpriseclient<br>
route DELETE ::/0<br>
netsh int ipv6 add route ::/0 "Teredo Tunneling Pseudo-Interface"<br>
netsh int ipv6 set prefix 2002::/16 30 1<br>
netsh int ipv6 set prefix 2001::/32 5 1<br>
Reg add HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\services\Dnscache\Parameters /v AddrConfigControl /t REG_DWORD /d 0 /f<br>

netsh int teredo set state default<br>
netsh int 6to4 set state default<br>
netsh int isatap set state default<br>
netsh int teredo set state server=teredo.remlab.net<br>
netsh int ipv6 set teredo enterpriseclient<br>
netsh int ter set state enterpriseclient<br>
route DELETE ::/0<br>
netsh int ipv6 add route ::/0 "Teredo Tunneling Pseudo-Interface"<br>
netsh int ipv6 set prefix 2002::/16 30 1<br>
netsh int ipv6 set prefix 2001::/32 5 1<br>
Reg add HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\services\Dnscache\Parameters /v AddrConfigControl /t REG_DWORD /d 0 /f<br>

ipconfig /all<br>
ipconfig /flushdns<br>
netsh int ipv6 show teredo<br>
netsh int ipv6 show route<br>
netsh int ipv6 show int<br>
netsh int ipv6 show prefix<br>
netsh int ipv6 show address<br>
route print<br>
cmd<br>

请先执行IPV6_1.bat再执行IPV6_2.bat，查看命令行执行结果，如报错请查看<br>
[#7241](https://github.com/XX-net/XX-Net/issues/7241)<br>
[#7051](https://github.com/XX-net/XX-Net/issues/7051)<br>
[#6918](https://github.com/XX-net/XX-Net/issues/6918)<br>
[#6991](https://github.com/XX-net/XX-Net/issues/6991)<br>
[#7150](https://github.com/XX-net/XX-Net/issues/7150)<br>
[#7164](https://github.com/XX-net/XX-Net/issues/7164)<br>

### 6.打开[http://test-ipv6.com/](http://test-ipv6.com/)查看IPv6 连接测试<br>
![IP测试](https://user-images.githubusercontent.com/19790792/31531999-382241da-b01d-11e7-8e78-b4952a6e68f8.jpg)<br>
![测试2](https://user-images.githubusercontent.com/19790792/31532009-492a576a-b01d-11e7-8ec6-4aa0458209ad.jpg)<br>

### 7.点击[XX-net本地配置](http://127.0.0.1:8085/?module=gae_proxy&menu=config)打开IPv6并保存设置<br>
![XX设置](https://user-images.githubusercontent.com/16462258/31285565-37111bf6-aaee-11e7-8f17-1d9eec8ccf2d.png)

### 8.一万IP等着您，Good Luck!!<br>
![ip10000](https://user-images.githubusercontent.com/32607791/31721450-02ea0bd2-b44c-11e7-8474-56973be76887.PNG)

### 9.其它<br>
* IPv6使用一段时间连接失败时，登陆[http://test-ipv6.com/](http://test-ipv6.com/)查看是否无法获取IPv6地址，如无法获取时请再**运行两遍IPv6_2.bat**<br>

* **IPV6相关命令及说明**<br>

#停用“ip helper”服务<br>
net stop "ip helper"<br>

#启用“ip helper”服务<br>
net start "ip helper"<br>

#显示Teredo信息<br>
netsh interface ipv6 show teredo<br>

#Teredo、6to4、isatap重置<br>
netsh interface teredo set state default<br>
netsh interface 6to4 set state default<br>
netsh interface isatap set state default<br>

#关闭和卸载Teredo、6to4、isatap<br>
netsh interface teredo set state disable<br>
netsh interface 6to4 set state disabled<br>
netsh interface isatap set state disabled<br>

#重新启用Teredo<br>
netsh interface Teredo set state type=default<br>

#设置Teredo服务器<br>
netsh interface teredo set state server=teredo.remlab.net<br>
netsh interface teredo set state server=teredo-debian.remlab.net<br>
netsh interface teredo set state server=teredo.trex.fi<br>

#设置Teredo服务器为teredo.ipv6.microsoft.com（此teredo服务器已报废）<br>
netsh interface ipv6 set teredo client teredo.ipv6.microsoft.com<br>

#设置isatap服务器（服务器PING不通）<br>
netsh int IPV6 isatap set router isatap.scu.edu.cn<br>

#手动解决Windows7对IPv6支持的瑕疵<br>
netsh interface IPV6 set global randomizeidentifiers=disabled<br>

#启用Teredo<br>
netsh interface ipv6 set teredo enterpriseclient<br>
netsh int ter set state enterpriseclient<br>

#手动换算（IPv4）并设置本地连接（IPv6）地址<br>
#换算IPv4地址<br>
http://ip-lookup.net/conversion.php<br>
#修改本地连接IPv6地址<br>
#子网前缀长度 48<br>

#google ipv6 dns:<br>
2001:4860:4860::8888<br>
2001:4860:4860::8844<br>

#opendns ipv6 dns:<br>
2620:0:ccc::2<br>
2620:0:ccd::2<br>

#HE ipv6 dns:<br>
2001:470:20::2<br>

ipconfig /all<br>
ipconfig /flushdns<br>
netsh int ipv6 show int<br>
netsh int ipv6 show route<br>

#看看teredo状态是不是qualified<br>
netsh int ipv6 show teredo<br>

#删除多余回路<br>
route DELETE ::/0<br>

#添加路由 (这一步重启后需要重新再做一遍)<br>
netsh int ipv6 add route ::/0 "Teredo Tunneling Pseudo-Interface"<br>

#在“start.bat”中添加下面两句，实现XX执行自启<br>
netsh int ipv6 add route ::/0 "Teredo Tunneling Pseudo-Interface"<br>
SET PYTHONPATH="%~dp0%start.vbs" console<br>

#优先级<br>
netsh int ipv6 show prefix<br>
netsh int ipv6 set prefix 2002::/16 30 1<br>
netsh int ipv6 set prefix 2001::/32 5 1<br>

#查看Teredo Tunneling Pseudo-Interface 接口<br>
route print<br>

#显示IPv6地址<br>
netsh interface ipv6 show address<br>

#显示IPv6路由<br>
netsh interface ipv6 show route<br>

#重启ipv6，再重启计算机<br>
netsh interface ipv6 reset<br>

#重启网卡（"本地连接 2"换成自己要重启的网卡名）<br>
netsh interface set interface "本地连接 2" disabled<br>
netsh interface set interface "本地连接 2" enabled<br>

* **感谢热心网友：**<br>
[ylwszb](https://github.com/ylwszb)<br>
[lon91ong](https://github.com/lon91ong)<br>
