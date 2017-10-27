最近翻不了墙实在郁闷，然后看了说开启IPV6能扫到IP,偏偏mac开启ipv6资料很少，最近上知乎看到一个答案，关于清华大学内网用ipv6上网的问题，大致思路就是ipv4连上isatap服务器，然后这个服务器根据他的ipv6前缀+你的ip实现ipv6通信,可是网络原理不是太懂，无法深入研究，一直没试成功，希望大家完善一下，做出mac内网开启ipv6通信的教程
============================================================================
#!/bin/sh
PASSWORD="your password"
isatap_adr="isatap address"
isatap_adr_v6_perfix="isatap address ipv6 perfix"
echo $PASSWORD | sudo -S route delete -inet6 default
echo $PASSWORD | sudo -S ifconfig gif0 destroy
lan_ip="$(echo $myip | awk '{print $2}')"
if [ -n "$lan_ip" ]; then
echo "IP = ${lan_ip}"
echo $PASSWORD | sudo -S ifconfig gif0 create
echo $PASSWORD | sudo -S ifconfig gif0 tunnel $lan_ip $isatap_adr
echo $PASSWORD | sudo -S ipconfig set gif0 MANUAL-V6 $isatap_adr_v6_perfix:$lan_ip 64
echo $PASSWORD | sudo -S route add -inet6 ::/0 -interface gif0
else
echo "No IP"
fi