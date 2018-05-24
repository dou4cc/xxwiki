## X_tunnel是XX-Net的新功能模块  
* 提供socks5代理特性，解决GAE证书问题  
  支持完整的SSL/HTTPS 加密通讯，支持非http协议。  
* 更多前端，更快更稳定  
  目前支持GAE, cloudflare, heroku  
  客户端根据速度，智能调度。  
* 更安全  
  流量混淆  
    通过流量分析，无法了解用户传输什么内容。  
  中间经过2跳，任意节点无法知道谁，在访问什么网站。  
  

## 使用方法

### 首先[下载XX-Net客户端](https://github.com/XX-net/XX-Net/blob/master/code/default/download.md)    
* 解压后点击 start.bat/start.vbs/start 运行    
* 点击xx图标，进入web页面      
* 左侧栏会有个 x_tunnel，点击 、首页、注册、登录。
* x-tunnel 服务器带宽流量需要购买，条件允许请支持项目。    

### 浏览器安装代理插件    
* 火狐用 pan 或者`autoproxy`(57版本之后的用switchOmega)
* chrome 用[SwitchyOmega](https://github.com/XX-net/XX-Net/wiki/%E5%AE%89%E8%A3%85%E5%92%8C%E4%BD%BF%E7%94%A8-SwitchyOmega)调用（[导入在线恢复文件](https://raw.githubusercontent.com/XX-net/XX-Net/master/SwitchyOmega/OmegaOptions.bak)，一键完成设置）


<img src="https://user-images.githubusercontent.com/31188782/30581444-bdbef186-9d52-11e7-9f25-e51486647340.JPG" height=250/>

* SwitchyOmega选择X_Tunnel自动切换模式   

支持的代理协议

| 代理协议 | 代理服务器 | 代理端口 |
|----------|------------|----------|
| SOCKS   | 127.0.0.1  | 1080     |
|HTTP      |127.0.0.1|1080|

### 最后一步
* 右键托盘图标，勾选“取消全局代理”    

### 高级技巧
* [指定服务器](X-Tunnel-use-special-server)
* [[修改监听端口|X_tunnel-Config-file]]

### 如何获得流量：
1. 每捐赠1个appid，奖励10G流量/2年

    https://github.com/XX-net/XX-Net/wiki/DonateAppid

    捐赠后给xxnet.dev@gmail.com发邮件，告知appid和你的x_tunnel account

2. 购买套餐：   
  
    |套餐| 价格|最高流量|
    |-----|-----|---|
    |季度 |$4.5  | 300G |
    |年度 |$15   | 1200G|

   条件允许的，请购买流量，以支持项目发展。  
   最高流量只是一个上限，保证大家足够用，套餐以有限时间为主。  
   我们鼓励您将流量分给朋友使用，但注意不要在QQ/微信中交流XX-Net。  

   可以用国内银行卡注册paypal，自动转换美元。   
   安全原因，目前不支持支付宝、微信支付。  


3. 参与项目的贡献，可在dev留x_tunnel account  

4. 推广X-Tunnel  
  https://github.com/XX-net/XX-Net/wiki/X-Tunnel-%E6%8E%A8%E5%B9%BF%E8%AE%A1%E5%88%92