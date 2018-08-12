### 1.开启本地路由器UPnP服务，如有光猫请设置成桥接使用自己的路由器拨号<br>
下图为`IPv6`成连接后的路由器显示<br>
![路由器UPnP](https://user-images.githubusercontent.com/31415872/31861133-0dc36056-b75a-11e7-8faf-af3ae5eff830.PNG)

### 2.恢复IPv6组策略默认设置<br>
开始——运行——输入：`gpedit.msc`<br>
参照下图依次打开：计算机配置 —— 管理模板 —— 网络 —— TCP/IP 设置 —— IPv6 转换技术，如有已配置或禁用、启用等均修改为“未配置”
![IPv6组策略](https://user-images.githubusercontent.com/19790792/31531180-110454b2-b018-11e7-8d87-0bda5c0fc4f8.jpg)

### 3.恢复防火墙默认设置<br>
开始 —— 控制面板 —— 查看方式“大图标” —— Windows 防火墙 —— 还原默认设置
![防火墙设置](https://user-images.githubusercontent.com/19790792/31532888-71595d30-b022-11e7-83b5-c75e3452dbc0.jpg)

### 4.设置本地连接 IPv4 和 IPv6 的 DNS<br>
|IPv4 DNS|
|-|
| 180.76.76.76 |
| 114.114.114.114 |
> 参考 [http://ip.cn/dns.html](http://ip.cn/dns.html) 

![IPv4 DNS 设置](https://user-images.githubusercontent.com/19790792/31531466-ddbc34e2-b019-11e7-902f-b9c97b7ccb34.jpg) <br>

|IPv6 DNS|
|-|
| 2001:4860:4860::8888 |
| 2001:4860:4860::8844 |

![IPv6 DNS 设置](https://user-images.githubusercontent.com/19790792/31531486-039ad5b0-b01a-11e7-84ff-8bf9da24fe89.jpg)

### 5.执行一键批处理开启 IPv6 操作<br>
* 请将下列命令保存成 `IPV6_1.bat` 文件并**以管理员权限**执行<br>
其中的**网络连接**请根据自己实际使用情况**修改**为您本机上述第三步配置DNS的网络连接，如**网络连接**或**网络连接2**、**网络连接3**……<br>

```
@echo off

net start "ip helper"
netsh int ipv6 reset

netsh int teredo set state default
netsh int 6to4 set state default
netsh int isatap set state default
netsh int teredo set state server=teredo.remlab.net
netsh int ipv6 set teredo enterpriseclient
netsh int ter set state enterpriseclient
route DELETE ::/0
netsh int ipv6 add route ::/0 "网络连接"
netsh int ipv6 set prefix 2002::/16 30 1
netsh int ipv6 set prefix 2001::/32 5 1
Reg add HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\services\Dnscache\Parameters /v AddrConfigControl /t REG_DWORD /d 0 /f

netsh int teredo set state default
netsh int 6to4 set state default
netsh int isatap set state default
netsh int teredo set state server=teredo.remlab.net
netsh int ipv6 set teredo enterpriseclient
netsh int ter set state enterpriseclient
route DELETE ::/0
netsh int ipv6 add route ::/0 "网络连接"
netsh int ipv6 set prefix 2002::/16 30 1
netsh int ipv6 set prefix 2001::/32 5 1
Reg add HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\services\Dnscache\Parameters /v AddrConfigControl /t REG_DWORD /d 0 /f

ipconfig /all
ipconfig /flushdns
netsh int ipv6 show teredo
netsh int ipv6 show route
netsh int ipv6 show int
netsh int ipv6 show prefix
netsh int ipv6 show address
route print
cmd
```
* 请将下列命令保存成 IPV6_2.bat 文件并**以管理员权限**执行<br>
```
@echo off

net start "ip helper"
netsh int ipv6 reset

netsh int teredo set state default
netsh int 6to4 set state default
netsh int isatap set state default
netsh int teredo set state server=teredo.remlab.net
netsh int ipv6 set teredo enterpriseclient
netsh int ter set state enterpriseclient
route DELETE ::/0
netsh int ipv6 add route ::/0 "Teredo Tunneling Pseudo-Interface"
netsh int ipv6 set prefix 2002::/16 30 1
netsh int ipv6 set prefix 2001::/32 5 1
Reg add HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\services\Dnscache\Parameters /v AddrConfigControl /t REG_DWORD /d 0 /f

netsh int teredo set state default
netsh int 6to4 set state default
netsh int isatap set state default
netsh int teredo set state server=teredo.remlab.net
netsh int ipv6 set teredo enterpriseclient
netsh int ter set state enterpriseclient
route DELETE ::/0
netsh int ipv6 add route ::/0 "Teredo Tunneling Pseudo-Interface"
netsh int ipv6 set prefix 2002::/16 30 1
netsh int ipv6 set prefix 2001::/32 5 1
Reg add HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\services\Dnscache\Parameters /v AddrConfigControl /t REG_DWORD /d 0 /f

ipconfig /all
ipconfig /flushdns
netsh int ipv6 show teredo
netsh int ipv6 show route
netsh int ipv6 show int
netsh int ipv6 show prefix
netsh int ipv6 show address
route print
cmd
```
- 请先执行`IPV6_1.bat`再执行`IPV6_2.bat`，查看命令行执行结果，如报错请查看<br>
[#7241](https://github.com/XX-net/XX-Net/issues/7241)
[#7051](https://github.com/XX-net/XX-Net/issues/7051)
[#6918](https://github.com/XX-net/XX-Net/issues/6918)
[#6991](https://github.com/XX-net/XX-Net/issues/6991)
[#7150](https://github.com/XX-net/XX-Net/issues/7150)
[#7164](https://github.com/XX-net/XX-Net/issues/7164)

### 6.打开[http://test-ipv6.com/](http://test-ipv6.com/)查看 IPv6 连接测试<br>
![IP测试](https://user-images.githubusercontent.com/19790792/31531999-382241da-b01d-11e7-8e78-b4952a6e68f8.jpg)<br>
![测试2](https://user-images.githubusercontent.com/19790792/31532009-492a576a-b01d-11e7-8ec6-4aa0458209ad.jpg)<br>

### 7.点击[XX-net本地配置](http://127.0.0.1:8085/?module=gae_proxy&menu=config)打开 IPv6 并保存设置<br>
![XX设置](https://user-images.githubusercontent.com/16462258/31285565-37111bf6-aaee-11e7-8f17-1d9eec8ccf2d.png)

### 8.一万 IP 等着您，Good Luck!!<br>
![ip10000](https://user-images.githubusercontent.com/32607791/31721450-02ea0bd2-b44c-11e7-8474-56973be76887.PNG)

### 9.其它<br>
* IPv6 使用一段时间连接失败时或 IPv6 可用地址为零时，请转到 XX-net 的 web 界面，点击高级——检查所有 IP ——运行，如检查完毕有效 IP 仍为零请**运行一遍 IPv6_2.bat**，点击屏幕右下角 XX-net 图标选择重启 GAEporxy 再通过检查 IP 来获取有效 IP<br>

* IPv6 使用一段时间连接失败时请打开[http://test-ipv6.com/](http://test-ipv6.com/)查看是否无法获取 IPv6 地址，如无法获取时请再**运行一遍 IPv6_2.bat**<br>

* IPv6_2.bat运行报错请打开命令行运行以下命令<br>
> netsh int ipv6 show teredo
- 查看 Teredo 服务器连接<br>
状态——probe     （请求中）<br>
状态——offline   （离线）<br>
状态——qualified （正常使用）<br>
- 请将`IPv6_2.bat`中的
> netsh interface teredo set state server=teredo.remlab.net

teredo.remlab.net 修改为以下备选 Teredo 服务器中的一个（有两处修改，请注意）

|Teredo 服务器|
|-|
|teredo-debian.remlab.net|
|teredo.trex.fi|
|teredo2.remlab.net|
|teredo.iks-jena.de|

替换一次就保存一次，再运行 IPv6_2.bat，再来用`netsh int ipv6 show teredo`检查查看 Teredo 服务器状态，直到状态显示为`qualified`就可以重启 GAEporxy 再通过检查 IP 来获取有效 IP，请保持耐心多试几次（有时 ping 不通的 Teredo 服务器也是可用的）一定会成功。

* **IPv6 相关命令及说明**<br>

- 停用“ip helper”服务
> net stop "ip helper"

- 启用“ip helper”服务
> net start "ip helper"

- 显示 Teredo 信息
> netsh interface ipv6 show teredo

- Teredo、6to4、isatap 重置
```
netsh interface teredo set state default
netsh interface 6to4 set state default
netsh interface isatap set state default
```
- 关闭和卸载 Teredo、6to4、isatap
```
netsh interface teredo set state disable
netsh interface 6to4 set state disabled
netsh interface isatap set state disabled
```
- 重新启用 Teredo
> netsh interface Teredo set state type=default

- 设置Teredo服务器
```
netsh interface teredo set state server=teredo.remlab.net
netsh interface teredo set state server=teredo-debian.remlab.net
netsh interface teredo set state server=teredo.trex.fi
```
- 设置Teredo服务器为teredo.ipv6.microsoft.com（此teredo服务器已报废）
> netsh interface ipv6 set teredo client teredo.ipv6.microsoft.com

- 设置isatap服务器（服务器 ping 不通）
>　netsh int IPV6 isatap set router isatap.scu.edu.cn

- 手动解决Windows7对IPv6支持的瑕疵
> netsh interface IPV6 set global randomizeidentifiers=disabled

- 启用 Teredo
```
netsh interface ipv6 set teredo enterpriseclient
netsh int ter set state enterpriseclient
```
- 手动换算`IPv4`并设置本地连接`IPv6`地址
  - 换算`IPv4`地址：http://ip-lookup.net/conversion.php
  - 修改本地连接`IPv6`地址
  - 子网前缀长度 48

  |提供方|DNS|
  |-|-|
  |Google IPv6 DNS | 2001:4860:4860::8888 <br> 2001:4860:4860::8844|
  |OpenDNS IPv6 DNS | 2620:0:ccc::2<br> 2620:0:ccd::2 |
  |HE IPv6 DNS | 2001:470:20::2 |

```
ipconfig /all
ipconfig /flushdns
netsh int ipv6 show int
netsh int ipv6 show route
```

- 看看 teredo 状态是不是`qualified`
> netsh int ipv6 show teredo

- 删除多余回路
>　route DELETE ::/0

- 添加路由 (这一步重启后需要重新再做一遍)
> netsh int ipv6 add route ::/0 "Teredo Tunneling Pseudo-Interface"

- 在“start.bat”中添加下面两句，实现`XX-net`执行自启
```
netsh int ipv6 add route ::/0 "Teredo Tunneling Pseudo-Interface"
SET PYTHONPATH="%~dp0%start.vbs" console
```

- 优先级
```
netsh int ipv6 show prefix
netsh int ipv6 set prefix 2002::/16 30 1
netsh int ipv6 set prefix 2001::/32 5 1
```
- 查看 `Teredo Tunneling Pseudo-Interface` 接口
> route print

- 显示`IPv6`地址
> netsh interface ipv6 show address

- 显示 IPv6 路由
> netsh interface ipv6 show route

- 重启 IPv6，再重启计算机
> netsh interface ipv6 reset

- 重启网卡（"本地连接 2"换成自己要重启的网卡名）
```
netsh interface set interface "本地连接 2" disabled
netsh interface set interface "本地连接 2" enabled
```
* **感谢热心网友：**<br>
[ylwszb](https://github.com/ylwszb)<br>
[lon91ong](https://github.com/lon91ong)<br>
