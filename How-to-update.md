# 更新方法
> 每次更新前备份data文件夹，可以随时恢复到指定版本

## 手动更新(不推荐新手)

* 备份 __data__ 文件夹(__data__ 文件夹内保存了 appid,good_ip 等配置信息)

* 下载[__XX-Net-Release__](https://github.com/XX-net/XX-Net/releases)版本或者根据[__下载页面__](https://github.com/XX-net/XX-Net/blob/master/code/default/download.md)提示进行版本选择

* 解压缩下载的文件

* 将 __data__ 文件夹放到解压缩目录

* 更新完成

## [自动更新](https://github.com/XX-net/XX-Net/wiki/Auto-update)

### 自动升级的类型

为了方便升级，同时适应不同用户的需要，提供几种不同的升级方式：  

+ 不检查升级  
  完全不检查升级  

+ 长期稳定版  
  不定期发布，一般是在有重大性能突破时才发送升级  

+ 稳定版  
  一般github上会维护一份[[稳定版|https://github.com/XX-net/XX-Net#下载链接]]，供新用户下载。  
  测试版经过3天到一周，没有收到反馈大问题，就会作为稳定版  

+ 测试版  
  一般发新版，需要经过[[测试版|https://github.com/XX-net/XX-Net#下载链接]]阶段，给遇到具体问题、热心参与测试的网友测试，  
  接受反馈


自动检查更新频率：每次启动时，以及启动后每24小时


### 如何设置

* 启动XX-Net后，打开http://127.0.0.1:8085/?module=launcher&menu=config
![升级管理](https://cloud.githubusercontent.com/assets/6830787/8200348/44002270-14f6-11e5-8bd9-62d27af83773.PNG)

* 单击“升级管理”，“自动升级到”选项会出现
![设置升级选项](https://cloud.githubusercontent.com/assets/6830787/8200384/dacf9b54-14f6-11e5-9953-6488495b3a63.PNG)

* 在下拉菜单中进行选择，窗口上方会出现“设置已成功保存.”字样，设置完成。
![设置成功保存](https://cloud.githubusercontent.com/assets/6830787/8200383/da77c618-14f6-11e5-8b2a-4fb9385d3437.PNG)

## 使用 Git 更新(不推荐新手)

* 等待编写