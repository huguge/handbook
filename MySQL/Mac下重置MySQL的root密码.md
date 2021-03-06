
# Mac下重置Mysql的root密码


```bash
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)
# 或者
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)
```

使用 `mysql -uroot -p` 登录进去。

## 停止 mysql server

 `系统偏好设置` > `MySQL` > `Stop MySQL Server`


## 终端，输入进入安全模式

```
sudo /usr/local/mysql/bin/mysqld_safe --skip-grant-tables
```

## 新开终端，输入


```bash
sudo /usr/local/mysql/bin/mysql -u root
# 输入 Mac 系统用户密码后，
# 直接敲回车进入 mysql 终端，输入：
mysql> FLUSH PRIVILEGES;
mysql> ALTER USER 'root'@'localhost' IDENTIFIED BY 'MyNewPass';
# 输入 \q 退出 mysql 终端
\q
```

## 重启MySQL.

```bash
ps -ef | grep mysql
```

通过上面命令查看进程编号。  

通过`sudo kill 93`杀掉`mysql`进程  

`系统偏好设置` > `MySQL` > `Start MySQL Server`


更快捷的重启  

```bash
sudo /usr/local/mysql/support-files/mysql.server start

```


# 官网参考


- [How to Reset the Root Password](http://dev.mysql.com/doc/refman/5.7/en/resetting-permissions.html)