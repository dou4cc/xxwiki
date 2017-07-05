# 登录Google帐户 #
https://www.google.com/ncr (若无帐户，需注册，若注册失败，可能需要更换线路或[梯子](https://wsgzao.github.io/post/fq))  

# 创建AppID #
1. 打开https://console.cloud.google.com/start ，点击`选择项目`，然后点击`创建项目`  
![Create_My_Project_1](https://cloud.githubusercontent.com/assets/19320102/26750556/af503ee2-4858-11e7-811b-30367691d912.png)
![Create_My_Project_2](https://cloud.githubusercontent.com/assets/19320102/26750550/6abaaed4-4858-11e7-8386-e07f0391325f.png)
2. 输入项目名称后，会自动帮你匹配可用ID，然后左击`创建`(请细读此教程底部[说明](#说明))  
![Create_My_Project_3](https://cloud.githubusercontent.com/assets/19320102/26750564/00414760-4859-11e7-910d-983dfdea17af.png)

# 设置AppID的App引擎 #
1. 点击`激活Google云端Shell`，点击`启动云端SHELL`进入Shell
![Create_My_Project_4](https://cloud.githubusercontent.com/assets/19320102/26750594/bb6ac110-4859-11e7-8d57-d5cf3a6b4e0a.png)
![Create_My_Project_5](https://cloud.githubusercontent.com/assets/19320102/26750604/df6bd4c8-4859-11e7-88a0-5cfc9fee94e0.png)
![Create_My_Project_6](https://cloud.githubusercontent.com/assets/19320102/26750642/815227c4-485a-11e7-81f7-d544f35650d3.png)
2. 在页面底部输入`gcloud config set project 项目ID`,按下键盘的enter键，然后输入 `gcloud beta app create --region us-central` ，再按一次enter。
![Create_My_Project_7](https://cloud.githubusercontent.com/assets/19320102/26750655/a038fc8a-485a-11e7-88ed-1fdb19f971ae.png)
![Create_My_Project_8](https://cloud.githubusercontent.com/assets/19320102/26750667/dcd4ca16-485a-11e7-8474-afac8dc25996.png)
![Create_My_Project_9](https://cloud.githubusercontent.com/assets/19320102/26750674/f2b29160-485a-11e7-8a4c-d1f5367c016f.png)
3. 当底部出现 Success! The app is now created. Please use 'gcloud app deploy' to deploy your first app. 时，创建appid成功。此时可以重复前面两步，创建更多的appid
![Create_My_Project_10](https://cloud.githubusercontent.com/assets/19320102/26750675/0b68f654-485b-11e7-982c-b9fcffca63cc.png)

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
3. 若部署过程中始终无法弹出窗口 , 建议[使用ss部署服务端](https://github.com/jzp820927/Deploy_XXNET_Server)
4. 若部署一直失败，可以安装[Google Cloud SDK](https://cloud.google.com/sdk/)，gcloud init设置代理，[gcloud app deploy](https://cloud.google.com/sdk/gcloud/reference/app/deploy)上传[gae文件夹](https://github.com/XX-net/XX-Net/tree/master/code/default/gae_proxy/server/gae)，在app.yaml中不要指定application和version

![deploy](https://ws1.sinaimg.cn/mw690/b64a58e3gy1fh9rhes8idj20i50fzwga.jpg)