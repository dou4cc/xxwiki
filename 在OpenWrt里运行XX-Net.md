
### 需要的条件:
安装python2.7运行环境和pyOpenSSL库。  
`opkg install python-pyopenssl`  

### 具体步骤：
登陆OpenWrt控制台  
拷贝XX-Net到OpenWrt  
`cd XX-Net`   
`./start.sh`  
  
### 远程访问状态管理页面
**允许远程访问Web界面：**  
修改 XX-Net/data/launcher/config.yaml  
  `modules:{`  
  ` launcher:{ allow_remote_connect:1 }`  
  
**允许GAE_proxy提供远程代理服务：**  
  修改 XX-Net/data/gae_proxy/manual.ini    
`[listen]`
`ip = 0.0.0.0
`  
重启XX-Net  
  
**浏览器中打开**
 http://OpenWrt的ip:8085  

### 远程下载、导入证书  
  在状态页中，有证书下载链接  
