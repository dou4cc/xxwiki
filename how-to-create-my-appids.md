# 登录Google帐户 #
https://www.google.com/ncr (若无帐户，需注册，若注册失败，可能需要更换线路或[梯子](https://wsgzao.github.io/post/fq))  

# 创建AppID #
1. 打开https://console.developers.google.com ，左击顶部`Project`，然后左击`创建项目`  
![1-CreateProject.png](https://cloud.githubusercontent.com/assets/5118705/19354947/1f4ae8ac-919b-11e6-9cc8-e0a589080de2.png)  
2. 输入项目名称后，会自动帮你匹配可用ID，然后左击`创建`(请细读此教程底部[说明](#说明))  
![2-CreateProject.png](https://cloud.githubusercontent.com/assets/5118705/19355039/7080b8a0-919b-11e6-89f4-34b649975804.png)  
3. 2016年12月后新注册用户部署AppID出现404错误的请转至`设置AppID的App引擎`解决相应问题

# 设置AppID的App引擎 #
1. 打开https://console.cloud.google.com/home/ (Google Cloud Platform)，可在左上角选择对应AppID
2. 在页面顶端中部搜索栏输入`App 引擎`回车进入App引擎管理界面
3. 在弹出的“欢迎使用App引擎”界面的左侧点击`选择一种语言`，选择`Python` (解决方案最先源于https://github.com/XX-net/XX-Net/issues/4720)
4. 在“你想在哪里提供自己的应用？”界面，更改`选择位置`为`us-central`


  以上方法为老方法,

##  [因GAE升级，设置AppID的App引擎需要用新的方法](https://github.com/XX-net/XX-Net/issues/4973)

1.进入 https://console.cloud.google.com/start ，点击 Project 、创建项目，记下您的项目id，点击创建。

![default](https://cloud.githubusercontent.com/assets/25559628/22777761/3adf4de0-eeef-11e6-89ac-9967809eee0b.png)

2.点击搜索框右边的按钮激活云端shell，页面底部会出现黑底白字，输入 gcloud config set project 23333 ，将前面的23333替换为您的项目id ，按下键盘的enter键，然后输入 gcloud beta app create --region us-central ，再按一次enter。

3.当底部出现 Success! The app is now created. Please use 'gcloud app deploy' to deploy your first app. 时，创建appid成功。此时可以重复前面两步，创建更多的appid

# 部署服务端 #
1. 打开XX-Net的设置页：http://127.0.0.1:8085 ，切换到`部署服务端`
2. 输入AppID后，左击`开始部署`，会弹出授权窗口  
![3-Deploy.png](https://cloud.githubusercontent.com/assets/5118705/19356731/61e3b1ca-91a1-11e6-85b3-c4e034d99d65.png)
3. 左击`Allow`，然后就会进行服务端的部署  
![4-RequestForPermission.png](https://cloud.githubusercontent.com/assets/5118705/19356129/501fa69e-919f-11e6-9b7a-549e4a0151de.png)
4. 部署完成后，切换到`配置`，输入部署好的AppID后左击`保存`  
![5-Config.png](https://cloud.githubusercontent.com/assets/5118705/19356467/884aaba8-91a0-11e6-9f45-4d4648510d64.png)
5. 切换到`状态`来确认状态  
![6-Status.png](https://cloud.githubusercontent.com/assets/5118705/19358167/87d799a4-91a7-11e6-8e1c-ee29c53ae18e.png)

# 说明 #
1. 每个AppID每天1G流量，一般每个Google帐户最多12个AppID
2. AppID的数量只影响流量，不影响速度
