### GoAgent配置文件说明：
 
- 一般用户使用Web UI进行配置即可，不必手动修改配置文件。

- 3.10.6 后的版本，配置文件采用json格式。   
  文件在`data/gae_proxy/config.json`

- 建议使用Notepad2或Notepad++等支持代码高亮的编辑器。

- 里面条目的默认值，请参考：  
`code/default/gae_proxy/local/config.py`  
以及  
`code/default/python27/1.0/lib/noarch/front_base/config.py`


- json格式，可以自行搜索。  
  注意最后一项后面没有逗号。


### 简单举例：
1. 自定义appid的密码
```
{
  "GAE_APPIDS" : ["xx-net-1", "xx-net-2"],
  "GAE_PASSWORD": "xxxx"
}
```

2. 自定义监听ip和端口
```
{
  "listen_ip": "0.0.0.0",
  "listen_port": 8088
}
```

3. 修改最大ip数
```
{
  "max_good_ip_num": 1000
}
```




补充：[为其他设备提供代理服务](https://github.com/XX-net/XX-Net/wiki/%E4%B8%BA%E5%85%B6%E4%BB%96%E8%AE%BE%E5%A4%87%E6%8F%90%E4%BE%9B%E4%BB%A3%E7%90%86%E6%9C%8D%E5%8A%A1)