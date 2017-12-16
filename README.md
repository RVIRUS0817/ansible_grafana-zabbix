ansibleでZabbix-server3.0.13の環境セットアップ

# 環境
・CentOS7  
・zabbix-server-3.0.13  
・php7.1  
・h2o 2.2.4  
・MariaDB 10.2

## 1.dry-run
````
$ ansible-playbook -i hosts zabbix3.yml --ask-sudo-pass --check
````

## 2.run
````
$ ansible-playbook -i hosts zabbix3.yml --ask-sudo-pass
````
## 3.DBの設定
・MariaDB初期設定

````
$ mysql_secure_installation
全部Y
````
・DB作成と権限

````
$ mysql -u root -p
> create database zabbix3;
> grant all privileges on zabbix3.* to zabbix3@localhost identified by 'adachinpo' ;
````

・初期データ投入

````
$ zcat /usr/share/doc/zabbix-server-mysql-3.0.0/zabbix-server-mysql-3.0.13 |mysql -u zabbix3 -padachinpo -D zabbix3
````

## 4.zabbix_server.confに追記

````
DBName=zabbix3
DBUser=zabbix3
DBPassword=adachinpo
````
