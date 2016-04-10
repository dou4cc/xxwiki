注册Google帐号和appid教程  
**废弃

推荐[图文版](https://github.com/XX-net/XX-Net/wiki/how-to-create-my-appids)**

1. 注册 Google 帐号

  请填入手机号，为后面使用appengine做准备

   https://accounts.google.com/SignUp

2. 绑定手机号码

  https://security.google.com/settings/phone?pli=1

  没有绑定手机号码，是不能注册appengine服务的


3. 申请AppEngine  

  https://console.developers.google.com/project

  点“建立专案”，选一个自己喜欢的名字，只能是字母和-号组成，要检查名字有没有人用过，
  第一次申请，要勾选下面的License

4. 设置部署的权限

  如果你没有启用2步登录验证，请启用弱安全应用
  https://www.google.com/settings/security/lesssecureapps


  如果你已经启用2步登录验证，请设置应用专用密码：
  https://security.google.com/settings/security/apppasswords

    设备选"其他"，随便起个名词，比如GoAgent，点"生成"后，会出来一串密码。
    以后就拿这个密码来上传appid部署服务端

5. 在WebUI里部署服务端
  
  http://127.0.0.1:8085/?module=goagent&menu=deploy

6. 配置使用新的appid
  
  http://127.0.0.1:8085/?module=goagent&menu=config