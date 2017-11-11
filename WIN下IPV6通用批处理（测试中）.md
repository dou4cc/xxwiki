随着 “墙” 越来越高，给电脑开IPV6成为了一个热门话题，有不少计算机网络爱好者都在研究此问题，俺也是其中一员。

在Issues内已经有不少关于如何开启IPV6的相关帖子，在wiki内还有如何开启IPv6的很多教程可以借鉴。

但是，直到目前为止，对于部分WIN系统用户而言开启IPV6仍然是个难题。


开启IPV6最常见的两大难题（遇到了我也很棘手，不能保证都能处理）：

（1）系统无法自动识别与正确安装隧道适配器

IPV6的隧道适配器分为三种，分别是：teredo、6to4、isatap

teredo：是大家最常用的隧道适配器，主要用于内网。
6to4：具有公网IP且ISP服务商必须提供IPV6服务的才能使用。
isatap：一般是教育网专用，非教育网几乎无法使用。

如能使用原生IPv6是最好不过了，很遗憾大部分用户仍然无法使用。

如果在issues内，咨询和提问都不能解决适配器正确安装和使用的问题，那就请重装系统解决吧！

（2）无法通过公共隧道服务器获取IPV6的IP地址

如果你的适配器能够正常工作，就是收不到公共隧道服务器分配给你的IPV6的IP地址时，请尝试更换新的公共隧道服务器，这样有可能会解决IPV6获取IP地址的问题。

当然，如果你的ISP服务器商屏蔽了你的公共隧道服务器使用，就算更换多少个公共隧道服务器也是无济于事，彻底放弃吧！


言归正传，下面来说说通用批处理：

只有在运行批处理时才能发现上面的两大难题，如果遇到了先在issues内提问或反馈，看看是否能解决，如不能很好的解决，就只能重装系统或更换新的隧道服务器来解决问题了。

本批处理融合了三个隧道，但关闭了6to4和isatap隧道，因为在测试中发现，同时开启三个隧道，有网络干扰和网络不稳定的情况发生。所以只保留开启了teredo隧道，提高稳定性。

本批处理已在 WIN 7/8/10 以及WIN SERVER 2008/2012 下通过测试
XP用户请看wiki中相关教程：https://github.com/XX-net/XX-Net/wiki/IPv6-WinXP

批处理特点（适合大部分WIN系统用户使用）：

