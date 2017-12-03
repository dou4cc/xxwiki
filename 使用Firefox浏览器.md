本页面将详细演示如何在一台全新的Windows7电脑上架设起Firefox+XXnet的上网渠道。（中英对照）

本文包含以下部分：

1. [[下载和安装Firefox浏览器|使用Firefox浏览器#下载和安装Firefox浏览器]]
2. [[获取和运行XX-Net|使用Firefox浏览器#%E8%8E%B7%E5%8F%96%E5%92%8C%E8%BF%90%E8%A1%8Cxx-net]]
3. [[设置代理|使用Firefox浏览器#设置代理]]
4. [[手动导入证书|使用Firefox浏览器#手动导入证书]]

# [下载和安装Firefox浏览器](https://support.mozilla.org/zh-CN/products/firefox/install-and-update-firefox)

## 下载
  打开火狐官网下载浏览器：[[https://www.mozilla.org/zh-CN/firefox/new/]]。

  在“[所有系统和语言](https://www.mozilla.org/zh-CN/firefox/all/)”页面找到所有支持的语言和操作系统。

## 安装

* 在“[所有系统和语言](https://www.mozilla.org/zh-CN/firefox/all/)”页面下载的是完整安装包。运行安装包时可能会跳出警告，点击“运行”即可。

![警告](https://cloud.githubusercontent.com/assets/6830787/10131402/a4363082-6602-11e5-84a1-81b8de5f50f5.PNG)

* 如果你不想安装“静默更新服务”，请选择“自定义安装”，否则一路下一步即可。

![自定义安装](https://cloud.githubusercontent.com/assets/6830787/10131437/d57f59d4-6602-11e5-8e79-00c5fc3bf51b.PNG)

* 安装完成后，程序会询问您是否要从其他浏览器中导入资料。您可以自行决定是否导入。

![导入资料](https://cloud.githubusercontent.com/assets/6830787/10131375/7330f5a8-6602-11e5-831d-e7c92213f80a.PNG)

# 获取和运行XX-Net
* 打开[[https://github.com/XX-net/XX-Net#下载链接]]，注意看网址前是否有绿色的证书验证成功的显示。
![下载链接](https://cloud.githubusercontent.com/assets/6830787/10131883/fe7b78ba-6605-11e5-9bff-75dd7e24a42b.PNG)
* 选择下载稳定版，下载之后解压缩。运行文件夹中的start.bat，生成桌面快捷方式（以后通过快捷方式启动）
[](https://cloud.githubusercontent.com/assets/6830787/10131884/fea44a56-6605-11e5-95e0-9c8b301f45bf.PNG)
* 如果弹出管理员权限请求（用户账户控制），请允许。

![管理员权限请求](https://cloud.githubusercontent.com/assets/6830787/10132435/079df852-6609-11e5-824d-06c8c4bb929b.PNG)

* 首次运行可能会弹出防火墙警告，请允许访问。

![防火墙警告](https://cloud.githubusercontent.com/assets/6830787/10131885/feb9afa4-6605-11e5-82c5-b2f15eb2ebd2.PNG)

# 设置代理
## 方案一：简单方法
* 启动XX-Net后，右下角会出现[[托盘图标|托盘右键菜单]]。右键单击托盘图标，点击“全局PAC智能代理”即可。
![托盘右键菜单](https://cloud.githubusercontent.com/assets/6830787/10132436/07a149f8-6609-11e5-8e1b-1dbe9336b226.PNG)
* 火狐菜单 - 选项 - 高级 - 网络 - 设置，勾选自动代理设置，输入：http://127.0.0.1:8086/proxy.pac  ，完成。
* 当然最后一步还是要手动导入证书，就可以畅游网络了。


## 方案二：安装和使用代理切换插件
firefox57+ 可用插件：
* https://addons.mozilla.org/zh-CN/firefox/addon/simpleproxy/
* https://addons.mozilla.org/zh-CN/firefox/addon/switchyomega/ 
* https://addons.mozilla.org/zh-CN/firefox/addon/foxyproxy-basic/
  
* 56与长期支持版，可安装pan代理插件
  - https://addons.mozilla.org/zh-CN/firefox/addon/pan/?src=search
![安装pan](https://raw.githubusercontent.com/yeahwu/wu/master/pan1.png)
* 添加过滤规则，右键点击pan插件，然后再点击“过滤规则首选项”
![过滤规则](https://raw.githubusercontent.com/yeahwu/wu/master/pan2.jpg)
* 添加过滤规则订阅组，先点击“添加过滤规则订阅组”，再点击“添加”，完成。一定要添加订阅“GFWList Main”规则组。
![添加过滤规则订阅组](https://raw.githubusercontent.com/yeahwu/recycle-bin/master/pan4.jpg)
* 选择默认代理，右键点击pan，选择默认代理，再点击goagent代理。
![默认代理](https://raw.githubusercontent.com/yeahwu/wu/master/pan5.jpg)
* 做到这一步，浏览器端插件设置算是完成了，记住点击pan插件，默认蓝色图标——表示“自动代理”，绿色——“全局代理”，灰色——“禁用代理”。下面是xx-net端，请点击“取消全局代理”
![取消全局代理](https://raw.githubusercontent.com/yeahwu/wu/master/pan8.jpg)
* pan插件代理到此也就设置完成了，最后手动导入证书，就可以畅游网络了。

## 手动设置系统代理
当使用托盘菜单设置代理不成功时，你可以手动设置系统代理。具体内容请看：[[设置代理]]

# 手动导入证书
1. 点击右上角菜单按钮，选择浏览器的"首选项"
![火狐浏览器的菜单](https://cloud.githubusercontent.com/assets/6830787/10130653/d84bdc38-65fc-11e5-8748-9ac1847fed21.PNG)
2. 选择"高级"中的"证书"，选择"查看证书"，在证书管理器中选中"证书机构"，点击“导入”。
![火狐导入证书](https://cloud.githubusercontent.com/assets/6830787/10130719/518f32a2-65fd-11e5-987e-52c834581a77.PNG)
3. 在XX-Net文件夹下，找到 data\gae_proxy 目录下的 "CA.crt" 证书，导入即可。
![火狐导入证书2](https://cloud.githubusercontent.com/assets/6830787/10130747/8c5d95ea-65fd-11e5-905e-ab329dc4201e.PNG)
4. 在弹出的“下载证书”窗口中，选择"信任使用此CA标识的网站"，确定。
![“下载证书”窗口](https://cloud.githubusercontent.com/assets/6830787/10130813/02a7f06a-65fe-11e5-907b-e4b8b998e947.PNG)
5. 尝试访问[[https://www.google.com/]]或[[https://www.facebook.com/]]，检验证书是否导入成功。
![检验证书是否导入成功](https://cloud.githubusercontent.com/assets/6830787/10130827/1aeb0b9e-65fe-11e5-9815-5f95a3a44be5.PNG)

### 注（每次更新xx-net,保留data文件夹，不需要重新导入证书）