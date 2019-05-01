使用方法
=======
注意：    
1. 由于封锁严重，软件自带IP已经被封杀殆尽。因此需要**数分钟到数小时的初始化IP扫描**，方能正常运行。    
2. 虽然系统内置了公共appid, 还是建议[[部署自己的appid|how to create my appids]]，公共appid限制看视频。需要注意的是，只有当你能访问Google之后，才能部署自己的APPID。    

# 概述

总体来说，使用XX-Net科学上网，大致需要如下步骤：    
1. **[[获取XX-Net|https://github.com/XX-net/XX-Net/blob/master/code/default/download.md]]**    
2. **设置和初始化**：安装、设置完成后，如果无法翻墙，则需要等待后台程序扫描IP（10分钟到数小时）。    
3. [可选]**[[创建和使用自己的appid|how to create my appids]]**    
4. **[[设置代理]]**    
5. [强烈建议]**获取和配置可靠的浏览器**（[[Firefox火狐浏览器|使用Firefox浏览器]]，或[[Chrome谷歌浏览器|使用Chrome浏览器]]），并使用[[代理切换插件|安装和使用-SwitchyOmega]]。


下面分别介绍各个操作系统平台下的使用方法：


# Windows系统
  1. 以管理员身份运行start.bat。
    - Win7/8/10：将提示请求管理员权限（出于[[安装CA证书|GoAgent Import CA]]的需要）。请点击同意。
  2. 启动完毕后，将弹出浏览器，访问 http://localhost:8085/ （[[配置页面简介]]）
  3. 右下角将出现托盘图标：点击可弹出上述的XX-Net配置页面, 右键可显示[[常用功能菜单|托盘右键菜单]]。
  4. 第一次启动, 会提示在桌面建立快捷方式,可根据自己需要选择。
  - 推荐[[使用Chrome浏览器]], [[安装SwichyOmega|安装和使用-SwitchyOmega]], 可在XX-Net目录中的SwitchyOmega文件夹下找到插件和配置文件。
  - 也可以选择[[使用Firefox（火狐）浏览器|使用Firefox浏览器]]。需[[手动导入证书|GoAgent Import CA#Firefox浏览器手动导入的方式]]
  - 启动失败，请关闭后双击start.bat再次启动程序，把日志发到bug反馈区  

  - WinXP，需要破解tcp连接数，推荐使用[tcp-z](https://github.com/XX-net/tcp-z/archive/master.zip)  
  - Win8，win10 的APP，需要使用：https://loopback.codeplex.com/   
  - Windows Server 2008，需要安装  Visual C++ 2008 Redistributable - x86  

针对两种常用浏览器，分别有详细的新手图文教程：[[使用Firefox浏览器]]、[[使用Chrome浏览器]]

# Mac系统
  1. 双击 start 启动
  2. 证书将被自动导入，如果还有提示非安全连接，请手动导入data/gae_proxy/CA.crt证书

注：
* 命令行启动方式：./start
* 推荐[[使用Chrome|使用Chrome浏览器]]和[[SwitchyOmega扩展|安装和使用-SwitchyOmega]]
* 部分版本可能需要手动升级python。命令为：brew upgrade

# Linux系统
  - 执行 ./start 启动

  - 自动导入证书，需安装 libnss3-tools 包  
 `sudo apt-get install libnss3-tools`
  - 没有安装PyGtk的，需要先安装gtk：
 `sudo apt-get install python-gtk2`
  - 配置http代理 localhost 8087, 勾选全部协议使用这个代理。   
  如Firefox，如果管理页面弹不出，请在地址栏输入127.0.0.1:8085，注意和代理端口的区别：   
![](https://github.com/sonichy/CMDU/blob/master/Firefox%E4%BB%A3%E7%90%86%E8%AE%BE%E7%BD%AE.png)   
    推荐Chrome + SwitchyOmega
  - ubuntu 下，可能需要安装  
     `sudo apt-get install python-openssl`  
     `sudo apt-get install libffi-dev`  
     `sudo apt-get install python-gtk2`   
     `sudo apt-get install python-appindicator`  
     `sudo apt-get install libnss3-tools`  
  - 后台运行：在终端中运行：    
     `xx_net.sh start/stop/restart`
  - 开机自启：在/etc/rc.local中添加一行：    
     `sudo /home/username/xxnet/xx_net.sh start`

## 关于 ArchLinux
  0. 可能需要的包: `python-pyopenssl python2-pyopenssl libffi pygtk python2-notify nss` 
  1. 安装xx-net: 在aur仓库中收录, 需要`yaourt`命令:   
     `yaourt -S xx-net` 
   - 可选用`supervisor`工具进行管理, `xx-net`包中已包含了`supervisor`配置文件:  
     `sudo pacman -S supervisor`  
     `sudo systemctl enable supervisor` 
  2. 安装miredo: 
   - 在x86_64下安装:  
     `yaourt -S miredo`  
     `sudo systemctl enable miredo` 
   - 在armv7h下安装(如: 树莓派):  
     `yaourt -S miredo-debian`  
     `# 此处需要supervisor 托管一个脚本，来解决systemd&sysctl 关于eth0 disable_ipv6的 bug` 
   - 运行miredo  
     `sudo systemctl enable miredo` 

## 关于 Fedora
  - 在bin目录下运行./ srart   (第一次运行时可能需要你同意安装一些依赖)
  - 执行`sudo dnf install miredo`     (安装IP6隧道)
  - 打开浏览器输入127.0.0.1:8085，下载和安装证书
  - 配置浏览器代理插件
  - 在网页的系统配置选项那里打开 开机自启动
  - 如果不会设置开机自启miredo的话，需要每次开机都执行`sudo miredo`来开启IPv6
## OpenSUSE
  - 安装依赖库：
      `sudo zypper install python-gtk-devel pyOpenSSL miredo-client`

  - 安装证书：
       `sudo cp -r CA.crt /etc/ipsec.d/cacerts/`

# 其他平台
## 路由器
  1. OpenWrt
     - [[在OpenWrt LEDE中里运行XX Net（2018.3.14 更新）]]<br>
  2. 梅林固件
     - [[在有USB接口的梅林固件路由器上安装XX-Net-（懒人脚本）]]<br>
  3. 树莓派
     - 使用ArchLinuxArm, armv7h架构的, 见上[关于-ArchLinux](https://github.com/XX-net/XX-Net/wiki/How-to-use#关于-archlinux)

## Android
  - [[Android技术设计]]
  - [安卓版使用说明](https://github.com/XX-net/XX-Net/wiki/%E5%AE%89%E5%8D%93%E7%89%88)
  - FireFox安卓版设置：
    1. Firefox安卓浏览器本身支持安装证书，可以不用安装在手机上。
    2. Firefox安卓浏览器可以使用Pan插件(默认代理方式为SS)，类似pc版的autoproxy插件，可以在about:config 设置代理方式为GoAgent.
    3. 如果不使用代理插件,可在地址栏输入 about:config ,搜索 proxy.type 将5改成1 ,然后搜索 proxy.http ，在上面横线填上 127.0.0.1 下面横线填上 8087

<img src="https://cloud.githubusercontent.com/assets/14154547/23933979/12088db6-097d-11e7-8020-1ebaed563650.png" alt="GitHub" title="GitHub,Social Coding" width="303.75" height="540" /> <img src="https://user-images.githubusercontent.com/23282821/29607899-31211a02-8825-11e7-8799-5e710fc98b71.png" alt="GitHub" title="GitHub,Social Coding" width="303.75" height="540" />

# 附录
## 关于服务端
  - 服务端兼容 GoAgent 3.1.x/3.2.x的客户端
  - 虽然系统内置了公共appid, 还是建议[[部署自己的appid|how to create my appids]]。

## 异常处理
如果出现异常，请翻阅[[故障速查手册]]，查看常见问题和解决方法。    

无法解决的，参考[[异常处理|How-to-get-start-error-log]]，将问题反馈到：  
`https://github.com/XX-net/XX-Net/issues`  
`https://groups.google.com/forum/#!forum/xx-net`  

提交issue时请贴出状态页、GAE_proxy日志、部署日志，以便开发者和其他用户更好地帮助你。