（1）无需修改组策略，算是系统无组策略的用户福音
![2](https://user-images.githubusercontent.com/19790792/32687545-ec96ba68-c6f9-11e7-907c-527d699e17af.jpg)

（2）无需开启“本地连接”中的IPV6协议，但必须要安装
![1](https://user-images.githubusercontent.com/19790792/32687548-f79b8ac4-c6f9-11e7-85c2-6cd2d150fe21.jpg)

（3）正常安装且能使用的teredo适配器是这样的
![3](https://user-images.githubusercontent.com/19790792/32687597-00fd8526-c6fb-11e7-9403-db88c965b999.jpg)
还有部分teredo适配器，显示（位置：在 Microsoft IPv4 IPv6 转换适配器总线 上），这样也是正常的。

综上所述，“IPV6 Teredo 隧道通用批处理” 就这样诞生了，批处理文件会放在后面，供大家下载，研究和使用。

@echo ==================================================
@echo WINDOWS 7/8/10 IPV6 Teredo 隧道通用批处理
@echo 6to4 和 isatap 隧道默认是关闭的，需要的可自行开启
@echo 测试中发现三个隧道同时开启，会出现互相干扰等情况
@echo **************************************************
@echo 提示1：请使用 “管理员身份运行” 本批处理文件。
@echo 提示2：执行批处理后如遇问题，请到 issues 内反馈。
@echo **************************************************
@echo 开启IPV6：请按任意键继续——（ 等待完成 ）
@echo 暂不开启：请直接关闭本窗口即可——（ End ）
@echo ==================================================
pause

@echo off

net start "ip helper"
netsh winsock reset

netsh int teredo show state

@echo ++++++++++++++++++++++++++++++++++++++++++++++++++
@echo 【6to4】具有公网IP且ISP服务商提供IPV6服务才可开启
netsh int ipv6 6to4 set state disabled
@echo ++++++++++++++++++++++++++++++++++++++++++++++++++
@echo 【isatap】教育网专用隧道，非教育网请勿开启
netsh int ipv6 isatap set router isatap.tsinghua.edu.cn
netsh int ipv6 isatap set state disabled
@echo ++++++++++++++++++++++++++++++++++++++++++++++++++
netsh int teredo set state default
netsh int teredo set state enterpriseclient server=default
netsh int teredo set state server=teredo.remlab.net
netsh int ipv6 set teredo client teredo.remlab.net
netsh int ipv6 set teredo enterpriseclient
netsh int teredo set state enterpriseclient
route delete ::1/128
route DELETE ::/0
netsh int ipv6 add route ::/0 "Teredo Tunneling Pseudo-Interface"
netsh int ipv6 set prefix 2002::/16 30 1
netsh int ipv6 set prefix 2001::/32 5 1
Reg add HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\services\Dnscache\Parameters /v AddrConfigControl /t REG_DWORD /d 0 /f

@echo ++++++++++++++++++++++++++++++++++++++++++++++++++
@echo 【6to4】具有公网IP且ISP服务商提供IPV6服务才可开启
netsh int ipv6 6to4 set state disabled
@echo ++++++++++++++++++++++++++++++++++++++++++++++++++
@echo 【isatap】教育网专用隧道，非教育网请勿开启
netsh int ipv6 isatap set router isatap.tsinghua.edu.cn
netsh int ipv6 isatap set state disabled
@echo ++++++++++++++++++++++++++++++++++++++++++++++++++
netsh int teredo set state default
netsh int teredo set state enterpriseclient server=default
netsh int teredo set state server=teredo.remlab.net
netsh int ipv6 set teredo client teredo.remlab.net
netsh int ipv6 set teredo enterpriseclient
netsh int teredo set state enterpriseclient
route delete ::1/128
route DELETE ::/0
netsh int ipv6 add route ::/0 "Teredo Tunneling Pseudo-Interface" metric=1
netsh int ipv6 set prefix 2002::/16 30 1
netsh int ipv6 set prefix 2001::/32 5 1
Reg add HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\services\Dnscache\Parameters /v AddrConfigControl /t REG_DWORD /d 0 /f

ipconfig /all
ipconfig /flushdns
ipconfig /registerdns
netsh int ipv6 show teredo
netsh int ipv6 show route
netsh int ipv6 show int
netsh int ipv6 show prefix
netsh int ipv6 show address
route print

ipconfig /all
netsh int ipv6 show route
netsh int ipv6 show int
netsh int teredo show state

@echo ==================================================
@echo 所有命令都已执行完毕，如遇错误信息请反馈到 issues
@echo 如需修复 IPV6 请按任意键继续；不修复请直接关闭窗口
@echo ==================================================
pause
pause
netsh int ip reset
netsh int ipv6 reset
cmd


【重要提示】

（1）执行下面两条命令如报错是正常现象，无需纠结。
route delete ::1/128
route DELETE ::/0

（2）请注意你的teredo适配器名称，如果不是"Teredo Tunneling Pseudo-Interface"，请更换。

（3）执行到批处理最后一步时，会询问是否修复 IP & IPV6 ，如果 IP & IPV6 工作正常，请勿修复，直接关闭窗口即可。

（4）随时用命令观察teredo运行状态，如不稳定请更换teredo公共服务器。
netsh int teredo show state
netsh int ipv6 show teredo


批处理文件下载：[IPV6 update.zip](https://github.com/XX-net/XX-Net/files/1463573/IPV6.zip)
相关参考：
https://github.com/XX-net/XX-Net/wiki/%E5%A6%82%E4%BD%95%E5%BC%80%E5%90%AFIPv6
https://github.com/XX-net/XX-Net/issues/7241