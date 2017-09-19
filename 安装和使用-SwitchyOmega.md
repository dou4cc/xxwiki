SwichySharp已经改名字为SwitchyOmega，虽然Chrome商店里面可以下载和搜索，但是，下载完成安装以后，会被要求更新为SwitchyOmega（可以选择无视这个提醒），所以，下面的介绍和流程将直接展示SwitchyOmega的安装，当然，如果之前有SwichySharp的配置，也可以导入到SwitchyOmega中，他们没有冲突。

* 下面的安装步骤将告诉你，在你的网络还没有能力访问Chrome的网上运用商店的做法。

### 下载
* https://github.com/FelisCatus/SwitchyOmega/releases

下载以后Chrome会自动安装，如果失败了，请根据下面的方法手动安装。

### 安装
1. 打开Chrome；
2. 打开“设置”选项；
3. 点击**左上角**的“扩展程序”；
4. 将下载的SwitchyOmega.crx直接拖入到Chrome的页面内；

### 配置
> 
1. 安装好SwitchyOmega了以后，在安装扩展程序的页面找到SwitchyOmega，点击“选项”；

3. 点击**左边**的“导入导出选项”；

4. 选择从“备份文件恢复”，将XX-net目录下 SwitchyOmega文件夹->SwitchyOptions.bak导入进去；

### 使用

1. 在Chrome浏览器的工具栏中找到SwitchyOmega（一个圆环的图标）；

2. 点击下面的XX-net或 XX-net 自动切换模式，就可以实现代理了（一般选择自动切换模式）；

### 调试

Q：SwitchyOmega显示很多资源未加载？

A：有可能需要等一会，如果等待1分钟左右还没有反映，说明XX-net没有正常工作。

Q：XX-net，XX-net PAC和自动切换模式有什么区别？

A：如果设置为XX-net，表示全局代理，所有的数据都通过XX-net传输；XX-net PAC是代理自动配置，将不需要代理的网站进行直接访问；比如逛淘宝，看优酷很慢，可以选择XX-net PAC模式，这时候淘宝和优酷这种国内的网站就是直接访问；自动情境模式与GoAgent PAC的效果和目地一样，只是这个访问的选择交给了插件来决定，方便修改。