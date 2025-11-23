[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/1niUih_B)
| Name           | NRP        | Kelas     |
| ---            | ---        | ----------|
| Muhamad Aziz Romdhoni | 5025241071 | C |



## Put your topology config image here!

<img width="1920" height="1020" alt="Screenshot 2025-10-03 194553" src="https://github.com/user-attachments/assets/38e8abc4-024e-4a59-a27f-31295aad235b" />

- CaptainAmerica
```
iface eth0 inet static
	address 10.193.3.2
	netmask 255.255.255.0
	gateway 10.193.3.1
        up iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE -s 10.193.0.0/16
        up echo "nameserver 192.168.122.1" > /etc/resolv.conf
```

- WinterSoldier
```
auto eth0
iface eth0 inet static
	address 10.193.4.2
	netmask 255.255.255.0
	gateway 10.193.4.1
        up iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE -s 10.193.0.0/16
        up echo "nameserver 192.168.122.1" > /etc/resolv.conf
```

- BlackPanther
```
auto eth0
iface eth0 inet static
	address 10.193.0.2
	netmask 255.255.255.0
	gateway 10.193.0.1
	up iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE -s 10.193.0.0/16
	up echo "nameserver 192.168.122.1" > /etc/resolv.conf

auto eth1
iface eth1 inet static
	address 10.193.3.1
	netmask 255.255.255.0
	up iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE -s 10.193.0.0/16
	up echo "nameserver 192.168.122.1" > /etc/resolv.conf

auto eth2
iface eth2 inet static
	address 10.193.4.1
	netmask 255.255.255.0
	up iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE -s 10.193.0.0/16
	up echo "nameserver 192.168.122.1" > /etc/resolv.conf
```

- IronMan
```
auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet static
	address 10.193.0.1
	netmask 255.255.255.0
	up iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE -s 10.193.0.0/16
	up echo "nameserver 192.168.122.1" > /etc/resolv.conf
	up ip route add 10.193.3.0/24 via 10.193.0.2
	up ip route add 10.193.4.0/24 via 10.193.0.2

auto eth2
iface eth2 inet static
	address 10.193.1.1
	netmask 255.255.255.0
	up iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE -s 10.193.0.0/16
	up echo "nameserver 192.168.122.1" > /etc/resolv.conf
	up ip route add 10.193.5.0/24 via 10.193.1.2
	up ip route add 10.193.6.0/24 via 10.193.1.2
	up ip route add 10.193.7.0/24 via 10.193.1.2
```

- BlackWidow
```
auto eth0
iface eth0 inet static
	address 10.193.1.2
	netmask 255.255.255.0
	gateway 10.193.1.1
	up iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE -s 10.193.0.0/16
	up echo "nameserver 192.168.122.1" > /etc/resolv.conf

auto eth1
iface eth1 inet static
	address 10.193.6.1
	netmask 255.255.255.0
	up iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE -s 10.193.0.0/16
	up echo "nameserver 192.168.122.1" > /etc/resolv.conf

auto eth2
iface eth2 inet static
	address 10.193.5.1
	netmask 255.255.255.0
	up iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE -s 10.193.0.0/16
	up echo "nameserver 192.168.122.1" > /etc/resolv.conf
  up ip route add 10.193.7.0/24 via 10.193.6.2
```

- Vision
```
auto eth0
iface eth0 inet static
	address 10.193.6.2
	netmask 255.255.255.0
	gateway 10.193.6.1
	up iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE -s 10.193.0.0/16
	up echo "nameserver 192.168.122.1" > /etc/resolv.conf

auto eth1
iface eth1 inet static
	address 10.193.7.1
	netmask 255.255.255.0
	up iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE -s 10.193.0.0/16
	up echo "nameserver 192.168.122.1" > /etc/resolv.conf
```

- Falcon
```
auto eth0
iface eth0 inet dhcp
```

- Hawkeye
```
auto eth0
iface eth0 inet dhcp
```

- Thor
```
auto eth0
iface eth0 inet dhcp
```

- ScarletWitch
```
auto eth0
iface eth0 inet dhcp
```

- Hulk
```
auto eth0
iface eth0 inet dhcp
```

