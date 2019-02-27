## Teredo隧道 
 
### 命令行方法 
### **运行code\default(或最新版本号)\gae_proxy\local\ipv6_tunnel文件夹下的enable_ipv6.bat**

>下面的"**有效的Teredo接口名称**”需要自己查找替换，具体名称规则，不是**Teredo**开头的“Teredo Tunneling Pseudo-Interface”，就是**本地连接**挂*的，状态应该是**已连接**(connected)

右键管理员权限执行一次，稍等一下（10~20s左右），执行`netsh int ipv6 add route ::/0 "有效的Teredo接口名称"`(**引号不可缺**) 回显提示：“**对象已存在**”即可。
访问[IPv6测试页](http://test-ipv6.com/)，结果如下图所示，只要保证那一项成功即可：
![20171007103126](https://user-images.githubusercontent.com/16462258/31313145-c2847fac-ac0b-11e7-854a-ea2137f9447d.png)
>@Anudorannador 反应下面一步不需要，应该是跟系统的安全设置方面相关。Win10比Win7更严格！
关键在于上一步设置的路由表第一项还在不在，反正我用的[Win10 LTSB企业版](http://bbs.pcbeta.com/viewthread-1750409-1-1.html) 是重启就没了

以后每次重启之后，都要执行`netsh int ipv6 add route ::/0 "有效的Teredo接口名称" metric=1`再启动XX-Net，可以把它写入XX-Net目录中的start.bat中：
```shell
@echo off
netsh int ipv6 add route ::/0 "有效的Teredo接口名称" metric=1
SET PYTHONPATH=
"%~dp0%start.vbs" noconsole
```
发个快捷方式到桌面，改“管理员权限”，以后启动XX-Net用这个快捷方式就好了！
![20171007121255](https://user-images.githubusercontent.com/16462258/31304665-110bc54e-ab59-11e7-92d6-e87eaf3a0f2e.png)


### 总结回溯排错步骤
1. 检查路由表，`netsh int ipv6 show route`，看看你设置的是不是**唯一**的` ::/0 `项。如果多余不唯一，参见下面问题3。如果没有你设置的则跳转到下一步检查。
2. 检查teredo服务状态，`netsh int ipv6 show teredo`，看看**状态**是不是`qualified`，[参考解决办法](http://ju.outofmemory.cn/entry/94277)。连**状态行**都没有的话，[检查IP Helper服务是否启动](#issuecomment-334945915)，进一步参考[“未能打开隧道适配器”](#issuecomment-334978237) @qumaggot [修改注册表的方法](https://github.com/XX-net/XX-Net/issues/6918#issuecomment-334987098) @FrankHB [参考方法](http://support.xbox.com/zh-CN/xbox-on-windows/social/troubleshoot-party-chat)
3. 检查**策略组**(运行gpedit.msc开启)中的ISATAP状态是不是下图的样子

![isatap](https://user-images.githubusercontent.com/16462258/31307823-0ff8536c-ab9e-11e7-887f-505ef8c52a33.png)

家庭版的系统没有**策略组**，使用`netsh int ipv6 show int`查看网络接口中有没有`isatap`开头的

4. 检查网络连接的IPv6静态网址和IPv4自动获取的网址是不是对应的，如果出现IPv6退回自动的状态，参见下面的问题
5. **建议把IPv4地址也设置成静态或者在路由器中设置绑定MAC地址到固定IP。**

### 补充几个常见问题
1. 有个别朋友的网络环境差异，导致Teredo服务器可能连不上，尝试几次换换服务器可能成功。[参考](http://ju.outofmemory.cn/entry/94277)
2. 注意检查有效的Teredo接口名称，不是**Teredo**开头的，就是**本地连接**挂*的，状态应该是**已连接**(connected)
3. 遇到了两个朋友，路由表有多余的**回路**(Loopback Pseudo-Interface)占用了首选位置，需要先删除：`route DELETE ::/0 ` 再重新添加：`netsh int ipv6 add route ::/0 "有效的Teredo接口名称" metric=1`
4. 还有极个别由于系统优化的原因导致**IP Helper**服务被禁用的，需要手动启用
5. 遇到几例网卡没有IPv6地址的情况，`ipconfig -all`查看没有任何v6地址，先试试@robinshiesh [修改防火墙规则](https://github.com/XX-net/XX-Net/issues/6918#issuecomment-335667804)的方法；手动设置地址后会跳回自动，这个问题是系统设置的个例，[参考解决办法一](http://www.windows7en.com/jiaocheng/26518.html)，[微软修复工具](https://support.microsoft.com/en-us/help/929852/how-to-disable-ipv6-or-its-components-in-windows)，实在不行试试[#7100](https://github.com/XX-net/XX-Net/issues/7100)的方法，也可以参考[知乎的类似问题](https://www.zhihu.com/question/50283246)
6. 有几个电信用户，路由表首位总是被莫名其妙的占据，[解决方法](http://ximalas.info/2014/02/04/disabling-ipv6-autoconfiguration-in-windows-servers/)如下：
`netsh interface ipv6 set interface "本地连接" routerdiscovery=disabled` 注意把“本地连接”换成你的连接路由器的连接名
7. 之前Teredo连不上的时候我都推荐连芬兰的那个服务器`teredo.trex.fi`，今天试了试，很痛快的连上了，但就是测试页的关键项通不过，反复检查了其它设置都无误，最后试着换成微软默认的Teredo服务器：`win10.ipv6.microsoft.com`，一次通过。

来了