> **提示**：本文基于Teredo隧道开启IPv6，其他开启IPv6的方法暂待完善。

> **特别重要**：找到 网络和共享中心 - 更改适配器设置 - 本地连接（无线网络则找到WLAN或蓝牙网络连接）- 属性，把 IPv6协议 前面的勾去掉，确定。*否则会出现一些[奇怪的问题](https://github.com/XX-net/XX-Net/issues/8709)。*

## 家庭版

### 命令行：

同[专业版或企业版的命令行方法](https://github.com/XX-net/XX-Net/wiki/IPv6-Win10#%E5%91%BD%E4%BB%A4%E8%A1%8C-1)

## 专业版或企业版

### 命令行：

- Win+X 打开CMD 或 Windows PowerShell（管理员），输入命令：

  ```bat
    // 设置 Teredo 服务器，默认为：win10.ipv6.microsoft.com
    netsh interface teredo set state enterpriseclient server=default
    
    // 测试 IPv6 连接
    ping -6 ipv6.test-ipv6.com
    ping -6 [2001:470:1:18::125]

    // 重置 IPv6 配置
    netsh interface ipv6 reset
  ```

- 重启系统

- 通过命令`ipconfig /all` 查看当前网络信息，看到 `Teredo Tunneling Pseudo-Interface` 有以 2001 开头的IPv6地址即可。
  启动IE浏览器，访问 <http://test-ipv6.com> 或 <http://ipv6.test-ipv6.com>，如果选项卡 “**测试项目**” 下面的 “**不使用域名的 IPv6 测试**” 显示成功，则隧道建立成功。*Chrome浏览器的测试结果可能和IE不一样，请注意*

- 如果经过上面操作后仍无法启用 IPv6，可能是 Teredo 服务器无法正常连接，也可能是 Windows 自身配置问题，可尝试以下两种方法：

  ```bat
    // 第一种：修改 Teredo 服务器为 teredo.remlab.net
    netsh interface teredo set state server=teredo.remlab.net

    // 第二种：先卸载当前 Teredo 适配器再重新启用
    netsh interface Teredo set state disable
    netsh interface Teredo set state type=default
    ping -6 ipv6.test-ipv6.com
  ```

   ![dormant](https://user-images.githubusercontent.com/31188782/33047065-cf1932f8-ce8e-11e7-9701-c0a679886859.png)

### 脚本：

打开XX-Net目录，切换到 code\default\gae_proxy\local\ipv6_tunnel，执行 **enable_ipv6.bat**

### 组策略方法:

> **建议不要混用两种方法**

- Win+R 打开 组策略 gpedit.msc

  ![组策略](https://user-images.githubusercontent.com/31188782/33045995-0b620dac-ce8a-11e7-9df2-e704eb987d9d.png)  

- 打开 “计算机配置” - “管理模板” - “网络” - “TCPIP 设置” -  “IPv6 转换技术” ，

  “6to4 状态” 和 “ISATAP 状态” 都配置为 “已禁用状态” ，

  **“Teredo 状态” 配置为 “企业客户端”，“Teredo 默认限定” 配置为 “已启用状态”**

   ![IPv6 转换技术](https://user-images.githubusercontent.com/31188782/33046760-6e3af0d0-ce8d-11e7-8a39-ea26ca3d2212.png)

   ![Teredo 状态](https://user-images.githubusercontent.com/31188782/33046845-ca9bab1c-ce8d-11e7-8a4b-b485befea07e.png)



**提示**：如按照教程设置无效出现其他莫名其妙的问题，建议：

- 管理员模式运行disable_ipv6.bat。（如是用的组策略模式，请把所有更改过的组策略改成未配置）

   删除regedit：计算机\HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\ 下面的Tcpip6和TCPIP6TUNNEL两个选项。（**改动注册表之前请备份**）

- 在[自动禁用或重新启用 IPv6 或其组件](https://support.microsoft.com/zh-cn/help/929852/how-to-disable-ipv6-or-its-components-in-windows)下载 "在非隧道接口和 IPv6 隧道接口上重新启用 IPv6" ，运行后重启电脑，然后按照组策略教程再重做一遍。（切记：组策略方法开启IPv6必须指定服务器名称）

- 文章开头提示的：禁用IPv6协议。

## 其他参考

- https://support.xbox.com/zh-CN/xbox-on-windows/social/troubleshoot-party-chat

- https://support.xbox.com/zh-HK/xbox-on-windows/social/troubleshoot-party-chat

- http://www.windows7en.com/jiaocheng/26518.html

- [Launch the Windows Settings app](https://docs.microsoft.com/en-us/windows/uwp/launch-resume/launch-settings-app)

  - ms-settings:gaming-xboxnetworking

  - ms-settings:network-proxy

    [![xbox](https://user-images.githubusercontent.com/31188782/33045390-948f05ba-ce87-11e7-99e8-6c3ffb0ccfbf.png)](https://support.xbox.com/en-US/xbox-on-windows/social/troubleshoot-party-chat)