- Spiderman
```
auto eth0
iface eth0 inet dhcp
```

- DoctorStrange
```
auto eth0
iface eth0 inet dhcp
```
## Put your GNS3 Project file here!

https://drive.google.com/file/d/19SBgEdIK-8qMTvqYLsN3FZyHCzbTmQTW/view?usp=drive_link

<br>

## Soal 1

> Dokumentasikan hasil pengelompokan subnet yang telah dibuat.

> _Document the results of the subnet grouping that has been created._

**Answer:**

- Screenshot

  <img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/e515cd80-b1f9-4c7b-b579-fa39bbc2b173" />

- Explanation

Karena instruksi menggunakan netmask 255.255.255.0, maka setiap jaringan yang dipisahkan oleh router akan dianggap sebagai satu subnet. Misalnya, pada bagian kiri topologi, router BlackPanther memiliki tiga interface yang terhubung ke CaptainAmerica dan falcon subnetnya adalah 10.193.3.0/24, WinterSoldier dan Hawkeye subnetnya adalah 10.193.4.0/24, router IronMan subnetnya adalah 10.193.0.0/24. untuk router BlackWidow interface yang terhubung ke Thor dan ScarletWitch subnetnya adalah 10.193.5.0/24, Hulk dan router Vision subnetnya adalah 10.193.6.0/24, router IronMan subnetnya adalah 10.193.1.0/24. untuk router Vision subnetnya adalah 10.193.7.0/24 
<br>

## Soal 2

> Lakukan konfigurasi routing agar setiap node dapat saling berkomunikasi. Pastikan setiap router dapat mengirimkan paket ke jaringan lain melalui tabel routing yang sesuai. Sertakan bukti bahwa Falcon bisa melakukan ping ke SpiderMan, DoctorStrange, dan ScarletWitch.

> _Configure routing so that each node can communicate with each other. Ensure each router can forward packets to other networks through the appropriate routing table. Include proof that Falcon can ping SpiderMan, Doctor Strange, and ScarletWitch._

**Answer:**

- Screenshot

  <img width="1920" height="1020" alt="Screenshot 2025-10-03 174043" src="https://github.com/user-attachments/assets/944c029f-2257-4087-9782-6ad8a2307979" />

- Explanation

Langkah pertama adalah melakukan konfigurasi routing pada setiap router. Karena setiap router memisahkan jaringan ke dalam subnet yang berbeda, perlu menambahkan rute statis agar paket yang dikirim dari satu subnet dapat diteruskan ke subnet lain melalui jalur yang benar. Gunakan perintah berikut ini untuk menambahkan routing. Karena di project saya itu Falcon,Spiderman,DoctorStrange, dan ScarletWitch itu ipnya menggunakan yang dinamis jadi memerlukan langkah yang panjang seperti mengatur dhcp server, dhcp relay, dan dhcp client baru bisa melakukan ping.
`ip route add <SUBNET TUJUAN>/<NETMASK> via <GATEWAY>`

<br>

## Soal 3

> Lakukan konfigurasi agar semua node dapat terhubung ke internet. Sertakan hasil uji coba dengan melakukan ping ke google.com dari node Falcon, CaptainAmerica, SpiderMan, dan Thor.

> _Configure all nodes to connect to the internet. Include test results by pinging google.com from the Falcon, CaptainAmerica, SpiderMan, and Thor nodes._

**Answer:**

- Screenshot

  <img width="1920" height="1020" alt="Screenshot 2025-10-03 174244" src="https://github.com/user-attachments/assets/a2562de5-64da-442f-b9a6-0118ba3ac786" />
  <br><br>
  <img width="1920" height="1020" alt="Screenshot 2025-10-03 174250" src="https://github.com/user-attachments/assets/c88f7d32-25ef-477f-918f-e1037fb74216" />
  <br><br>
  <img width="1920" height="1020" alt="Screenshot 2025-10-03 174255" src="https://github.com/user-attachments/assets/bbce2b24-c356-42a8-9826-32ced85ba363" />
  <br><br>
  <img width="1920" height="1020" alt="Screenshot 2025-10-03 174301" src="https://github.com/user-attachments/assets/870617b6-c2e2-425f-9738-45b58e924807" />

