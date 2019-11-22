
# script-jesus
SW-CORE (JESUS) 

enable
configure terminal
hostname SW-CORE 
enable secret SenhadaEnable 
line console 0  
password SenhadaConsole 
login 
exit 
username PedroLucca privilege 15 secret SenhaLucca
username AndreJesus privilege 15 secret SenhaJesus
username KevinWitt privilege 15 secret SenhaWitt
username MarcosTeles privilege 15 secret SenhaTeles
ip domain-name GRUPO2.local
crypto key generate rsa general-keys modulus 1024
service password-encryption
line vty 0 15
transport input ssh
exec-timeout 5
login local
exit
vlan 12
name PCVLAN12
vlan 102
name Equipamentos
interface fastethernet 0/1
switchport mode access
switchport access vlan 102
description SRVGRUPO2
exit
interface fastethernet 0/2
switchport mode trunk
switchport trunk native vlan 99
switchport trunk allowed vlan 12,102,99
exit
interface gigabitethernet 0/1
switchport mode trunk
switchport trunk native vlan 99
switchport trunk allowed vlan 12,102,99
exit
interface vlan 102
ip address 192.168.253.254 255.255.255.0
no shutdown
exit
ip default-gateway 192.168.253.1
do wr
