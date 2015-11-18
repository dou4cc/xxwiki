本页面将详细演示如何在一台全新的Windows7电脑上架设起Firefox+XXnet的上网渠道。（中英对照）

本文包含以下部分：

1. [[下载和安装Firefox浏览器|使用Firefox浏览器#下载和安装Firefox浏览器]]
2. [[获取和运行XX-Net|使用Firefox浏览器#%E8%8E%B7%E5%8F%96%E5%92%8C%E8%BF%90%E8%A1%8Cxx-net]]
3. [[设置代理|使用Firefox浏览器#设置代理]]
4. [[手动导入证书|使用Firefox浏览器#手动导入证书]]

# 下载和安装Firefox浏览器
## 下载
* 首先打开火狐官网下载浏览器：[[https://www.mozilla.org/zh-CN/firefox/new/]]。

除非官网无法访问，否则**不应该**从其他渠道下载。
![火狐官网](https://cloud.githubusercontent.com/assets/6830787/10131216/37b25298-6601-11e5-97c5-13d7c0f93137.PNG)

* 简体中文版的Firefox浏览器针对大陆用户作出了一些特殊设置，如果你不喜欢这个“大陆定制版”的火狐，你可以在[[https://www.mozilla.org/en-US/firefox/new/]]下载英文版。
![火狐官网英文](https://cloud.githubusercontent.com/assets/6830787/10131240/6afef976-6601-11e5-96af-4ad685eab8ea.PNG)

* 你也可以在“[所有系统和语言](https://www.mozilla.org/en-US/firefox/all/)”页面找到所有支持的语言和操作系统。

## 安装
### 使用在线安装器安装
* 一般来说，你下载的是一个几百KB大小的“在线安装器”。开始安装时，你可以点击“选项”，在其中进行一些设置。画红线的部分建议您斟酌。
![在线安装器安装](https://cloud.githubusercontent.com/assets/6830787/10131336/1ef80a94-6602-11e5-90ad-ee301e42e0a7.PNG)
![在线安装器安装选项](https://cloud.githubusercontent.com/assets/6830787/10131293/c7b2aec4-6601-11e5-95a9-637b85013003.PNG)
* 接下来安装程序会自动下载完整安装包。如果下载失败，建议前往“[所有系统和语言](https://www.mozilla.org/en-US/firefox/all/)”页面下载完整安装包。
![自动下载](https://cloud.githubusercontent.com/assets/6830787/10131326/0bdb5998-6602-11e5-9f6c-0dcf7e032f87.PNG)
* 安装完成后，程序会询问您是否要从其他浏览器中导入资料。您可以自行决定是否导入。

![导入资料](https://cloud.githubusercontent.com/assets/6830787/10131375/7330f5a8-6602-11e5-831d-e7c92213f80a.PNG)

### 使用完整安装包安装
* 在“[所有系统和语言](https://www.mozilla.org/en-US/firefox/all/)”页面下载的多是完整安装包。完整安装包将会跳过下载这一过程。运行安装包时可能会跳出警告，点击“运行”即可。

![警告](https://cloud.githubusercontent.com/assets/6830787/10131402/a4363082-6602-11e5-84a1-81b8de5f50f5.PNG)

* 如果你不想安装“静默更新服务”，请选择“自定义安装”，否则一路下一步即可。

![自定义安装](https://cloud.githubusercontent.com/assets/6830787/10131437/d57f59d4-6602-11e5-8e79-00c5fc3bf51b.PNG)

* 安装完成后，程序会询问您是否要从其他浏览器中导入资料。您可以自行决定是否导入。

![导入资料](https://cloud.githubusercontent.com/assets/6830787/10131375/7330f5a8-6602-11e5-831d-e7c92213f80a.PNG)

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
## 简单方法
启动XX-Net后，右下角会出现[[托盘图标|托盘右键菜单]]。右键单击托盘图标，点击“全局PAC智能代理”即可。

![托盘右键菜单](https://cloud.githubusercontent.com/assets/6830787/10132436/07a149f8-6609-11e5-8e1b-1dbe9336b226.PNG)

## 安装和使用代理切换插件
（待补充）

## 手动设置浏览器代理
（待补充）

菜单 - 选项 - 高级 - 网络 - 设置，勾选自动代理设置，输入：http://127.0.0.1:8086/proxy.pac

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