- Explanation

Karena saya menggunakan ip client yang dinamis maka pertama tama yang saya lakukan adalah mengatur dhcp servernya terlebih dahulu, setelah itu lakukan dhcp relay, dan baru dhcp client supaya dapat ping google.com pastikan semua router sudah bisa ping google.com terlebih dahulu dengan menjalankan perintah.
`apt update
apt install iptables`
Lalu jalankan perintah
`iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE -s [Prefix IP].0.0/16`
Setelah itu jalankan perintah ini di router untuk mengakses jaringan
`echo nameserver [IP DNS] > /etc/resolv.conf`
<br>

## Soal 4

> Berikan Falcon alamat IP dalam rentang [Prefix IP].3.20 - [Prefix IP].3.25
> <br> </br>
> Berikan Hawkeye alamat IP dalam rentang [Prefix IP].4.30 - [Prefix IP].4.35
> <br> </br>
> Berikan Hulk alamat IP dalam rentang [Prefix IP].6.50 - [Prefix IP].6.55

<br>

> _Give Falcon an IP address in the range [IP Prefix].3.20 - [IP Prefix].4.35_
> <br> </br>
> _Give Hawkeye an IP address in the range [IP Prefix].4.30 - [IP Prefix].4.35_
> <br> </br>
> _Give Hulk an IP address in the range [IP Prefix].6.50 - [IP Prefix].6.55_

**Answer:**

- Screenshot

  <img width="1920" height="1020" alt="Screenshot 2025-10-03 174903" src="https://github.com/user-attachments/assets/a30fdd86-5c8f-4136-b0fb-e70e151b5efc" />
  <br><br>
  <img width="1920" height="1020" alt="Screenshot 2025-10-03 174912" src="https://github.com/user-attachments/assets/27e598a5-9201-49f7-a6ce-4f4264d64e6a" />

- Explanation

- Yang harus dilakukan adalah mengatur dhcp server di CaptenAmerica pertama update terlebih dahulu lalu install isc-dhcp-server perintahnya adalah seperti berikut
```
apt-get update
apt-get install isc-dhcp-server
```
- setelah itu melakukan config interface dengan perintah sebagai berikut
- /etc/default/isc-dhcp-server
```INTERFACESv4="eth0"```
- `/etc/dhcp/dhcpd.conf`
```
subnet 10.193.3.0 netmask 255.255.255.0 {
    range 10.193.3.20 10.193.3.25;
    option routers 10.193.3.1;
    option broadcast-address 10.193.3.255;
    option domain-name-servers 192.168.122.1;
}

subnet 10.193.4.0 netmask 255.255.255.0 {
    range 10.193.4.30 10.193.4.35;
    option routers 10.193.4.1;
    option broadcast-address 10.193.4.255;
    option domain-name-servers 192.168.122.1;
}

subnet 10.193.6.0 netmask 255.255.255.0 {
    range 10.193.6.50 10.193.6.55;
    option routers 10.193.6.1;
    option broadcast-address 10.193.6.255;
    option domain-name-servers 192.168.122.1;
}
```
- `service isc-dhcp-server restart`
nah jika sudah langsung mengatur bagian dhcp relay di router BlackPanther, IronMan, BlackWidow, Vision
- langsung install dan dowload
```
apt-get update
apt-get install isc-dhcp-relay -y
service isc-dhcp-relay start
```
- Pada `/etc/default/isc-dhcp-relay` lakukan konfigurasi berikut
```
SERVERS="[IP Address dari DHCP Server]"
INTERFACES="menyesuaikan jumlah interface output yang terhubung dengan client"
OPTIONS=
```
- Pada `/etc/sysctl.conf`
```
net.ipv4.ip_forward=1
```
- `service isc-dhcp-relay restart`
- ubah configuration pada bagian client
- uncoment pada bagian
```
auto eth0
iface eth0 inet dhcp
```
<br>

## Soal 5

> Berikan ScarletWitch dan Thor alamat IP dalam rentang [Prefix IP].5.40 - [Prefix IP].5.45 dan [Prefix IP].5.100 - [Prefix IP].5.105

