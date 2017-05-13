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