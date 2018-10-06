## 登录Google帐户 
https://www.google.com/ncr 

若无帐户，需注册，若注册失败，可能需要更换注册环境 （使用不同的代理/VPN， 不同的终端/浏览器）

## 创建AppID
1. 打开https://console.cloud.google.com/start ，点击`选择项目`，然后点击`创建项目`  
![Create_My_Project_1](https://cloud.githubusercontent.com/assets/19320102/26750556/af503ee2-4858-11e7-811b-30367691d912.png)
![Create_My_Project_2](https://cloud.githubusercontent.com/assets/19320102/26750550/6abaaed4-4858-11e7-8386-e07f0391325f.png)
2. 输入项目名称后，会自动帮你匹配可用ID，然后左击`创建`(请细读此教程底部[说明](#说明))  （注意：不要使用带有个人信息的名称）
![](https://user-images.githubusercontent.com/31188782/31053682-abce8a2c-a6d5-11e7-919c-c6f57fa9d06e.JPG)

## 设置AppID的App引擎 
**注意**：如果图形界面始终无法正确显示，可以尝试使用云端 Shell 来完成设置，参考[旧版 Wiki](https://github.com/XX-net/XX-Net/wiki/how-to-create-my-appids/b7e7d1ea13f5d8c578fbe7b1a16240bc4494eb45)。
1. 访问APP引擎信息中心， https://console.cloud.google.com/appengine/start?project=你的项目id

    ![](https://user-images.githubusercontent.com/31188782/31053684-abff5224-a6d5-11e7-9fa2-8ec6f785e6eb.JPG)

2. 选择一种语言--Python

    ![](https://user-images.githubusercontent.com/31188782/31053685-ac0ee2fc-a6d5-11e7-9fe1-512ce35ae0ed.JPG)

3. 选择区域，默认us-central即可（部分地区可以点选日本服务器，看不到地图的请选择全局代理或者更换梯子）

    ![](https://user-images.githubusercontent.com/31188782/31053686-ac15ad6c-a6d5-11e7-868b-b04f76fabf76.JPG)

4. 等待后台完成初始化配置，然后[打开XX-Net](http://127.0.0.1:8085/?module=gae_proxy&menu=deploy)开始[部署服务端的操作](https://github.com/XX-net/XX-Net/wiki/how-to-create-my-appids#%E9%83%A8%E7%BD%B2%E6%9C%8D%E5%8A%A1%E7%AB%AF)
    ![](https://user-images.githubusercontent.com/31188782/31053687-ac1721d8-a6d5-11e7-9d44-74c9797d6ae7.JPG)
![https://raw.githubusercontent.com/Alvin9999/PAC/master/appid6.png](https://user-images.githubusercontent.com/31188782/31576639-79cd52a4-b131-11e7-94c3-b2620103c79b.png)
## 部署服务端 
### XX-net更新不需要重新部署服务端，除非XX-Net升级说明中提到“升级服务端功能代码”
1. 打开XX-Net的设置页，切换到`部署服务端`http://127.0.0.1:8085/?module=gae_proxy&menu=deploy
2. 输入AppID后，点击打开Show Debug Log

    左击`开始部署`，会弹出授权窗口 （如果点击按钮部署不成功，请[参考脚本部署](https://github.com/XX-net/XX-Net/tree/master/code/default/gae_proxy/server)）
![3-Deploy.png](https://cloud.githubusercontent.com/assets/5118705/19356731/61e3b1ca-91a1-11e6-85b3-c4e034d99d65.png)
3. 左击`Allow`，然后就会进行服务端的部署  
![4-RequestForPermission.png](https://cloud.githubusercontent.com/assets/5118705/19356129/501fa69e-919f-11e6-9b7a-549e4a0151de.png)
4. 等待成功部署（根据网络情况和appid数量时间不定），日志会显示部署过程
![3-Deploy.png](https://cloud.githubusercontent.com/assets/5118705/19356731/61e3b1ca-91a1-11e6-85b3-c4e034d99d65.png)


## 配置AppID
1. 部署完成后，切换到`配置`，输入部署好的AppID后左击`保存`  
![5-Config.png](https://cloud.githubusercontent.com/assets/5118705/19356467/884aaba8-91a0-11e6-9f45-4d4648510d64.png)
1. 切换到`状态`来确认状态  
[](https://cloud.githubusercontent.com/assets/5118705/19358167/87d799a4-91a7-11e6-8e1c-ee29c53ae18e.png)
![6-status.jpg](https://user-images.githubusercontent.com/31188782/30781783-f4d55a6c-a157-11e7-911a-617353c002fd.jpg)

## 如何判断appid部署成功：  
假设你的appid是 myid  

用浏览器通过GAE_Proxy代理访问 myid.appspot.com, 如果出现  
```
GoAgent 服务端已经在 xxxxxxx 升级到 3.3.1 版本, 请更新您的客户端。
```
这样的字眼，就说明部署成功，否则需要重新部署。  

# 说明 #
1. 每个AppID每天1G流量，一般每个Google帐户最多12个AppID
1. AppID一次部署，多端通用，你还可以将appid分享给不能注册gmail的朋友使用
1. AppID的数量只影响流量，不影响速度
1. AppID的名称中切勿带有个人信息，因为使用GAE代理时目标网站可以看到你的AppID
1. 若部署过程中始终无法弹出窗口 , 建议[使用ss部署服务端](https://github.com/jzp820927/Deploy_XXNET_Server)
1. 若部署一直失败，可以本地安装[Google Cloud SDK](https://cloud.google.com/sdk/)手动部署，参考[gcloud app deploy](https://cloud.google.com/sdk/gcloud/reference/app/deploy)，需要全局代理工具(如SS,OVPN)
1. AppID 可以被删除，确认删除后需停止访问和使用该 AppID，一段时间后（通常是一周）此 AppID 就会真正被删除并空出其占用的数量。