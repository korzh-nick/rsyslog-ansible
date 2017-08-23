# rsyslog-ansible

## Description
Rsyslog script installs and enables nginx send logs to elk (logstash) via rsyslog

## Playbook example
```
- hosts: all
  vars_files:
    - vars/main.yml
  roles:
    - role: rsyslog
```
vars/main.yml:
```
host_name: ""
logstash_host_ip: ""
logs_path: "/var/log/nginx"
```

## Host iptables 

* install ipset
* add iptables rule:
```
-A INPUT -m set --set rsyslog src -p udp -m udp --dport 10514 -j ACCEPT
```
* add ip to ipset:
```
sudo ipset add rsyslog {{ host_name }}
sudo ipset list
```
