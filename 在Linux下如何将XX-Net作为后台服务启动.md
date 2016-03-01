#把 XX-Net 作为后台服务启动

有些时候，在没有安装桌面的 Linux 服务器上，需要把 xx-net 作为后台服务启动,
这时候只需要在 XX-Net 目录下，用 root 权限运行 xx_net.sh 就可以了.

启动xx-net：

    sudo xx_net.sh start

  
停止xx-net：

    sudo xx_net.sh stop

  
重启xx-net:

    sudo xx_net.sh restart

  
日志保存在/var/log/messages文件中，用tail命令查看：

    tail -f /var/log/messages|grep xx_net

## 关于 Fedora

目前，主流发行版均使用 Systemd init 管理系统服务。 Fedora 用户可添加 [FZUG 源](https://github.com/FZUG/repo/wiki/%E6%B7%BB%E5%8A%A0-FZUG-%E6%BA%90)，安装 xx-net 并使用 systemd 管理。

启动xx-net：

    $ systemctl --user start xx-net

查看状态：

    $ systemctl --user status xx-net

停止xx-net：

    $ systemctl --user stop xx-net

使用 systemctl 用户模式管理，而无需用 root 权限运行，提高安全性。