> _Give ScarletWitch and Thor IP addresses in the range [IP Prefix].5.40 - [IP Prefix].5.45 and [IP Prefix].5.100 - [IP Prefix].5.105_

**Answer:**

- Screenshot

  <img width="1920" height="1020" alt="Screenshot 2025-10-03 175021" src="https://github.com/user-attachments/assets/a1205815-b08f-470d-9c7d-34ec839b5ac4" />

- Explanation

Sama seperti sebelumnya langsung saja ditambahkan di bagian `/etc/dhcp/dhcpd.conf`
```
subnet 10.193.5.0 netmask 255.255.255.0 {
    range 10.193.5.40 10.193.5.45;
    range 10.193.5.100 10.193.5.105;
    option routers 10.193.5.1;
    option broadcast-address 10.193.5.255;
    option domain-name-servers 192.168.122.1;
}
```
lalu `service isc-dhcp-server restart`
Lalu `service isc-dhcp-server restart`
ubah configuration pada bagian client
uncoment pada bagian
```
auto eth0
iface eth0 inet dhcp
```
<br>

## Soal 6

> Berikan SpiderMan dan DoctorStrange alamat IP dalam rentang [Prefix IP].7.60 - [Prefix IP].7.65  dan [Prefix IP].7.110 - [Prefix IP].7.115

> _Give SpiderMan and DoctorStrange IP addresses in the ranges [IP Prefix].7.60 - [IP Prefix].7.65 and [IP Prefix].7.110 - [IP Prefix].7.115_

**Answer:**

- Screenshot

 <img width="1920" height="1020" alt="Screenshot 2025-10-03 175048" src="https://github.com/user-attachments/assets/82e1067a-ffa3-4d81-aa45-98c13d097534" />

- Explanation

Masih sama seperti sebelumnya langsung tambahkan di bagian `/etc/dhcp/dhcpd.conf`
```
subnet 10.193.7.0 netmask 255.255.255.0 {
    range 10.193.7.60 10.193.7.65;
    range 10.193.7.110 10.193.7.115;
    option routers 10.193.7.1;
    option broadcast-address 10.193.7.255;
    option domain-name-servers 192.168.122.1;
}
```
Lalu `service isc-dhcp-server restart`
ubah configuration pada bagian client
uncoment pada bagian
```
auto eth0
iface eth0 inet dhcp
```

<br>

## Soal 7

> Tetapkan waktu peminjaman alamat IP pada DHCP server untuk client yang terhubung melalui Switch 2 selama 5 menit (Default), dan untuk client melalui Switch 5 selama 10 menit (Default). Tetapkan juga batas waktu peminjaman maksimal selama 2 jam.
> <br> </br>
> Tetapkan waktu peminjaman alamat IP pada DHCP server untuk client yang terhubung melalui Switch 1 dan Switch 3 selama 2 menit (Default). Tetapkan juga batas waktu peminjaman maksimal selama 100 menit.

<br>

> _Set the IP address lease period on the DHCP server for clients connected through Switch 2 to 5 minutes (default), and for clients connected through Switch 5 to 10 minutes (default). Also, set the maximum lease period to 2 hours._
> <br> </br>
> _Set the IP address lease time on the DHCP server for clients connected via Switch 1 and Switch 3 to 2 minutes (default). Also set the maximum lease time limit to 100 minutes._

**Answer:**

