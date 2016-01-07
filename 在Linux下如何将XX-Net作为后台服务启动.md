#把XX-Net作为后台服务启动

有些时候，在没有安装桌面的linux服务器上，需要把xx-net作为后台服务启动,
这时候只需要在XX-Net目录下，用root权限运行xx_net.sh就可以了.

启动xx-net：

    sudo xx_net.sh start

  
停止xx-net：

    sudo xx_net.sh stop

  
重启xx-net:

    sudo xx_net.sh restart

  
日志保存在/var/log/messages文件中，用tail命令查看：

    tail -f /var/log/messages|grep xx_net
