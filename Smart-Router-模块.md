### 特性

- 墙内/墙外**自动切换**
- 实现在本地的DNS服务，通过在服务器上远程解析DNS，**避免DNS污染**
- 支持解析IPv4/IPv6
- **无需**特别设定DNS，模块开启后会自动绑定当前DNS地址

### 使用

- 在 `系统` - `配置` - `模块管理` 中启用 `Smart Router` 模块

- 模块监听于**SOCKS5@127.0.0.1:8086**

- 配置SwitchyOmega或相应的代理设置

- 模块会优先尝试直连目标服务器，再尝试使用GAEProxy，最后再尝试X-Tunnel

  可于 `SMART ROUTER` - `配置` - `通用` 设置

### 参考

- [3.9.3版本状态页“请检查浏览器代理设置”且双Fail的解决办法](https://github.com/XX-net/XX-Net/issues/9330)