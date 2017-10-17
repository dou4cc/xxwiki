本页面将详细演示如何在一台全新的Windows7电脑上架设起Chrome+XX_Net的上网渠道。

本文包含以下部分：

1. [[下载和安装Chrome浏览器|使用Chrome浏览器#下载和安装Chrome浏览器]]
2. [[获取和运行XX-Net|使用Chrome浏览器#%E8%8E%B7%E5%8F%96%E5%92%8C%E8%BF%90%E8%A1%8Cxx-net]]
3. [[设置代理|使用Chrome浏览器#设置代理]]
4. [[手动导入证书（备选）|使用Chrome浏览器#%E6%89%8B%E5%8A%A8%E5%AF%BC%E5%85%A5%E8%AF%81%E4%B9%A6%E5%A4%87%E9%80%89]]

# 下载和安装Chrome浏览器
## 下载
* Chrome官网下载地址：https://www.google.cn/intl/zh-CN/chrome/browser/desktop/index.html
* 虽然是CN网站，但是挂了"google"这个敏感词，所以会经常抽风。那么下面就多提供几个下载地址。

  - 浏览迷网站：http://liulanmi.com/  
  - 新浪软件中心：http://tech.sina.com.cn/down/  
  - 卡饭chrome区：http://bbs.kafan.cn/forum-214-1.html  
  - chrome离线包：https://api.shuax.com/tools/getchrome

上面几个网站搜索或者点击chrome浏览器下载，建议用“Stable（稳定版）”

## 安装
* 为了不侮辱大家的智商，安装Chrome就不详解了，一路“确定”就ok了

# 获取和运行XX-Net
* 打开[[https://github.com/XX-net/XX-Net/blob/master/code/default/download.md]]，选择稳定版下载.
![下载链接](https://cloud.githubusercontent.com/assets/13873808/16293362/eaa5e1ee-394b-11e6-8660-04d84892c8d2.png)
* 下载完毕后解压缩文件夹，运行文件夹中start.vbs文件
![运行](https://cloud.githubusercontent.com/assets/13873808/16293263/150b6cc0-394b-11e6-9b84-9428caa6f780.png)
* 如果弹出管理员权限请求（用户账户控制），请允许。

![管理员权限请求](https://cloud.githubusercontent.com/assets/6830787/10132435/079df852-6609-11e5-824d-06c8c4bb929b.PNG)

* 首次运行可能会弹出防火墙警告，请允许访问。

![防火墙警告](https://cloud.githubusercontent.com/assets/6830787/10131885/feb9afa4-6605-11e5-82c5-b2f15eb2ebd2.PNG)

# 设置代理
## 方案一：简单方法
* 启动XX-Net后，右下角会出现[[托盘图标|托盘右键菜单]]。右键单击托盘图标，点击“全局PAC智能代理”即可。
![托盘右键菜单](https://cloud.githubusercontent.com/assets/6830787/10132436/07a149f8-6609-11e5-8e1b-1dbe9336b226.PNG)

## 方案二：安装和使用代理切换插件
* 打开XX-Net/SwitchyOmega文件夹；打开浏览器的扩展程序页面 chrome://extensions 。把SwitchyOmega.crx文件拖放到浏览器扩展程序页面安装。如图
![SwitchyOmega](https://raw.githubusercontent.com/yeahwu/recycle-bin/master/xx0.JPG)
![安装扩展程序](https://raw.githubusercontent.com/yeahwu/recycle-bin/master/xx1.JPG)
* 添加扩展程序
![添加扩展程序](https://raw.githubusercontent.com/yeahwu/recycle-bin/master/xx2.JPG)
* 跳过教程
![教程](https://raw.githubusercontent.com/yeahwu/recycle-bin/master/xx3.JPG)
* 导入bak文件
![导入／导出](https://raw.githubusercontent.com/yeahwu/recycle-bin/master/xx4.JPG)
![从备份文件中恢复](https://github.com/yeahwu/recycle-bin/blob/master/xx5.JPG)
* 点击从备份文件中恢复后，找到XX-Net/SwitchyOmega/OmegaOptions.bak文件，点击打开
![bak文件](https://raw.githubusercontent.com/yeahwu/recycle-bin/master/xx5.5.JPG)
* 点击情景模式中的 GAE-Proxy自动切换 ,跳过教程
![教程](https://raw.githubusercontent.com/yeahwu/recycle-bin/master/xx6.JPG)
* 下拉点击“立即更新情景模式”
![更新情景模式](https://user-images.githubusercontent.com/31188782/31662044-7c88c902-b36f-11e7-890b-2e10dddadac1.png)

* 点击SwitchyOmega，切换成“GAE-Proxy自动切换”，如果使用的是X-Tunnel或SS，请点击“X-Tunnel自动切换”。
![切换代理](https://user-images.githubusercontent.com/31188782/31662260-33c95e42-b370-11e7-87b9-d9a6985cb1c9.png)
* 到此，浏览器端设置代理也就完成了，还需最后一步，把XX-Net切换为“取消全局代理”，就可以畅游网络了。

![取消全局代理](https://raw.githubusercontent.com/yeahwu/wu/master/pan8.jpg)

# 手动导入证书（备选）
* 正常情况下，Chrome的证书都是自动导入的。手动导入证书，只是非正常情况下才会用到，比如遇到“您打开的链接不是私密连接”，这个时候就需要手动导入证书了。
* 点击浏览器 菜单-设置-下翻点击“显示高级设置”-点击“管理证书”
![管理证书](https://raw.githubusercontent.com/yeahwu/recycle-bin/master/zs0.JPG)
* 选择“受信任的根证书颁发机构”这一栏，然后点击导入
![导入证书](https://raw.githubusercontent.com/yeahwu/recycle-bin/master/zs1.JPG)
![下一步](https://raw.githubusercontent.com/yeahwu/recycle-bin/master/zs2.JPG)
* 点击浏览，然后定位到xx-net/data/gae_proxy文件夹，点击CA.crt文件，打开
![浏览](https://raw.githubusercontent.com/yeahwu/recycle-bin/master/zs3.JPG)
![导入CA](https://raw.githubusercontent.com/yeahwu/recycle-bin/master/zs4.JPG)
* 将证书存放在“受信任的根证书颁发机构”，点击下一步，完成
![存放](https://raw.githubusercontent.com/yeahwu/recycle-bin/master/zs5.JPG)
![完成](https://raw.githubusercontent.com/yeahwu/recycle-bin/master/zs6.JPG)
* 到此手动导入证书也就完成了。
