# ansible_grafana-zabbix   

## Environment
・CentOS7 2core 3GB   
・zabbix-server-3.0.13  
・grafana-server-4.6.3  
・php7.1  
・h2o 2.2.4  
・MariaDB 10.2

## Used  

I encourage zabbix to work with Grafana. Let zabbix be host registration only and see the graph at Grafana.  

## 1.dry-run
````
$ ansible-playbook -i hosts zabbix3.yml --ask-sudo-pass --check
````

## 2.run
````
$ ansible-playbook -i hosts zabbix3.yml --ask-sudo-pass
````
## 3.DB setting
・MariaDB

````
$ mysql_secure_installation
Y
````
・create DB and user

````
$ mysql -u root -p
> create database zabbix3;
> grant all privileges on zabbix3.* to zabbix3@localhost identified by 'adachinpo' ;
````

・first data in DB

````
$ zcat /usr/share/doc/zabbix-server-mysql-3.0.0/zabbix-server-mysql-3.0.13 |mysql -u zabbix3 -padachinpo -D zabbix3
````

## 4.zabbix_server.conf

````
DBName=zabbix3
DBUser=zabbix3
DBPassword=adachinpo
````

## 4.Grafana-Zabbix  

https://blog.adachin.me/wordpress/archives/7249  
