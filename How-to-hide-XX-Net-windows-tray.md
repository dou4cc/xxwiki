##如何隐藏XX-Net图标  

本来windows的系统托盘管理有隐藏功能，但是还是有部分用户不希望它出现。  
这里给出一个办法，让它完全不出现。  

###原理
launcher/x.x.x/???_tray.py 就是各种平台下的托盘实现代码；  
其中non_tray.py就是没有托盘。  

你拷贝non_tray.py覆盖对应平台的文件，就能达到目的。  
比如Windows平台：  

拷贝non_tray.py 覆盖 win_tray.py就可以了





