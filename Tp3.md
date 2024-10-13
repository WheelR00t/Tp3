# TP 3

### I. ARP basics

#### Affichez l'adresse MAC de votre carte WiFi !

```powershell
Carte réseau sans fil Wi-Fi :

   Suffixe DNS propre à la connexion. . . :
   Description. . . . . . . . . . . . . . : Realtek RTL8821CE 802.11ac PCIe Adapter
  ☀️  Adresse physique . . . . . . . . . . . : 74-97-79-66-39-B3
   DHCP activé. . . . . . . . . . . . . . : Oui
   Configuration automatique activée. . . : Oui
   Adresse IPv6 de liaison locale. . . . .: fe80::23f8:c185:1b16:5353%19(préféré)
   Adresse IPv4. . . . . . . . . . . . . .: 10.33.79.0(préféré)
   Masque de sous-réseau. . . . . . . . . : 255.255.240.0
   Bail obtenu. . . . . . . . . . . . . . : mardi 8 octobre 2024 13:33:44
   Bail expirant. . . . . . . . . . . . . : mercredi 9 octobre 2024 13:33:44
   Passerelle par défaut. . . . . . . . . : 10.33.79.254
   Serveur DHCP . . . . . . . . . . . . . : 10.33.79.254
   IAID DHCPv6 . . . . . . . . . . . : 292853625
   DUID de client DHCPv6. . . . . . . . : 00-01-00-01-2E-46-80-B3-74-97-79-66-39-B3
   Serveurs DNS. . .  . . . . . . . . . . : 8.8.8.8
                                       1.1.1.1
   NetBIOS sur Tcpip. . . . . . . . . . . : Activé
```

#### Affichez votre table ARP

```powershell
PS C:\Users\Ethan> arp -a

Interface : 192.168.56.1 --- 0x6
  Adresse Internet      Adresse physique      Type
  192.168.56.255        ff-ff-ff-ff-ff-ff     statique
  224.0.0.2             01-00-5e-00-00-02     statique
  224.0.0.22            01-00-5e-00-00-16     statique
  224.0.0.251           01-00-5e-00-00-fb     statique
  224.0.0.252           01-00-5e-00-00-fc     statique
  230.0.0.1             01-00-5e-00-00-01     statique
  239.242.6.7           01-00-5e-72-06-07     statique
  239.255.132.178       01-00-5e-7f-84-b2     statique
  239.255.255.250       01-00-5e-7f-ff-fa     statique
  239.255.255.253       01-00-5e-7f-ff-fd     statique

Interface : 10.33.79.0 --- 0x13
  Adresse Internet      Adresse physique      Type
  10.33.65.63           44-af-28-c3-6a-9f     dynamique
  10.33.79.254          7c-5a-1c-d3-d8-76     dynamique
  10.33.79.255          ff-ff-ff-ff-ff-ff     statique
  224.0.0.2             01-00-5e-00-00-02     statique
  224.0.0.22            01-00-5e-00-00-16     statique
  224.0.0.251           01-00-5e-00-00-fb     statique
  224.0.0.252           01-00-5e-00-00-fc     statique
  230.0.0.1             01-00-5e-00-00-01     statique
  239.242.6.7           01-00-5e-72-06-07     statique
  239.255.132.178       01-00-5e-7f-84-b2     statique
  239.255.255.250       01-00-5e-7f-ff-fa     statique
  239.255.255.253       01-00-5e-7f-ff-fd     statique
  255.255.255.255       ff-ff-ff-ff-ff-ff     statique
```

#### Déterminez l'adresse MAC de la passerelle du réseau de l'école

```powershell
Interface : 10.33.79.0 --- 0x13
  Adresse Internet      Adresse physique      Type
  10.33.65.63           44-af-28-c3-6a-9f     dynamique
 ☀️ 10.33.79.254          7c-5a-1c-d3-d8-76     dynamique
  ...
```

#### Supprimez la ligne qui concerne la passerelle

```
 arp -d 10.33.79.254  
```

#### Prouvez que vous avez supprimé la ligne dans la table ARP

