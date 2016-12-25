1. 在终端下使用会出错，两个方面
  1. 不能和proxychains配合使用

  ~~2. 设置好终端代理的环境变量后，url中不加 http:// 或 https:// 会访问不到网页，例子~~
     
  ~~export http_proxy=http://127.0.0.1:8087~~

  ~~export https_proxy=$http_proxy~~

  ~~curl www.google.com~~

     在Archlinux中使用yaourt命令安装软件，也会出错  
     相比之下，goproxy可以

2. 和goproxy相比，xx-net下载大文件（90M以上）容易断开
