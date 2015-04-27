Block是1.11.2新增的保护机制中的一部分

## 保护机制
原因是连接某些ip被设为蜜罐，被探测到后，导致短时被封。  
内部一方面需要将这些ip设置为黑名单，另一方面，需要暂停联网一段时间。  


## 如果长期在Block倒计时状态
建议您看看XX-Net/data/goagent/bad_ip2.txt  
如果已经有七八条，那么建议您将这个文件的内容，以及您所在的地区以及网络状态提交到Issue  
例子：https://github.com/XX-net/XX-Net/issues/247