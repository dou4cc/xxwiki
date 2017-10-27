

工具是一个DOS命令的UI，可以方便更换Teredo代理，禁用Teredo代理，通过IPV4网络（联通，电信的网络）来访问IPV6网站。

本工具支持穿越路由器（NAT穿透）来访问IPV6，适用于不熟悉netsh命令，也适合于快速切换teredo服务器(不用去CMD下运行netsh了）

### 下载IPV6Teredo程序。下载地址以及MD5验证码如下：
- IPV6Teredo For XP下载地址：[ipv6teredoforxp.zip](https://github.com/XX-net/XX-Net/files/1405084/ipv6teredoforxp.zip)
- IPV6Teredo For XP.exe 的Md5码：97BEA8119910B7D15828DCBC1C01BCB9 
- ipv6teredoforxp.zip 的Md5码: 4F416C199EDA4D9C8FE74558636BB083


特别提示: 请一定注意MD5验证码是否正确，以免下载的软件被人恶意修改过。

可以在Sourceforge上面下载MD5 验证工具 http://sourceforge.net/projects/md5tools/。

在线病毒检测http://r.virscan.org/report/da27d23a5e6788120d532a99d40b22b7

### 运行IPV6Teredo程序。将下载的压缩文件解压后，直接运行IPV6Teredo即可，运行界面如下。
![image](https://user-images.githubusercontent.com/31188782/31864143-3917f4b6-b78b-11e7-9dfa-4dfc9c23eca2.png)

各个按钮会打开DOS界面，是正常现象，毕竟工具只是个封装了netsh命令的UI。

注：对于XXNet的使用，ipv6优先和hosts文件不是必须设置的

1. 如果你以前没有安装过IPV6协议，需要先安装IPV6协议。软件提供了快速安装IPV6协议的按钮，即"安装IPV6协议"。你也可以通过其它方法安装IPV6协议。

1. 选择一个你要使用的Teredo隧道服务器，软件所列的是网络上公开的Teredo隧道服务器，如你发现新的好用的Teredo服务器，烦请通知我。

1. 如果你有公网IP，那么需要选择"我有公网IP"这个选择框。如果你不能确认是否有公网IP，可以先不选择这个复选框。

1. 选择Teredo隧道服务器，设置好"我有公网IP"复选框后，点"开启隧道"。

1. 如果一个网站（如Google.com)同时存在IPV4 和 IPV6两个网络，大多数浏览器是优先访问IPV4网络的,这是需要启用IPV6优先，直接单击"启用IPV6优先"即可。

1. 某些DNS服务器不能正常解析IPV6的IP地址，此时需要你设置Hosts文件。点击"编辑Hosts文件"可以快速打开Hosts文件，详细地Hosts文件设置规则打开"查看Hosts文件设置规则"即可。

1. 当你不需要使用IPV6隧道时，可以禁用隧道，即"禁用隧道"按钮。

**转载自：星海博客 http://starhai.net/2011/357.htm**