- Screenshot

  <img width="1920" height="1020" alt="Screenshot 2025-10-03 175206" src="https://github.com/user-attachments/assets/6ef319a0-635a-4f86-a002-d9041becd8ac" />
  <br><br>
  <img width="1920" height="1020" alt="Screenshot 2025-10-03 175214" src="https://github.com/user-attachments/assets/c15ff885-251b-4b17-b3f3-f42b9ee59713" />
  <br><br>
  <img width="1920" height="1020" alt="Screenshot 2025-10-03 175221" src="https://github.com/user-attachments/assets/c95a8421-301b-4d79-90fa-fd04d25bf039" />
  <br><br>
  <img width="1920" height="1020" alt="Screenshot 2025-10-03 180257" src="https://github.com/user-attachments/assets/02eff00c-26f0-4f6b-b68b-afda0f7b9a76" />
  <br><br>
  <img width="1920" height="1020" alt="Screenshot 2025-10-03 180321" src="https://github.com/user-attachments/assets/2c448333-eafd-4f5c-83f6-c87198cb5074" />
  <br><br>
  <img width="1920" height="1020" alt="Screenshot 2025-10-03 180412" src="https://github.com/user-attachments/assets/9b426930-5512-489e-8438-fd498430317f" />
  <br><br>
  <img width="1920" height="1020" alt="Screenshot 2025-10-03 180459" src="https://github.com/user-attachments/assets/94cf2061-41f1-487b-b8b7-6304e8d1d928" />
  <br><br>
  <img width="1920" height="1020" alt="Screenshot 2025-10-03 181440" src="https://github.com/user-attachments/assets/b60f72e5-e697-4fe3-805b-a5835f7c173c" />
  <br><br>
  <img width="1920" height="1020" alt="Screenshot 2025-10-03 181454" src="https://github.com/user-attachments/assets/27fcbc4f-5b9d-449b-9d64-c9ddb174aa79" />

- Explanation

Langsung saja modifikasi pada bagian `/etc/dhcp/dhcpd.conf` menjadi seperti ini:
```
subnet 10.193.3.0 netmask 255.255.255.0 {
    range 10.193.3.20 10.193.3.25;
    option routers 10.193.3.1;
    option broadcast-address 10.193.3.255;
    option domain-name-servers 192.168.122.1;
    min-lease-time 120;
    default-lease-time 120;
    max-lease-time 6000;
}

subnet 10.193.4.0 netmask 255.255.255.0 {
    range 10.193.4.30 10.193.4.35;
    option routers 10.193.4.1;
    option broadcast-address 10.193.4.255;
    option domain-name-servers 192.168.122.1;
    default-lease-time 300;
    max-lease-time 7200;
}

subnet 10.193.6.0 netmask 255.255.255.0 {
    range 10.193.6.50 10.193.6.55;
    option routers 10.193.6.1;
    option broadcast-address 10.193.6.255;
    option domain-name-servers 192.168.122.1;
    default-lease-time 600;
    max-lease-time 7200;
}
subnet 10.193.5.0 netmask 255.255.255.0 {
    range 10.193.5.40 10.193.5.45;
    range 10.193.5.100 10.193.5.105;
    option routers 10.193.5.1;
    option broadcast-address 10.193.5.255;
    option domain-name-servers 192.168.122.1;
    min-lease-time 120;
    default-lease-time 120;
    max-lease-time 6000;
}
subnet 10.193.7.0 netmask 255.255.255.0 {
    range 10.193.7.60 10.193.7.65;
    range 10.193.7.110 10.193.7.115;
    option routers 10.193.7.1;
    option broadcast-address 10.193.7.255;
    option domain-name-servers 192.168.122.1;
    default-lease-time 600;
    max-lease-time 7200;
}
```
lalu `service isc-dhcp-server restart`

<br>

## Soal 8

> Ubah konfigurasi DHCP Server agar Hawkeye, Thor, dan SpiderMan mendapatkan IP statis dengan [Prefix IP].x.5, namun masih menggunakan DHCP.

> _Change the DHCP Server configuration so that Hawkeye, Thor, and SpiderMan get static IPs with [Prefix IP].x.5, but still use DHCP._

**Answer:**

- Screenshot

  <img width="1920" height="1020" alt="Screenshot 2025-10-03 182358" src="https://github.com/user-attachments/assets/7e92502b-a1ac-4100-8002-a597888ff9ba" />
  <br><br>
  <img width="1920" height="1020" alt="Screenshot 2025-10-03 182422" src="https://github.com/user-attachments/assets/5a7ed6b3-d10c-473c-83f2-5487d46b49eb" />
  <br><br>
  <img width="1920" height="1020" alt="Screenshot 2025-10-03 182440" src="https://github.com/user-attachments/assets/80288a91-54cc-43cb-aa90-3f9d36c207c5" />

- Explanation

Masih sama langsung tambahkan di bagian `/etc/dhcp/dhcpd.conf`:

