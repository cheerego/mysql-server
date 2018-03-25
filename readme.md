### Master
`https://blog.csdn.net/mycwq/article/details/17136001`
```
# 日志文件名  
log-bin = mysql-bin  
  
# 主数据库端ID号  
server-id = 1  
```
```
# 创建slave帐号slave，密码slave  
grant replication slave on *.* to 'slave'@'%' identified by '123456';  
  
# 更新数据库权限  
flush privileges;

# 查看master状况
show master status//将这里的值再下面的sql中执行
```



### Slave
```$xslt
# 主数据库端ID号  
server-id = 1  

# 执行同步命令，设置主数据库ip，同步帐号密码，同步位置  
change master to master_host='mysql-master',master_user='slave',master_password='slave',master_log_file='master-bin.000009',master_log_pos=196;

# 开启同步功能  
start slave; 

show slave status
需要slave_io_runing和slave_sql_runing都是Yes

```
