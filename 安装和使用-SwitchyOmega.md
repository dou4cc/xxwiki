SwichySharp已经改名字为SwitchyOmega，虽然Chrome商店里面可以下载和搜索，但是，下载完成安装以后，会被要求更新为SwitchyOmega（可以选择无视这个提醒），所以，下面的介绍和流程将直接展示SwitchyOmega的安装，当然，如果之前有SwichySharp的配置，也可以导入到SwitchyOmega中，他们没有冲突。

* 下面的安装步骤将告诉你，在你的网络还没有能力访问Chrome的网上运用商店的做法。

### 下载
* https://github.com/FelisCatus/SwitchyOmega/releases


### 安装
1. 打开Chrome；
2. 选择更多工具 ->拓展程序(在更老的chrome中，“设置”选项 -> 扩展程序)；
3. 将下载好的SwitchyOmega_Chromium.crx直接拖入到Chrome的页面内；

![installation](https://user-images.githubusercontent.com/14904657/31257672-624ac3da-aa6c-11e7-8318-795ad1e01707.jpg)

### 配置
> 
1. 安装好SwitchyOmega了以后，在弹出的窗口中点击“**导入/导出**”；

2. 选择“从备份文件恢复”，将XX-net目录下 SwitchyOmega文件夹->SwitchyOptions.bak（OmegaOptions.bak）导入进去；

### 使用

1. 在Chrome浏览器的工具栏中找到SwitchyOmega（一个圆环的图标）；

2. 点击下面的XX-net或 XX-net 自动切换模式，就可以实现代理了（一般选择自动切换模式）；

### 调试

Q：SwitchyOmega显示很多资源未加载？

A：有可能需要等一会，如果等待1分钟左右还没有反映，说明XX-net没有正常工作。

Q：XX-net与XX-net自动切换模式有什么区别？

A：如果设置为XX-net，表示全局代理，浏览器的所有的数据都通过XX-net传输；XX-net自动切换模式只会将在pac黑名单中的域名通过XX-net传输，其他流量自动选择直接连接