* 根目录

su

* 用户创建

useradd student -d /student -p 123456

cat /etc/passwd

* ip地址和进程

ps

ip a

ss -nlptu

ss -nlptu | grep sshd

ps aux | grep sshd

* 网卡自启动

cd /etc/sysconfig/network-scripts

vi ifcfg-ens33

systemctl restart netw

最后一个yes

* 查看文件

ls -la

* 编辑文档

vi

i

x

: wq!

* 防火墙

systemctl status firewalld.service

systemctl stop firewalld.service

systemctl disable firewalld.service

* selinux

vi /etc/selinux/config(SELINUX=enforcing disabled)

getenforce

* 主机名称修改

vi /etc/hostname

* 配置服务器ip地址

vi /etc/hosts

master  192.168.xxx.xxx

slave  192.168.xxx.xxx

ping master

* 静态IP

cd /etc/sysconfig/network-scripts

vi ifcfg-ens33

IPDDR=192.168.240.136

NETMASK=255.255.255.0

GATEWAY=192.168.240.2

DNS=192.168.0.1 

* 连接其他主机

ssh master

或ssh 192.168.xxx.xxx

exit

* 免密

cd /etc/ssh

ssh-keygen

ssh-copy-id slave1

* sudo权限

visudo

emoaya  ALL=(ALL)       ALL  

sudo vi /etc/hostname

su emoaya

* 传文件

rz -bey

* 解压

tar -xzvf xxxxx