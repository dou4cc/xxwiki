## 家庭版
1. 命令行

- Win+X 打开Windows PowerShell（管理员），输入命令

  ```bat
    // 设置 Teredo 服务器，默认为：win10.ipv6.microsoft.com
    netsh interface teredo set state enterpriseclient server=default
    ping -6 ipv6.test-ipv6.com

    // 重置 IPv6 配置
    netsh interface ipv6 reset
  ```
- 重启系统
- 通过命令`ipconfig /all` 命令查看当前网络信息，看到 `Teredo Tunneling Pseudo-Interface` 有以 2001 开头的地址即可。
启动IE浏览器，访问 <http://test-ipv6.com>/<http://ipv6.test-ipv6.com>，如果选项卡 “**测试项目**” 下面的 “**不使用域名的 IPv6 测试**” 显示成功，则隧道建立成功。chrome浏览器的测试结果可能和IE不一样，请注意

- 如上面操作后仍无法启用 IPv6，可能是 Teredo 服务器无法正常连接，也可能是 Windows 自身配置问题，可尝试以下两种方法

  ```bat
    // 第一种：修改 Teredo 服务器为 teredo.remlab.net
    netsh interface teredo set state server=teredo.remlab.net

    // 第二种：先卸载当前 Teredo 适配器再重新启用
    netsh interface Teredo set state disable
    netsh interface Teredo set state type=default
    ping -6 ipv6.test-ipv6.com
  ```
   ![dormant](https://user-images.githubusercontent.com/31188782/33047065-cf1932f8-ce8e-11e7-9701-c0a679886859.png)

## 专业版
### 命令行方法：
 同家庭版  

### 组策略方法  
* Win+R 打开gpedit.msc  
 ![组策略](https://user-images.githubusercontent.com/31188782/33045995-0b620dac-ce8a-11e7-9df2-e704eb987d9d.png)  

* 依顺序打开“计算机配置”——>“管理模板”——>“网络”——>“TCPIP 设置”——>“IPv6 转换技术” ，

   “6to4 状态” 和 “ISATAP 状态” 都配置为 “已禁用状态” ，

   **“Teredo 状态” 配置为 “企业客户端”，“Teredo 默认限定” 配置为 “已启用状态”**

   ![IPv6 转换技术](https://user-images.githubusercontent.com/31188782/33046760-6e3af0d0-ce8d-11e7-8a39-ea26ca3d2212.png)

   ___![Teredo 状态](https://user-images.githubusercontent.com/31188782/33046845-ca9bab1c-ce8d-11e7-8a4b-b485befea07e.png)

## 其他参考
   - https://support.xbox.com/zh-CN/xbox-on-windows/social/troubleshoot-party-chat
   - https://support.xbox.com/zh-HK/xbox-on-windows/social/troubleshoot-party-chat
   - http://www.windows7en.com/jiaocheng/26518.html

   [![xbox](https://user-images.githubusercontent.com/31188782/33045390-948f05ba-ce87-11e7-99e8-6c3ffb0ccfbf.png)](https://support.xbox.com/en-US/xbox-on-windows/social/troubleshoot-party-chat)

