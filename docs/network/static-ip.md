# Konfiguracja statycznego IP

## Infrastruktura
- Ubuntu PC (główny serwer) — interfejs: enp3s0
- Sieć: 192.168.137.0/24 (Windows ICS)
- Brama: 192.168.137.1 (laptop Windows)

## Adresy statyczne
|
 Maszyna     
|
 Adres IP        
|

|
-------------
|
-----------------
|

|
 Ubuntu PC   
|
 192.168.137.10  
|

|
 Raspberry Pi
|
 TBD             
|


## Jak skonfigurowano Ubuntu PC
System używa NetworkManager + Netplan.

Problem: dwa pliki Netplan kłóciły się — installer
ustawiał dhcp4: true, przez co po rebootcie system
dostawał dwa adresy jednocześnie.

Rozwiązanie: wyłączono DHCP w pliku instalatora:
/etc/netplan/00-installer-config.yaml → dhcp4: false

Weryfikacja:
    ip addr show enp3s0 | grep "inet "
    ip route show default
    ping -c 3 8.8.8.8

## Status
- [x] Ubuntu PC — 192.168.137.10 
- [ ] Raspberry Pi — TBD