```powershell
Interface : 10.33.79.0 --- 0x13
  Adresse Internet      Adresse physique      Type
  10.33.65.63           44-af-28-c3-6a-9f     dynamique
  10.33.79.255          ff-ff-ff-ff-ff-ff     statique
  224.0.0.2             01-00-5e-00-00-02     statique
  224.0.0.22            01-00-5e-00-00-16     statique
  224.0.0.251           01-00-5e-00-00-fb     statique
  224.0.0.252           01-00-5e-00-00-fc     statique
  230.0.0.1             01-00-5e-00-00-01     statique
  239.242.6.7           01-00-5e-72-06-07     statique
  239.255.132.178       01-00-5e-7f-84-b2     statique
  239.255.255.250       01-00-5e-7f-ff-fa     statique
  239.255.255.253       01-00-5e-7f-ff-fd     statique
  255.255.255.255       ff-ff-ff-ff-ff-ff     statique
```

#### Wireshark

[Capture](./arp1.pcap)



### 1. Basics

#### Déterminer pour la carte réseau impliquée dans le partage de connexion (carte WiFi ?)
#### - son adresse IP au sein du réseau local formé par le partage de co
#### - son adresse MAC

```powershell
Carte réseau sans fil Wi-Fi :

   Suffixe DNS propre à la connexion. . . :
  ☀ Description. . . . . . . . . . . . . . : Realtek RTL8821CE 802.11ac PCIe Adapter
  ☀ Adresse physique . . . . . . . . . . . : 74-97-79-66-39-B3
   DHCP activé. . . . . . . . . . . . . . : Oui
   Configuration automatique activée. . . : Oui
   Adresse IPv6. . . . . . . . . . . . . .: 2a04:cec0:101b:f5ca:a07e:f58c:4173:a1ea(préféré)
   Adresse IPv6 temporaire . . . . . . . .: 2a04:cec0:101b:f5ca:2146:fb39:d934:9220(préféré)
   Adresse IPv6 de liaison locale. . . . .: fe80::23f8:c185:1b16:5353%19(préféré)
   ☀ Adresse IPv4. . . . . . . . . . . . . .: 172.20.10.2(préféré)
   Masque de sous-réseau. . . . . . . . . : 255.255.255.240
   Bail obtenu. . . . . . . . . . . . . . : mardi 8 octobre 2024 16:41:54
   Bail expirant. . . . . . . . . . . . . : mercredi 9 octobre 2024 16:41:54
   Passerelle par défaut. . . . . . . . . : fe80::e8a7:30ff:fef0:f164%19
                                       172.20.10.1
   Serveur DHCP . . . . . . . . . . . . . : 172.20.10.1
   IAID DHCPv6 . . . . . . . . . . . : 292853625
   DUID de client DHCPv6. . . . . . . . : 00-01-00-01-2E-46-80-B3-74-97-79-66-39-B3
   Serveurs DNS. . .  . . . . . . . . . . : fe80::e8a7:30ff:fef0:f164%19
                                       172.20.10.1
   NetBIOS sur Tcpip. . . . . . . . . . . : Activé
```

### DIY

#### - Changer d'adresse IP

```powershell
Carte réseau sans fil Wi-Fi :

   Suffixe DNS propre à la connexion. . . :
   Description. . . . . . . . . . . . . . : Realtek RTL8821CE 802.11ac PCIe Adapter
   Adresse physique . . . . . . . . . . . : 74-97-79-66-39-B3
   DHCP activé. . . . . . . . . . . . . . : Non
   Configuration automatique activée. . . : Oui
   Adresse IPv6. . . . . . . . . . . . . .: 2a04:cec0:101b:f5ca:a07e:f58c:4173:a1ea(préféré)
   Adresse IPv6 temporaire . . . . . . . .: 2a04:cec0:101b:f5ca:7c9f:d776:da22:7d5c(préféré)
   Adresse IPv6 de liaison locale. . . . .: fe80::23f8:c185:1b16:5353%19(préféré)
   Adresse IPv4. . . . . . . . . . . . . .: 172.20.10.10(préféré)
   Masque de sous-réseau. . . . . . . . . : 255.255.240.0
   Passerelle par défaut. . . . . . . . . : fe80::e8a7:30ff:fef0:f164%19
   IAID DHCPv6 . . . . . . . . . . . : 292853625
   DUID de client DHCPv6. . . . . . . . : 00-01-00-01-2E-46-80-B3-74-97-79-66-39-B3
   Serveurs DNS. . .  . . . . . . . . . . : fe80::e8a7:30ff:fef0:f164%19
   NetBIOS sur Tcpip. . . . . . . . . . . : Activé
```


#### Pingz !

