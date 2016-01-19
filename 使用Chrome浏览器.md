本页面将详细演示如何在一台全新的Windows7电脑上架设起Chrome+XXnet的上网渠道。

本文包含以下部分：

1. [[下载和安装Chrome浏览器|使用Chrome浏览器#下载和安装Chrome浏览器]]
2. [[获取和运行XX-Net|使用Chrome浏览器#%E8%8E%B7%E5%8F%96%E5%92%8C%E8%BF%90%E8%A1%8Cxx-net]]
3. [[设置代理|使用Chrome浏览器#设置代理]]
4. [[手动导入证书|使用Chrome浏览器#手动导入证书]]

# 下载和安装Chrome浏览器
## 下载
* Chrome官网下载地址：http://www.google.cn/intl/zh-CN/chrome/browser/desktop/index.html
![Chrome官网](https://raw.githubusercontent.com/yeahwu/recycle-bin/master/cxx.JPG)
* 虽然是CN网站，但是挂了"google"这个敏感词，所以会经常抽风。那么下面就多提供几个下载地址。

  _ 浏览迷网站：http://liulanmi.com/  
  _ 新浪软件中心：http://tech.sina.com.cn/down/  
  _ 卡饭chrome区：http://bbs.kafan.cn/forum-214-1.html  

上面几个网站搜索或者点击chrome浏览器下载，建议用“Stable（稳定版）”

# 安装
* 为了不侮辱大家的智商，安装Chrome就不详解了，一路“确定”就ok了。

# 获取和运行XX-Net
* 打开[[https://github.com/XX-net/XX-Net#下载链接]]，注意看网址前是否有绿色的证书验证成功的显示。
![下载链接](https://cloud.githubusercontent.com/assets/6830787/10131883/fe7b78ba-6605-11e5-9bff-75dd7e24a42b.PNG)
* 选择下载稳定版，下载之后解压缩。运行文件夹中的start快捷方式（也可以运行start.vbs）
![运行](https://cloud.githubusercontent.com/assets/6830787/10131884/fea44a56-6605-11e5-95e0-9c8b301f45bf.PNG)
* 如果弹出管理员权限请求（用户账户控制），请允许。

![管理员权限请求](https://cloud.githubusercontent.com/assets/6830787/10132435/079df852-6609-11e5-824d-06c8c4bb929b.PNG)

* 首次运行可能会弹出防火墙警告，请允许访问。

![防火墙警告](https://cloud.githubusercontent.com/assets/6830787/10131885/feb9afa4-6605-11e5-82c5-b2f15eb2ebd2.PNG)

# 设置代理
## 方案一：简单方法
* 启动XX-Net后，右下角会出现[[托盘图标|托盘右键菜单]]。右键单击托盘图标，点击“全局PAC智能代理”即可。
![托盘右键菜单](https://cloud.githubusercontent.com/assets/6830787/10132436/07a149f8-6609-11e5-8e1b-1dbe9336b226.PNG)

## 方案二：安装和使用代理切换插件
* 打开XX-Net/SwitchyOmega文件夹；打开浏览器，设置-扩展程序 页面。把SwitchyOmega.crx文件拖放到浏览器扩展程序页面安装。如图
![SwitchyOmega](https://raw.githubusercontent.com/yeahwu/recycle-bin/master/xx0.JPG)
![安装扩展程序](https://raw.githubusercontent.com/yeahwu/recycle-bin/master/xx1.JPG)
* 添加扩展程序
![添加扩展程序](https://raw.githubusercontent.com/yeahwu/recycle-bin/master/xx2.JPG)
* 跳过教程
![教程](https://raw.githubusercontent.com/yeahwu/recycle-bin/master/xx3.JPG)
* 导入bak文件
![导入／导出](https://raw.githubusercontent.com/yeahwu/recycle-bin/master/xx4.JPG)

