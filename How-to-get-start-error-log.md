## 如何解决启动问题  

如果启动有问题，就无法看状态页和日志，无法分析问题，怎么办？  
这里给出分析问题的途径：start.bat/start.sh  

### Windows系统  
  * 方法1 双击 start.bat  
  * 方法2 打开cmd运行（XX-Net路径为D:\Tools\XX-Net）

      > "D:\Tools\XX-Net\code\default\python27\1.0\python.exe"  "D:\Tools\XX-Net\code\default\launcher\start.py"

     或者
     > "D:\Tools\XX-Net\code\default\python27\1.0\pythonw.exe"  "D:\Tools\XX-Net\code\default\launcher\start.py"

### Mac和Linux平台  
  1. 打开命令行终端窗口  
  1. 切换到XX-Net目录  
  1. 执行start.sh  

### Windows系统其他解决办法      
* 方法1 关闭xx-net, 任务栏右键"启动任务管理器"-找到pythonw.exe-结束进程.        
* 方法2 重新下载对应版本解压, 将原来在用的XX-Net/data整个目录复制到新版本下. 双击start快捷方式.

### 如果还不能解决, 请反馈到：  
https://github.com/XX-net/XX-Net/issues  
https://groups.google.com/forum/#!forum/xx-net  
  
把异常日志、操作系统等情况粘贴上去。