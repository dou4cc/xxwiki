文字版：https://github.com/XX-net/XX-Net/wiki/Register-Google-appid<br>
# 前期准备
## 注册 Google 帐号<br>
请填入手机号，为后面使用appengine做准备<br>
https://accounts.google.com/SignUp<br>
## 绑定手机号码<br>
https://security.google.com/settings/phone?pli=1<br>
没有绑定手机号码，是不能注册appengine服务的<br>
## 启用弱安全应用<br>
https://www.google.com/settings/security/lesssecureapps<br>
对于多数用户而言，你只需要启用弱安全应用，就可以上传appid<br>

注：如果你已经启用2步登录验证，那么不需要启用弱安全应用，而是设置应用专用密码： https://security.google.com/settings/security/apppasswords<br>
设备选"其他"，随便起个名词，比如GoAgent，点"生成"后，会出来一串密码。 以后就拿这个密码来上传appid部署服务端<br>

# 申请appid
1、打开 https://appengine.google.com/ ，你会看到下图的界面（当然你的列表是空的）
![](http://i4.tietuku.com/267f4562b6c80bf9.png)<br>
2、点击该界面中的“Create Application”按钮，会看到如下的界面
然后按照图中的指示进行操作即可
![](http://i4.tietuku.com/901c9f02abaedaf2.png)
![](http://i4.tietuku.com/b20cac394ec7356a.png)<br>

3、创建成功后，会出现一些提示信息，告诉你应用程序创建成功，当然这对于我们来说不重要
![](http://i4.tietuku.com/665c7a7854d658b2.png)<br>
4、打开 https://security.google.com/settings/security/apppasswords ，并且按照下图操作：
![](http://i4.tietuku.com/809d7ca3759acb5e.png)
![](http://i4.tietuku.com/2ce5a40a8a0f90b2.png)
![](http://i4.tietuku.com/09f7a94cbaf6b2ac.png)
![](http://i4.tietuku.com/6c120045abe36a1b.png)<br>

# 上传服务端
 - 提示：在部署之前，APPID是无法使用的，不要将他们填入到XX-Net的配置中。
1、打开http://127.0.0.1:8085/?module=goagent&menu=deploy ，按下图说明操作：
![](http://i4.tietuku.com/42cc5b145e4ccd76.png)
![](http://i4.tietuku.com/0252209010b5ad68.png)<br>
2、如果你成功做到这一步，那么恭喜你，你即将修成正果，只差最后一步。
打开http://127.0.0.1:8085/?module=goagent&menu=config ，然后老样子看图即可。
![](http://i4.tietuku.com/be7a1a71ab4ce795.png)<br>
3、当你点击“保存并重启”的那一刻，你就脱离了苦海，视频畅饮，没有任何限制<br>

# 一些说明
1、每个GAE应用每天限额流量1G，因此如果你不够用的话，可以多注册几个，我注册了12个，想想怎么也够用了，每天12G的流量必然是用不完了<br>
2、我所处的网络环境对于速度的响应是比较敏感的，可以达到我的带宽上限，在youtube上看1080P的视频没有任何问题。视网络环境的不同，也许你的情况会比我更好 也可能更差，请放平心态，这与软件无关。<br>
3、现在可以通过Google Developer Console创建GAE对象，要通过Google Developer Console创建，[请移步这里](https://console.developers.google.com/project)。该界面有繁体中文版，对于英文不好的同学可以尝试从这里操作。不过此处界面与上面介绍的界面存在差异，请根据相关提示自行操作。