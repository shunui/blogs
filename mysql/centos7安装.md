### 安装
```shell
# 下载mysql源安装包
wget http://dev.mysql.com/get/mysql57-community-release-el7-8.noarch.rpm

# 安装mysql源
yum localinstall mysql57-community-release-el7-8.noarch.rpm

# 检查mysql源是否安装成功
shell> yum repolist enabled | grep "mysql.*-community.*"
```
![image](https://github.com/shunui/shunui.github.io/blob/master/images/mysql/centos7installmysql.png)

## 安装mysql
```shell
安装
yum install mysql-community-server
启动MySQL服务
systemctl start mysqld
查看mysql的启动状态
systemctl status mysqld
设置开机启动
systemctl enable mysqld
systemctl daemon-reload

修改root本地登录密码
mysql安装完成之后，在/var/log/mysqld.log文件中给root生成了一个默认密码。通过下面的方式找到root默认密码，然后登录mysql进行修改：
grep 'temporary password' /var/log/mysqld.log
结果如下
```
![image](https://github.com/shunui/shunui.github.io/blob/master/images/mysql/temporary_password.png)
## 登陆
```shell
mysql -uroot -p
输入默认的密码
set password for 'root'@'localhost'=password('your_password');//注意此处密码需要大写字母，小写字母及数字

然后就需要设置防火墙了
iptables -I INPUT -p tcp --dport 3306 -j ACCEPT #放开3306端口的访问

mysql> create user 'sunhui'@'%' IDENTIFIED BY 'your_password'; #添加mysql账号
mysql> GRANT ALL ON *.* TO 'sunhui'@'%'; #设置mysql账号权限

具体参考了 http://www.linuxidc.com/Linux/2016-09/135288.htm
http://www.jb51.net/article/31850.htm
```