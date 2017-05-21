```shell
关闭命令：  service iptables stop
永久关闭防火墙：chkconfig iptables off
两个命令同时运行，运行完成后查看防火墙关闭状态
service iptables status

# 打开相关端口
sudo iptables -I INPUT -s 0/0 -p tcp --dport 2181 -j ACCEPT
```