[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/oYnIPZ_t)
| Name           | NRP        | Kelas     |
| ---            | ---        | ----------|
| Muhamad Aziz Romdhoni | 5025241071 | C |



## Put your topology config image here!

<img width="1919" height="857" alt="Screenshot 2025-11-21 200205" src="https://github.com/user-attachments/assets/f0c4b659-e764-4341-ba76-15f6f9f85f72" />

## Put your GNS3 Project file here!

https://drive.google.com/file/d/1DpfD8vxnp-d5pbai1eVCG4jadxkd2Lc5/view?usp=sharing

<br>

## Soal 1

> Lakukan subnetting pada topologi diatas menggunakan metode VLSM: [Referensi](https://github.com/arsitektur-jaringan-komputer/Modul-Jarkom/tree/master/Modul-4/Subnetting#2-vlsm-variable-length-subnet-masking)  
*Cantumkan juga tabel dan diagram pembagian subnet pada laporan praktikum*.


> _Subnet the topology above using the VLSM method: [Reference](https://github.com/arsitektur-jaringan-komputer/Modul-Jarkom/tree/master/Modul-4/Subnetting#2-vlsm-variable-length-subnet-masking)_  
_Also include the subnet table and diagram in the lab report._

**Answer:**

- Screenshot

  <img width="1839" height="271" alt="Screenshot 2025-11-21 201602" src="https://github.com/user-attachments/assets/d196de3e-e6ce-4bd0-a36d-fc5cedb7311d" />
  <br><br>
  <img width="1187" height="548" alt="Screenshot 2025-11-21 201613" src="https://github.com/user-attachments/assets/c2a75b3f-28f6-42e4-ac85-3e45dd3c5d4d" />
  <br><br>

- Explanation

  buat confignya seluruh node seperti dibawah ini
  - IT-PC-1
  ```
  auto eth0
  iface eth0 inet static
  	address 10.193.2.3
  	netmask 255.255.255.128
  	gateway 10.193.2.126
          up echo nameserver 192.168.122.1 > /etc/resolv.conf
  ```
  - IT-PC-2
  ```
  auto eth0
  iface eth0 inet static
  	address 10.193.2.2
  	netmask 255.255.255.128
  	gateway 10.193.2.126
  	up echo nameserver 192.168.122.1 > /etc/resolv.conf
  ```
  - IT-PC-3
  ```
  auto eth0
  iface eth0 inet static
  	address 10.193.2.1
  	netmask 255.255.255.128
  	gateway 10.193.2.126
  	up echo nameserver 192.168.122.1 > /etc/resolv.conf
  ```
  - router-1
  ```
  auto eth0
  iface eth0 inet static
  	address 10.193.2.126
  	netmask 255.255.255.128
  	up echo nameserver 192.168.122.1 > /etc/resolv.conf
  
  auto eth1
  iface eth1 inet static
  	address 10.193.2.241
  	netmask 255.255.255.252
  	gateway 10.193.2.242
  	up echo nameserver 192.168.122.1 > /etc/resolv.conf

  ```
  - router-2
  ```
  auto eth0
  iface eth0 inet static
  	address 10.193.2.242
  	netmask 255.255.255.252
  	up echo nameserver 192.168.122.1 > /etc/resolv.conf
  
  auto eth1
  iface eth1 inet static
  	address 10.193.2.254
  	netmask 255.255.255.252
  	up echo nameserver 192.168.122.1 > /etc/resolv.conf
  
  auto eth2
  iface eth2 inet static
  	address 10.193.2.246
  	netmask 255.255.255.252
  	up echo nameserver 192.168.122.1 > /etc/resolv.conf
  
  auto eth3
  iface eth3 inet dhcp
  ```
  - router-3
  ```
  auto eth0
  iface eth0 inet static
  	address 10.193.2.245
  	netmask 255.255.255.252
  	gateway 10.193.2.246
  	up echo nameserver 192.168.122.1 > /etc/resolv.conf
  
  auto eth1
  iface eth1 inet static
  	address 10.193.2.238
  	netmask 255.255.255.240
  	up echo nameserver 192.168.122.1 > /etc/resolv.conf
    
  auto eth2
  iface eth2 inet static
  	address 10.193.2.222
  	netmask 255.255.255.224
  	up echo nameserver 192.168.122.1 > /etc/resolv.conf
  ```
  - DB-Server-1
  ```
  auto eth0
  iface eth0 inet static
  	address 10.193.2.225
  	netmask 255.255.255.240
  	gateway 10.193.2.238
  	up echo nameserver 192.168.122.1 > /etc/resolv.conf

  ```
  - DB-Server-2
  ```
  auto eth0
  iface eth0 inet static
  	address 10.193.2.193
  	netmask 255.255.255.224
  	gateway 10.193.2.222
  	up echo nameserver 192.168.122.1 > /etc/resolv.conf
  ```
  - router-4
  ```
  auto eth0
  iface eth0 inet static
  	address 10.193.2.253
  	netmask 255.255.255.252
  	gateway 10.193.2.254
  	up echo nameserver 192.168.122.1 > /etc/resolv.conf
  
  auto eth1
  iface eth1 inet static
  	address 10.193.2.158
  	netmask 255.255.255.224
  	up echo nameserver 192.168.122.1 > /etc/resolv.conf
  
  auto eth2
  iface eth2 inet static
  	address 10.193.2.190
  	netmask 255.255.255.224
  	up echo nameserver 192.168.122.1 > /etc/resolv.conf
    
  auto eth3
  iface eth3 inet static
  	address 10.193.2.250
  	netmask 255.255.255.252
  	gateway 10.193.2.254
  	up echo nameserver 192.168.122.1 > /etc/resolv.conf
  ```
  - Web-Server-1
  ```
  auto eth0
  iface eth0 inet static
  	address 10.193.2.129
  	netmask 255.255.255.224
  	gateway 10.193.2.158
  	up echo nameserver 192.168.122.1 > /etc/resolv.conf
  ```
  - Web-Server-2
  ```
  auto eth0
  iface eth0 inet static
  	address 10.193.2.161
  	netmask 255.255.255.224
  	gateway 10.193.2.190
  	up echo nameserver 192.168.122.1 > /etc/resolv.conf
  ```
  - router-5
  ```
  auto eth0
  iface eth0 inet static
  	address 10.193.2.249
  	netmask 255.255.255.252
  	gateway 10.193.2.250
  	up echo nameserver 192.168.122.1 > /etc/resolv.conf
  
  
  auto eth1
  iface eth1 inet static
  	address 10.193.1.254
  	netmask 255.255.254.0
  	up echo nameserver 192.168.122.1 > /etc/resolv.conf
  ```
  - HR-PC-1
  ```
  auto eth0
  iface eth0 inet static
  	address 10.193.0.1
  	netmask 255.255.254.0
  	gateway 10.193.1.254
  	up echo nameserver 192.168.122.1 > /etc/resolv.conf
  ```
  - HR-PC-2
  ```
  auto eth0
  iface eth0 inet static
  	address 10.193.0.2
  	netmask 255.255.254.0
  	gateway 10.193.1.254
  	up echo nameserver 192.168.122.1 > /etc/resolv.conf
  ```

<br>

## Soal 2

> Buatlah agar router-2 dapat melakukan koneksi ke internet. [Dapat menggunakan static routing].

> _Make sure router-2 can connect to the internet. [Can use static routing]._

**Answer:**

- Screenshot

 <img width="1310" height="427" alt="Screenshot 2025-11-21 181824" src="https://github.com/user-attachments/assets/c0bb3f1e-5cfd-496d-9abe-48b6f4b4b87d" />

- Explanation

  -  Langsung saja ping google.com karena router-2 langsung tersambung dengan NAT

<br>

## Soal 3

> Setelah mengimplementasi subnetting, buatlah agar seluruh topologi dapat terhubung. Lakukan Dynamic Routing pada topologi tersebut.
*Pastikan seluruh node yang ada dapat mengakses internet*.

> _After implementing subnetting, ensure the entire topology is connected. Perform dynamic routing on the topology._  
_Ensure all existing nodes can access the internet._

**Answer:**

- Screenshot

  <img width="914" height="606" alt="Screenshot 2025-11-21 183757" src="https://github.com/user-attachments/assets/26278b44-d5ce-466e-82c2-0ed252d29f7e" />
  <br><br>
  <img width="895" height="603" alt="Screenshot 2025-11-21 183812" src="https://github.com/user-attachments/assets/74e42893-7486-4334-9dee-6be9aa64df85" />
  <br><br>
  <img width="900" height="607" alt="Screenshot 2025-11-21 183825" src="https://github.com/user-attachments/assets/3f7687e3-bbe0-4845-abf7-3d49512d32cc" />
  <br><br>
  <img width="907" height="603" alt="Screenshot 2025-11-21 183839" src="https://github.com/user-attachments/assets/19806e5a-2e16-4441-a8fe-e54e143120a8" />
  <br><br>
- Explanation

  - Untuk langkah - langkahnya tinggal langsung mengikuti bagian dynamic routing di router yaitu
  ```
  cd /usr/lib/frr
  ./zebra -d
  ./ripd -d
  ./mgmtd -d
  vtysh
  conf t
  router rip
  ```
  - Sesuai dengan NID dan netmasnk
  ```
  router1
  network 10.193.2.0/25
  network 10.193.2.240/30
  
  router2
  network 10.193.2.240/30
  network 10.193.2.244/30
  network 10.193.2.252/30
  
  router3
  network 10.193.2.192/27
  network 10.193.2.224/28
  network 10.193.2.244/30
  
  router4
  network 10.193.2.128/27
  network 10.193.2.160/27
  network 10.193.2.248/30
  network 10.193.2.252/30
  
  router5
  network 10.193.0.0/23
  network 10.193.2.248/30
  ```
  - Selanjutnya jalankan coman dibawah ini di router-2
  ```
  apt update
  apt install iptables
  ```
  - Selanjutnya baru jalnkan
  ```
  iptables -t nat -A POSTROUTING -o eth3 -j MASQUERADE -s 10.193.0.0/16
  ```
  - Baru bisa testing menggunakan ping di semua nodenya

<br>

## Soal 4

> Lakukan setup web server dengan file html di attachment berikut: [ Attachment ](https://drive.google.com/file/d/199qwfTNJCkxDV7mdO-MsaDdApkmKsnAG/view?usp=sharing)  menggunakan nginx pada “Web-Server-1” dan “Web-Server-2”.  
*Config dibebaskan kepada praktikkan dengan catatan menggunakan port 80*.

> _Set up a web server with the HTML file in the following attachment: [ Attachment ](https://drive.google.com/file/d/199qwfTNJCkxDV7mdO-MsaDdApkmKsnAG/view?usp=sharing) using nginx on “Web-Server-1” and “Web-Server-2”._
_Configuration is free to practice, but note that it uses port 80._

**Answer:**

- Screenshot

  <img width="901" height="603" alt="Screenshot 2025-11-21 183922" src="https://github.com/user-attachments/assets/ce1db820-8d32-45c3-8369-82fb2f9e3192" />
  <br><br>
  <img width="919" height="611" alt="Screenshot 2025-11-21 184006" src="https://github.com/user-attachments/assets/8c902c0f-e4a3-46b6-b5ea-21000354442d" />
  <br><br>

- Explanation

  - Buat direktori myweb,myconfig, dan file start_http.sh didalam folder myscripts dibagain Web-Server-1 dan Web-Server-2
  - myweb
    - Masukkan file index.html yang ada di diberikan
    ```
    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>Simple Page</title>
        <style>
            body {
                margin: 0;
                padding: 0;
                font-family: Arial, sans-serif;
                background: #f5f5f5;
                display: flex;
                justify-content: center;
                align-items: center;
                height: 100vh;
                color: #333;
            }
            .container {
                text-align: center;
                padding: 20px 30px;
                background: white;
                border-radius: 8px;
                box-shadow: 0 2px 10px rgba(0,0,0,0.1);
            }
            h1 {
                margin-bottom: 10px;
                font-size: 24px;
                font-weight: 600;
            }
            p {
                margin: 0;
                font-size: 14px;
                color: #555;
            }
        </style>
    </head>
    <body>
        <div class="container">
            <h1>Hello!</h1>
            <p>Web Server | Jarkom Praktikum Modul 4 </p>
        </div>
    </body>
    </html>
    ```
    - myconfig
      - Buat file nginx.conf
      ```
      user www-data;
      worker_processes auto;
      worker_cpu_affinity auto;
      pid /tmp/nginx.pid;
      error_log  /tmp/error.log;
      
      events { worker_connections 768; }
      
      http {
          server {
              listen 80;
              server_name _;
      
              root /myscripts/myweb;
              index index.html;
      
              location / {
                  try_files $uri $uri/ =404;
              }
          }
      }
      ```
    - Buat file start_http.sh untuk menjalankan nginx
    ```
    #!/bin/bash
    
    nginx -c /myscripts/myconfig/nginx.conf -g 'daemon off;'
    ```
  - Lalu jalankan perintah berikut: chmod +x /myscripts/start_http.sh
  - Jalankan nginx dengan perintah berikut /myscripts/start_http.sh
  - Lalu cek di bagian client yaitu HR-PC-1 dan HR-PC-2 dengan curl
<br>

## Soal 5

> Kalian diminta untuk melakukan drop semua paket TCP yang masuk  ke subnet HR dengan port 1337 dan 4444. Lakukan testing dengan netcat.

> _You are asked to drop all incoming TCP packets to the HR subnet with ports 1337 and 4444. Test with netcat._

**Answer:**

- Screenshot

  <img width="906" height="601" alt="Screenshot 2025-11-21 184310" src="https://github.com/user-attachments/assets/805a9ec7-9b04-4bc2-87fa-32e6c4ebc915" />
  <br><br>

- Explanation

  - Jalankan perintah berikut di router-5
  ```
  apt update
  apt install iptables
  iptables -A FORWARD -p tcp -d 10.193.0.0/23 --dport 1337 -j DROP
  iptables -A FORWARD -p tcp -d 10.193.0.0/23 --dport 4444 -j DROP
  ```
  - Terus bisa mengecek testing di bagian lainnya dengan netcat yaitu dengan menjalankan perintah ini dari luar node HR
  ```
  nc 10.193.0.1 1337 -v
  nc 10.193.0.2 1337 -v
  nc 10.193.0.1 4444 -v
  nc 10.193.0.2 4444 -v
  ```

<br>

## Soal 6

> Lakukan pembatasan sehingga koneksi SSH pada semua Web Server hanya dapat dilakukan oleh user yang berada pada node IT-PC-1, IT-PC-2, dan IT-PC-3. 

> _Implement restrictions so that SSH connections to all Web Servers can only be made by users on nodes IT-PC-1, IT-PC-2, and IT-PC-3._

**Answer:**

- Screenshot

  <img width="915" height="601" alt="Screenshot 2025-11-21 185929" src="https://github.com/user-attachments/assets/4d61a1df-7e57-4a5f-9c11-bfc7f57feec5" />
  <br><br>
  <img width="894" height="602" alt="Screenshot 2025-11-21 185957" src="https://github.com/user-attachments/assets/c8e235ef-48b1-48d8-8547-c982015d3be5" />

- Explanation

  - Jalankan perintah berikut di router-4
  ```
  apt update
  apt install iptables
  iptables -A FORWARD -s 10.193.2.1 -d 10.193.2.128/27 -p tcp --dport 22 -j ACCEPT
  iptables -A FORWARD -s 10.193.2.2 -d 10.193.2.128/27 -p tcp --dport 22 -j ACCEPT
  iptables -A FORWARD -s 10.193.2.3 -d 10.193.2.128/27 -p tcp --dport 22 -j ACCEPT
  iptables -A FORWARD -s 10.193.2.1 -d 10.193.2.160/27 -p tcp --dport 22 -j ACCEPT
  iptables -A FORWARD -s 10.193.2.2 -d 10.193.2.160/27 -p tcp --dport 22 -j ACCEPT
  iptables -A FORWARD -s 10.193.2.3 -d 10.193.2.160/27 -p tcp --dport 22 -j ACCEPT
  iptables -A FORWARD -d 10.193.2.128/27 -p tcp --dport 22 -j DROP
  iptables -A FORWARD -d 10.193.2.160/27 -p tcp --dport 22 -j DROP
  ```
  - Selanjutnya bisa di testing dengan netcat dari node IT-PC mengarah ke web dan testing juga dengan node selain itu
  ```
  nc 10.193.2.129 22 -v
  nc 10.193.2.161 22 -v
  ```
  - Jika ingin menampilkan SSH jalankan perintah berikut di web server
  ```
  apt-get update
  apt-get install openssh-server -y
  service ssh start
  ```
  - Bisa di testing ulang dengan netcat di IT-PC nanti akan menampilkan SSH

<br>

## Soal 7

> Semua subnet hanya dapat mengakses semua DB-Server pada port 80 dan 443 (DB-Server-1 dan DB-Server-2) pada hari Senin-Sabtu, pukul 07:00- 22:00.

> _All subnets can only access all DB-Servers on ports 80 and 443 (DB-Server-1 and DB-Server-2) on Monday-Saturday, 07:00-22:00._

**Answer:**

- Screenshot

  <img width="602" height="162" alt="Screenshot 2025-11-21 190237" src="https://github.com/user-attachments/assets/2b7d8d1f-e838-4d15-b05e-e6c3b8898842" />
  <br><br>
  <img width="543" height="300" alt="Screenshot 2025-11-21 190357" src="https://github.com/user-attachments/assets/d274a4bc-4fd0-4412-9a4b-72dfe5c3e297" />
  <br><br>
  <img width="892" height="605" alt="Screenshot 2025-11-21 190406" src="https://github.com/user-attachments/assets/9376550b-b2b4-49a7-ac09-2871f1611210" />
  <br><br>

- Explanation

  - Jalankan perintah berikut di router-3
  ```
  iptables -A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT
  iptables -A FORWARD -p tcp -m multiport --dports 80,443 -d 10.193.2.192/27 -m time --timestart 07:00 --timestop 22:00 --weekdays Mon,Tue,Wed,Thu,Fri,Sat -j ACCEPT
  iptables -A FORWARD -p tcp -m multiport --dports 80,443 -d 10.193.2.192/27 -j DROP
  iptables -A FORWARD -p tcp -m multiport --dports 80,443 -d 10.193.2.224/28 -m time --timestart 07:00 --timestop 22:00 --weekdays Mon,Tue,Wed,Thu,Fri,Sat -j ACCEPT
  iptables -A FORWARD -p tcp -m multiport --dports 80,443 -d 10.193.2.224/28 -j DROP
  ```
  - Di bagian router-3 bisa menjalankan perintah berikut untuk melakukan testing ketika memasuki range waktu tersebut dan diluar range waktu tersebut
  ```
  date -s "2025-11-24 10:00:00"
  date -s "2025-11-23 10:00:00"
  ```
  - Setelah itu bisa testing dengan netcat yang mengarah ke IP DB-Server berikut ini contoh mengeceknya
  ```
  nc 10.193.2.225 80 -v
  ```

<br>

## Soal 8

> Kemudian, buat agar “Web-Server-1” dan “Web-Server-2” hanya memperbolehkan traffic bertipe HTTP.

> _Then, make sure that “Web-Server-1” and “Web-Server-2” only allow HTTP type traffic._

**Answer:**

- Screenshot

  <img width="907" height="615" alt="Screenshot 2025-11-21 191014" src="https://github.com/user-attachments/assets/4247d7df-855a-467b-a944-947eba2ed65c" />
  <br><br>
  <img width="912" height="617" alt="image" src="https://github.com/user-attachments/assets/af003401-9e16-418f-8867-7fa492ad4051" />
  <br><br>
  <img width="915" height="617" alt="image" src="https://github.com/user-attachments/assets/bf28fc91-64e8-4456-aa43-0b10304481c6" />
  <br><br>

- Explanation

  - Bisa langsung menjalankan perintah berikut di router-4
  ```
  iptables -F FORWARD
  iptables -A FORWARD -p tcp --dport 80 -d 10.193.2.128/27 -j ACCEPT
  iptables -A FORWARD -p tcp --dport 80 -d 10.193.2.160/27 -j ACCEPT
  iptables -A FORWARD -d 10.193.2.128/27 -j DROP
  iptables -A FORWARD -d 10.193.2.160/27 -j DROP
  ```
  - Setelah itu testing bisa menggunakan netcat dari node selain Web-Server dan bisa juga bisa menggunakan curl dari node HR ke ip Web-Server harus dijalankan dahulu setup web-server nanti akan menampilkan file html

<br>

## Soal 9

> Pilih salah satu Subnet dan lakukan blokir terhadap semua request protokol ICMP (ping) dari luar subnet terhadap subnet tersebut.

> _Select one of the Subnets and block all ICMP protocol requests (ping) from outside the subnet to that subnet._

**Answer:**

- Screenshot

  <img width="904" height="603" alt="Screenshot 2025-11-21 191914" src="https://github.com/user-attachments/assets/36ee1e99-11a3-421f-9f9f-9ae310e4ba16" />
  <br><br>
  <img width="892" height="597" alt="Screenshot 2025-11-21 191920" src="https://github.com/user-attachments/assets/804635da-c200-4407-97af-29ed9038c7b6" />
  <br><br>

- Explanation

  - Bisa langsung menjalankan perintah berikut di router-5 saya memilih subnetnya HR
  ```
  iptables -F FORWARD
  iptables -A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT
  iptables -A FORWARD -p icmp -s 10.193.0.0/23 -j ACCEPT
  iptables -A FORWARD -p icmp -d 10.193.0.0/23 -j DROP
  ```
  - Langsung testing ping dari HR ke node lain dan coba juga dari node lain ke HR 

<br>

## Soal 10

> Konfigurasikan fitur logging untuk melakukan log terhadap seluruh paket yang di-DROP pada lalu lintas setiap node.

> _Configure the logging feature to log all dropped packets on each node's traffic._

**Answer:**

- Screenshot

  <img width="904" height="607" alt="Screenshot 2025-11-21 213728" src="https://github.com/user-attachments/assets/664b6a41-a073-49bb-bd06-a278793548b8" />
  <br><br>
  <img width="1912" height="844" alt="Screenshot 2025-11-21 213759" src="https://github.com/user-attachments/assets/e460e3b2-3824-4446-bbde-96ba8a5f60d6" />
  <br><br>
  <img width="909" height="613" alt="Screenshot 2025-11-21 214308" src="https://github.com/user-attachments/assets/dd6bf43e-2cfe-4007-bc84-cef8a1c3b416" />
  <br><br>
  <img width="1901" height="800" alt="Screenshot 2025-11-21 214356" src="https://github.com/user-attachments/assets/fdb71578-40ba-4023-97c5-d89cb31fb73a" />
  <br><br>
  <img width="903" height="611" alt="Screenshot 2025-11-21 214414" src="https://github.com/user-attachments/assets/6540ae8a-bcae-42f0-a7ec-f600d3ee0e19" />
  <br><br>
  <img width="1918" height="792" alt="Screenshot 2025-11-21 214426" src="https://github.com/user-attachments/assets/b9c6ad68-e35b-424a-b743-e4dde46a75ed" />
  <br><br>


- Explanation

  - Bisa menjalankan perintah berikut ini
  ```
  router 4
  iptables -N LOG_AND_DROP
  iptables -A LOG_AND_DROP -j LOG --log-prefix "R4-WEB-BLOCK: " --log-level 4
  iptables -A LOG_AND_DROP -j DROP
  iptables -F FORWARD
  iptables -A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT
  iptables -A FORWARD -s 10.193.2.128/27 -j ACCEPT
  iptables -A FORWARD -s 10.193.2.160/27 -j ACCEPT
  iptables -A FORWARD -p tcp --dport 80 -d 10.193.2.128/27 -j ACCEPT
  iptables -A FORWARD -p tcp --dport 80 -d 10.193.2.160/27 -j ACCEPT
  iptables -A FORWARD -d 10.193.2.128/27 -j LOG_AND_DROP
  iptables -A FORWARD -d 10.193.2.160/27 -j LOG_AND_DROP
  
  router5
  iptables -N LOG_AND_DROP
  iptables -A LOG_AND_DROP -j LOG --log-prefix "R5-HR-BLOCK: " --log-level 4
  iptables -A LOG_AND_DROP -j DROP
  iptables -F FORWARD
  iptables -A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT
  iptables -A FORWARD -s 10.193.0.0/23 -j ACCEPT
  iptables -A FORWARD -d 10.193.0.0/23 -p tcp --dport 1337 -j LOG_AND_DROP
  iptables -A FORWARD -d 10.193.0.0/23 -p tcp --dport 4444 -j LOG_AND_DROP
  iptables -A FORWARD -d 10.193.0.0/23 -p icmp -j LOG_AND_DROP
  
  router3
  iptables -N LOG_AND_DROP
  iptables -A LOG_AND_DROP -j LOG --log-prefix "R3-DB-BLOCK: " --log-level 4
  iptables -A LOG_AND_DROP -j DROP
  iptables -F FORWARD
  iptables -A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT
  iptables -A FORWARD -d 10.193.2.192/27 -p tcp -m multiport --dports 80,443 -m time --timestart 07:00 --timestop 22:00 --weekdays Mon,Tue,Wed,Thu,Fri,Sat -j ACCEPT
  iptables -A FORWARD -d 10.193.2.224/28 -p tcp -m multiport --dports 80,443 -m time --timestart 07:00 --timestop 22:00 --weekdays Mon,Tue,Wed,Thu,Fri,Sat -j ACCEPT
  iptables -A FORWARD -d 10.193.2.192/27 -j LOG_AND_DROP
  iptables -A FORWARD -d 10.193.2.224/28 -j LOG_AND_DROP
  ```
  - Untuk testing bisa dari node IT dengan netcat ke web-server,db-server dan testing dengan ping ke node HR contohnya seperti berikut dengan menjalankan perintah ini
  ```
  nc 10.193.2.161 22 -v
  nc 10.193.2.193 80 -v
  ping 10.193.0.2
  ```
  - Untuk mengeceknya bisa dibagian router dengan menjalankan perintah berikut bisa dilihat jumlah packet yang dicatat kedalam log dan yang di drop
  ```
  iptables -nvL
  ```

<br>
  
## Problems

## Revisions (if any)
