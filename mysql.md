
group_concat 문제발생시 my.cnf 에 아래 부분 추가 
```
[mysqld]
group_concat_max_len=15000
```

mysql service 재기동명령
```
service mysqld restart
```

utf8 설정 
```
[mysqld]
init_connect='SET collation_connection = utf8_unicode_ci'
init_connect='SET NAMES utf8'
character-set-server=utf8
collation-server=utf8_unicode_ci
skip-character-set-client-handshake
```

utf8 설정 확인
```sql
show variables like "%character%";show variables like "%collation%";
```
```sql
+--------------------------+----------------------------+
| Variable_name | Value |
+--------------------------+----------------------------+
| character_set_client | utf8 |
| character_set_connection | utf8 |
| character_set_database | utf8 |
| character_set_filesystem | binary |
| character_set_results | utf8 |
| character_set_server | utf8 |
| character_set_system | utf8 |
| character_sets_dir | /usr/share/mysql/charsets/ |
+--------------------------+----------------------------+
8 rows in set (0.00 sec)

+----------------------+-----------------+
| Variable_name | Value |
+----------------------+-----------------+
| collation_connection | utf8_unicode_ci |
| collation_database | utf8_unicode_ci |
| collation_server | utf8_unicode_ci |
+----------------------+-----------------+
```

### mysql with docker 
```
docker run -v /d/docker_share/mysql:/home/mysql -d -e MYSQL_ROOT_PASSWORD=1234 -p 3306:3306 --name mysql_test mysql
docker exec -i -t mysql_test /bin/bash
```

### Mysqldump
```
mysqldump -uroot -p --port 3306 -t [db명]]  > c:\folder\file.sql
```

오류패스  
```
mysql -uroot  p --database [db명] -f < c:\folder\file.sql
```

정상
```
mysql -uroot -p --database [db명] < file.sql
```

## 비밀번호 변경
```
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY '1234'
flush privileges;
```
