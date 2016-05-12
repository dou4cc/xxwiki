文字版：https://github.com/XX-net/XX-Net/wiki/Register-Google-appid<br>
#如何注册自己的appid
# 前期准备
## 注册 Google 帐号<br>
为后面使用appengine做准备，会需要手机号<br>
https://accounts.google.com/SignUp<br>
## 绑定手机号码<br>
https://myaccount.google.com/phone?pli=1<br>
没有绑定手机号码，是不能注册appengine服务的<br>
## 启用弱安全应用<br>
https://www.google.com/settings/security/lesssecureapps<br>
对于多数用户而言，你只需要启用弱安全应用，就可以上传appid<br>

(注：如果你已经启用2步登录验证，那么不需要启用弱安全应用，而是设置应用专用密码： https://security.google.com/settings/security/apppasswords<br>
设备选"其他"，随便起个名词，比如GoAgent，点"生成"后，会出来一串密码。 以后就拿这个密码来上传appid部署服务端)<br>

# 申请appid
1、打开 https://console.cloud.google.com ，你会看到下图的界面  
![](https://cloud.githubusercontent.com/assets/13873808/15204523/bc97f930-1840-11e6-8c58-7674120cccfb.png)<br>
2、点击该界面中的“Create a project”按钮，会看到如下的界面  
![](https://cloud.githubusercontent.com/assets/10395528/12047789/67b97c2e-af0c-11e5-8fac-e818836f9e61.png)<br>  
  1 填入你希望的appid  
    下面的appid会显示实际给你的appid，建议字母后面加上3-4个数字  
  2 点选不要发邮件   
  3 点同意  
  4 提交  
# 设置部署权限  
   如果你没有启用2步登录验证，请启用弱安全应用   
       https://www.google.com/settings/security/lesssecureapps  
  
   如果你已经启用2步登录验证，请设置应用专用密码：  
打开 https://security.google.com/settings/security/apppasswords ，并且按照下图操作：  
![](http://i4.tietuku.com/809d7ca3759acb5e.png)
![](http://i4.tietuku.com/2ce5a40a8a0f90b2.png)
![](http://i4.tietuku.com/09f7a94cbaf6b2ac.png)
![](http://i4.tietuku.com/6c120045abe36a1b.png)<br>

# 上传服务端
 - 提示：在部署之前，APPID是无法使用的，不要将他们填入到XX-Net的配置中。    
1、打开http://127.0.0.1:8085/?module=gae_proxy&menu=deploy

2、在框中输入你已经申请的AppID, “批量部署多个AppID, 请用|分割”
![deploy](https://cloud.githubusercontent.com/assets/14904657/14408865/469f6342-ff38-11e5-871d-99ae5282b5c4.png)

3、部署完成

4、打开http://127.0.0.1:8085/?module=gae_proxy&menu=config，填入你的AppID。多个AppID, 请用|分割。
![](http://i4.tietuku.com/be7a1a71ab4ce795.png)<br>

4、当你点击“保存并重启”的那一刻，你就脱离了苦海，视频畅饮，没有任何限制<br>

# 一些说明
1、每个GAE应用每天限额流量1G，每个google帐号限制12个AppID<br>
2、appid只影响流量，不影响速度<br>