```
host Hawkeye {
    hardware ethernet 02:42:26:dd:65:00;
    fixed-address 10.193.4.5;
}

host Thor {
    hardware ethernet 02:42:52:4d:d7:00;
    fixed-address 10.193.5.5;
}

host Spiderman {
    hardware ethernet 02:42:b3:2e:7e:00;
    fixed-address 10.193.7.5;
}
```

Lalu `service isc-dhcp-server restart`
<br>

## Soal 9

> Buatlah konfigurasi DHCP Failover dengan WinterSoldier sebagai DHCP server backup untuk CaptainAmerica.

> _Create a DHCP Failover configuration with WinterSoldier as the backup DHCP server for CaptainAmerica._

**Answer:**

- Screenshot

  <img width="1920" height="1020" alt="Screenshot 2025-10-03 184246" src="https://github.com/user-attachments/assets/56df30bf-b4a4-4cfd-96f5-193ac31d51f8" />
  <br><br>
  <img width="1920" height="1020" alt="Screenshot 2025-10-03 190639" src="https://github.com/user-attachments/assets/b034b024-bb44-4414-a7b3-0c8ba08f8ef2" />
  <br><br>
  <img width="1920" height="1020" alt="Screenshot 2025-10-03 190701" src="https://github.com/user-attachments/assets/a7d200f9-8fc8-48cf-80bf-a70e17864f48" />
  <br><br>
  <img width="1920" height="1020" alt="Screenshot 2025-10-03 190751" src="https://github.com/user-attachments/assets/49f6fa51-5eb4-4943-bc7d-6da3ba588799" />


- Explanation

  Yang pertama dilakukan adalah mengatur WinterSolder sebagai dhcp server sama seperti CaptainAmerica langkah langkahnya
  lalu modifikasi pada bagian configurasi server `/etc/dhcp/dhcpd.conf` baik itu di server CaptainAmerica atau WinterSolder seperti berikut ini:
  Untuk WinterSolder
  ```
    failover peer "dhcp-failover" {
       secondary;
       address 10.193.4.2;
       peer address 10.193.3.2;
       max-response-delay 60;
       max-unacked-updates 10;
       load balance max seconds 0;
  }
  
  subnet 10.193.3.0 netmask 255.255.255.0 {
      option routers 10.193.3.1;
      option broadcast-address 10.193.3.255;
      option domain-name-servers 192.168.122.1;
      min-lease-time 120;
      default-lease-time 120;
      max-lease-time 6000;
      pool {
          failover peer "dhcp-failover";
          range 10.193.3.20 10.193.3.25;
      }
  }
  
  subnet 10.193.4.0 netmask 255.255.255.0 {
      option routers 10.193.4.1;
      option broadcast-address 10.193.4.255;
      option domain-name-servers 192.168.122.1;
      default-lease-time 300;
      max-lease-time 7200;
      pool {
          failover peer "dhcp-failover";
          range 10.193.4.30 10.193.4.35;
      }
  }
  
  subnet 10.193.6.0 netmask 255.255.255.0 {
      option routers 10.193.6.1;
      option broadcast-address 10.193.6.255;
      option domain-name-servers 192.168.122.1;
      default-lease-time 600;
      max-lease-time 7200;
      pool {
          failover peer "dhcp-failover";
          range 10.193.6.50 10.193.6.55;
      }
  }
  
  subnet 10.193.5.0 netmask 255.255.255.0 {
      option routers 10.193.5.1;
      option broadcast-address 10.193.5.255;
      option domain-name-servers 192.168.122.1;
      min-lease-time 120;
      default-lease-time 120;
      max-lease-time 6000;
      pool {
          failover peer "dhcp-failover";
          range 10.193.5.40 10.193.5.45;
      }
  }
  
  subnet 10.193.7.0 netmask 255.255.255.0 {
      option routers 10.193.7.1;
      option broadcast-address 10.193.7.255;
      option domain-name-servers 192.168.122.1;
      default-lease-time 600;
      max-lease-time 7200;
      pool {
          failover peer "dhcp-failover";
          range 10.193.7.60 10.193.7.65;
      }
  }
  ```
  dan Untuk CaptainAmerica
