## 家庭版
1. 命令行

- 以管理员权限打开命令提示符（右键单击“开始”图标，然后选择“命令提示符(管理员)”），输入命令

  ```bat
    // 设置 Teredo 服务器，默认为：win10.ipv6.microsoft.com
    netsh interface teredo set state enterpriseclient server=default

    // 重置 IPv6 配置
    netsh interface ipv6 reset
  ```
- 重启系统
- 打开命令提示符，通过 `ipconfig /all` 命令查看当前网络信息，看到 `Teredo Tunneling Pseudo-Interface` 有以 2001 开头的地址即可。
启动IE浏览器，访问 <http://test-ipv6.com>，如果选项卡 “**测试项目**” 下面的 “**不使用域名的 IPv6 测试**” 显示成功，则隧道建立成功。chrome浏览器的测试结果可能和IE不一样，请注意

- 如上面操作后仍无法启用 IPv6，可能是 Teredo 服务器无法正常连接，也可能是 Windows 自身配置问题，可尝试以下两种方法

  ```bat
    // 第一种：修改 Teredo 服务器为 teredo.remlab.net
    netsh interface teredo set state server=teredo.remlab.net

    // 第二种：先卸载当前 Teredo 适配器再重新启用
    netsh interface Teredo set state disable
    netsh interface Teredo set state type=default
  ```

 - 其他参考
   - https://support.xbox.com/zh-CN/xbox-on-windows/social/troubleshoot-party-chat
   - http://www.windows7en.com/jiaocheng/26518.html


## 专业版
### 命令行方法：
 以管理员权限运行 XX-Net\code\default\gae_proxy\local\ipv6_tunnel\enable_ipv6.bat  

### 组策略方法  
* win+R打开gpedit.msc  
 1.png   

* 依顺序打开“计算机配置”——>“管理模板”——>“网络”——>“TCPIP 设置”——>“IPv6 转换技术”  
 2.png   

* “6to4 状态” 和 “ISATAP 状态” 都配置为 “已禁用状态”  
 3.PNG  
 3.1.png   
 3.2.png   

* 重头戏，配置Teredo  
 1. “Teredo 状态” 配置为 “企业客户端”  
  4.1.png   

 2. “Teredo 默认限定” 配置为 “已启用状态”   