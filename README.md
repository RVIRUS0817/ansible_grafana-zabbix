#  用途
ansibleでZabbix-server3.0.13の環境セットアップ

# 環境  
CentOS7

## 1.dry-run
````
$ ansible-playbook -i hosts zabbix3.yml --ask-sudo-pass --check
````

## 2.run
````
$ ansible-playbook -i hosts zabbix3.yml --ask-sudo-pass
````
## 3.DBの設定  

後ほど！