```
    failover peer "dhcp-failover" {
     primary;
     address 10.193.3.2;
     peer address 10.193.4.2;
     max-response-delay 60;
     max-unacked-updates 10;
     mclt 3600;
     split 128;
     load balance max seconds 0;
}
  
  subnet 10.193.3.0 netmask 255.255.255.0 {
      option routers 10.193.3.1;
      option broadcast-address 10.193.3.255;
      option domain-name-servers 192.168.122.1;
      min-lease-time 120;
      default-lease-time 120;
      max-lease-time 6000;
      pool {
          failover peer "dhcp-failover";
          range 10.193.3.20 10.193.3.25;
      }
  }
  
  subnet 10.193.4.0 netmask 255.255.255.0 {
      option routers 10.193.4.1;
      option broadcast-address 10.193.4.255;
      option domain-name-servers 192.168.122.1;
      default-lease-time 300;
      max-lease-time 7200;
      pool {
          failover peer "dhcp-failover";
          range 10.193.4.30 10.193.4.35;
      }
  }
  
  subnet 10.193.6.0 netmask 255.255.255.0 {
      option routers 10.193.6.1;
      option broadcast-address 10.193.6.255;
      option domain-name-servers 192.168.122.1;
      default-lease-time 600;
      max-lease-time 7200;
      pool {
          failover peer "dhcp-failover";
          range 10.193.6.50 10.193.6.55;
      }
  }
  
  subnet 10.193.5.0 netmask 255.255.255.0 {
      option routers 10.193.5.1;
      option broadcast-address 10.193.5.255;
      option domain-name-servers 192.168.122.1;
      min-lease-time 120;
      default-lease-time 120;
      max-lease-time 6000;
      pool {
          failover peer "dhcp-failover";
          range 10.193.5.40 10.193.5.45;
      }
  }
  
  subnet 10.193.7.0 netmask 255.255.255.0 {
      option routers 10.193.7.1;
      option broadcast-address 10.193.7.255;
      option domain-name-servers 192.168.122.1;
      default-lease-time 600;
      max-lease-time 7200;
      pool {
          failover peer "dhcp-failover";
          range 10.193.7.60 10.193.7.65;
      }
  }
  ```
lalu `service isc-dhcp-server restart`
cabo lakukan `service isc-dhcp-server stop` untuk memastikan bahwa server WinterSoldier dapat membackup

<br>

## Soal 10

> Buatlah konfigurasi agar CaptainAmerica dan WinterSoldier berjalan dengan mode Load Balancing.

> _Create a configuration so that CaptainAmerica and WinterSoldier run in Load Balancing mode._

**Answer:**

- Screenshot

  <img width="1920" height="1020" alt="Screenshot 2025-10-03 190934" src="https://github.com/user-attachments/assets/df0ac4ce-a627-44a6-a0a2-0b3d6c0bfe05" />
  <br><br>
  <img width="1920" height="1020" alt="Screenshot 2025-10-03 190944" src="https://github.com/user-attachments/assets/c02092da-eacb-4150-9750-0cc5025d0d44" />
  <br><br>
  <img width="1920" height="1020" alt="Screenshot 2025-10-03 193258" src="https://github.com/user-attachments/assets/227a73e8-3cfa-49d9-9682-45a661d38dd7" />
  <br><br>
  <img width="1920" height="1020" alt="Screenshot 2025-10-03 193309" src="https://github.com/user-attachments/assets/a3713eb8-43b0-4a61-85fa-a89f3ef7f49b" />

- Explanation

  Caranya adalah langsung modifikasi saja di bagian `/etc/dhcp/dhcpd.conf`:
```
failover peer "dhcp-failover" {
     primary;
     address 10.193.3.2;
     peer address 10.193.4.2;
     max-response-delay 60;
     max-unacked-updates 10;
     mclt 3600;
     split 128;
     load balance max seconds 3;
}

    failover peer "dhcp-failover" {
       secondary;
       address 10.193.4.2;
       peer address 10.193.3.2;
       max-response-delay 60;
       max-unacked-updates 10;
       load balance max seconds 3;
  }
```
lalu `service isc-dhcp-server restart`
<br>
  
## Problems
`-`
## Revisions (if any)
Menambahkan 1 hasil ssan nomor 9 karena lupa dimasukkan
