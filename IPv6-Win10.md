## 家庭版
1. 命令行

- 以管理员权限打开命令提示符，输入命令

  ```bat
    // 设置 teredo 服务器，默认为：win10.ipv6.microsoft.com
    netsh interface teredo set state default server=default

    // 重置 ipv6 配置
    netsh interface ipv6 reset
  ```
- 重启系统
- 打开命令提示符，通常 `ipconfig /all` 命令查看当前网络信息，看到 `Teredo Tunneling Pseudo-Interface` 有以 2001 开头的地址即可。
启动IE浏览器，访问 <http://test-ipv6.com>，如果选项卡 “**测试项目**” 下面的 “**不使用域名的 IPv6 测试**” 显示成功，则隧道建立成功。chrome浏览器的测试结果可能和IE不一样，请注意

- 如上面操作后仍无法启用 ipv6，可能是 teredo 服务器无法正常连接，建议修改成其它地址，再检查结果

  ```bat
    //  设置 teredo 服务器为 teredo.remlab.net
    netsh interface teredo set state server=teredo.remlab.net
  ```
## 专业版
1. 命令行

1. 组策略