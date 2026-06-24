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
 192.168.178.11             
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

## Jak skonfigurowano Raspberry Pi

Problem: po zmianie IP przez nmcli connection down/up, SSH 
na nowy adres nie działało od razu — sieć potrzebowała 
chwili na odświeżenie tablicy ARP. 
Rozwiązanie: reboot Pi (sudo reboot) lub odczekanie ~1-2 minut.

Komendy:

    nmcli connection modify [nazwa profilu sieciowego] ipv4.addresses 192.168.178.11/24
    nmcli connection modify [nazwa profilu sieciowego] ipv4.gateway 192.168.178.1
    nmcli connection modify [nazwa profilu sieciowego] ipv4.dns "8.8.8.8 1.1.1.1"
    nmcli connection modify [nazwa profilu sieciowego] ipv4.method manual
    nmcli connection down [nazwa profilu sieciowego] && nmcli connection up [nazwa profilu sieciowego]
    nmcli connection show - sprawdzenie profili sieciowych

## Połączenie passwordless za pomocą ssh windows > PI

Komendy:

    ssh-keygen -t ed25519 -C "windows-homelab"
    echo "key" ~/.ssh/authorized_keys
    /etc/ssh/sshd_config - zmiana #PasswordAuthentication no
    sudo systemctl restart ssh       
    ssh -o PreferredAuthentications=password krysitan@192.168.178.11

## Status
- [x] Ubuntu PC — 192.168.137.10 
- [x] Raspberry Pi — 192.168.178.11
