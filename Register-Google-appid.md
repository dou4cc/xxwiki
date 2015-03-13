注册Google帐号和appid教程

1. 注册 Google 帐号

  请填入手机号，为后面使用appengine做准备

   https://accounts.google.com/SignUp

2. 绑定手机号码

  https://security.google.com/settings/phone?pli=1

  没有绑定手机号码，是不能注册appengine服务的

3. 启用弱安全应用

  https://www.google.com/settings/security/lesssecureapps

  如果你没有启用2步登录验证，那么需要启用弱安全应用，否则无法上传appid

  如果你已经启用2步登录验证，那么不需要启用弱安全应用，而是设置应用专用密码：
  https://security.google.com/settings/security/apppasswords

  设备选"其他"，随便起个名词，比如GoAgent，点"生成"后，会出来一串密码。
  以后就拿这个密码来上传appid部署服务端

4. 申请AppEngine

  https://appengine.google.com/

  点“Create Application”，选一个自己喜欢的名字，只能是字母和-号组成，要检查名字有没有人用过，
  第一次申请，要勾选下面的License

5. 在WebUI里部署服务端
