##国际化翻译手册：
  
###简介：  
  国际化采用类似jinjia2的模板格式，在html 文件中可以发现下面这样的格式：  
  `{{ _("English version text") }}`  
  
  一般html 存放在 $module/web_ui/  
  
  而各语言的翻译放在 $module/lang/$LANG/LC_MESSAGES/messages.po  
  其中简体中文 $LANG 为zh_CN，正体中文在zh_TW。  
  因为采用英文为翻译字典的索引，找不到翻译的就是直接现实为英文。  
  
  
###新增一种语言
（以繁体为例）  
* 建立翻译文件  
  创建 $module/lang/zh_TW/LC_MESSAGES/ 目录  
  $module为各模块，目前包括：launcher、gae_proxy、x_tunnel  
`
mkdir -p launcher/lang/zh_TW/LC_MESSAGES/ gae_proxy/lang/zh_TW/LC_MESSAGES/ x_tunnel/lang/zh_TW/LC_MESSAGES/
`
  
* 把简体中文的翻译文件拷贝过去:  
`cp launcher/lang/zh_CN/LC_MESSAGES/messages.po launcher/lang/zh_TW/LC_MESSAGES/messages.po
cp gae_proxy/lang/zh_CN/LC_MESSAGES/messages.po gae_proxy/lang/zh_TW/LC_MESSAGES/messages.po
cp x_tunnel/lang/zh_CN/LC_MESSAGES/messages.po x_tunnel/lang/zh_TW/LC_MESSAGES/messages.po
`
  
* 修改 $module/pybabel_update.sh  
    参考里面的样式，增加对应的语言  
  
* 修改 launcher/web_ui/config.html  
    在第10行增加一行新的语言选项  
  
###翻译  
  用文本编辑文件编辑各messages.po  
  
###根据html内容更新翻译文件  
  在开发中，需要更改、增加新的文字，修改html后，执行对应目录下的$module/pybabel_update.sh  
  可自动在po文件中更新字段  

###测试  
  刷新界面看效果  