```powershell
PS C:\Users\Ethan> ping 172.20.10.2 ; ping 172.20.10.13 ; ping 172.20.10.14

Envoi d’une requête 'Ping'  172.20.10.2 avec 32 octets de données :
Réponse de 172.20.10.2 : octets=32 temps=14 ms TTL=128
Réponse de 172.20.10.2 : octets=32 temps=6 ms TTL=128
Réponse de 172.20.10.2 : octets=32 temps=6 ms TTL=128
Réponse de 172.20.10.2 : octets=32 temps=6 ms TTL=128

Statistiques Ping pour 172.20.10.2:
    Paquets : envoyés = 4, reçus = 4, perdus = 0 (perte 0%),
Durée approximative des boucles en millisecondes :
    Minimum = 6ms, Maximum = 14ms, Moyenne = 8ms

Envoi d’une requête 'Ping'  172.20.10.13 avec 32 octets de données :
Réponse de 172.20.10.13 : octets=32 temps=5 ms TTL=128
Réponse de 172.20.10.13 : octets=32 temps=14 ms TTL=128
Réponse de 172.20.10.13 : octets=32 temps=49 ms TTL=128
Réponse de 172.20.10.13 : octets=32 temps=6 ms TTL=128

Statistiques Ping pour 172.20.10.13:
    Paquets : envoyés = 4, reçus = 4, perdus = 0 (perte 0%),
Durée approximative des boucles en millisecondes :
    Minimum = 5ms, Maximum = 49ms, Moyenne = 18ms

Envoi d’une requête 'Ping'  172.20.10.14 avec 32 octets de données :
Réponse de 172.20.10.14 : octets=32 temps=13 ms TTL=128
Réponse de 172.20.10.14 : octets=32 temps=8 ms TTL=128
Réponse de 172.20.10.14 : octets=32 temps=12 ms TTL=128
Réponse de 172.20.10.14 : octets=32 temps=21 ms TTL=128

Statistiques Ping pour 172.20.10.14:
    Paquets : envoyés = 4, reçus = 4, perdus = 0 (perte 0%),
Durée approximative des boucles en millisecondes :
    Minimum = 8ms, Maximum = 21ms, Moyenne = 13ms
```


#### Vérifiez avec une commande ping que vous avez bien un accès internet
```powershell
PS C:\Users\Ethan> ping google.com

Envoi d’une requête 'ping' sur google.com [2a00:1450:4007:807::200e] avec 32 octets de données :
Réponse de 2a00:1450:4007:807::200e : temps=26 ms
Réponse de 2a00:1450:4007:807::200e : temps=47 ms
Réponse de 2a00:1450:4007:807::200e : temps=95 ms
Réponse de 2a00:1450:4007:807::200e : temps=50 ms

Statistiques Ping pour 2a00:1450:4007:807::200e:
    Paquets : envoyés = 4, reçus = 4, perdus = 0 (perte 0%),
Durée approximative des boucles en millisecondes :
    Minimum = 26ms, Maximum = 95ms, Moyenne = 54ms
```

### 2. ARP

#### Affichez votre table ARP !

```powershell
PS C:\Users\Ethan> arp -a

Interface : 172.20.10.10 --- 0x13
  Adresse Internet      Adresse physique      Type
  172.20.10.2           e4-c7-67-b5-a2-3e     dynamique
  172.20.10.13          98-bd-80-d5-2b-bd     dynamique
  172.20.10.14          c0-35-32-1c-af-a9     dynamique
```

#### Wireshark that













### 3. ARP poisoning


⭐ Empoisonner la table ARP de l'un des membres de votre réseau et ettre en place un MITM

```
Utilisation de Ettercap sous Kali Linux

> sudo ettercap -G
> Sélection de l'interface
> Scan des hosts avec scan IPV6
> Sélection du routeur et de la victime 
> Démarrer le ARP Poisonning

> PS C:\Windows\system32> arp -a

Interface : 192.168.56.1 --- 0x6
  Adresse Internet      Adresse physique      Type
  224.0.0.2             01-00-5e-00-00-02     statique
  224.0.0.22            01-00-5e-00-00-16     statique
  224.0.0.251           01-00-5e-00-00-fb     statique

Interface : 192.168.1.198 --- 0x7
  Adresse Internet      Adresse physique      Type
  192.168.1.1           74-97-79-66-39-b3     dynamique
  ⭐192.168.1.133         74-97-79-66-39-b3     dynamique
  224.0.0.2             01-00-5e-00-00-02     statique
  224.0.0.22            01-00-5e-00-00-16     statique
  224.0.0.251           01-00-5e-00-00-fb     statique
  224.168.100.1         01-00-5e-28-64-01     statique

  > Sur Wireshark, nous voyons bien les requêtes faites par la victime quand il se rend sur le Web.


