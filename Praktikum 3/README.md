[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/e_s827HM)
| Name           | NRP        | Kelas     |
| ---            | ---        | ----------|
| Muhamad Aziz Romdhoni | 5025241071 | C |



## Put your topology config image here!

<img width="1920" height="1020" alt="Screenshot 2025-10-31 165326" src="https://github.com/user-attachments/assets/3a8717b8-6441-4af7-93e8-e66278268eba" />

## Put your GNS3 Project file here!

https://drive.google.com/file/d/1-p48JEuJpqv2Jiz54w6JS6Rc5aa_8iAi/view?usp=sharing

<br>

## Soal 1

> Setup Topo

> _Document the results of the subnet grouping that has been created._

**Answer:**

- Screenshot

  <img width="1920" height="1020" alt="10 193" src="https://github.com/user-attachments/assets/8e28b16b-9a97-4efe-96a0-c60083c49dae" />

- Explanation

  - Set up config sesuai dengan subnet yang diberikan oleh soal
  - Config subnet 10.193.2.X
    - Lune
    ```
    auto eth0
    iface eth0 inet static
      address 10.193.2.1
      netmask 255.255.0.0
    ```
    - Sciel
    ```
    auto eth0
    iface eth0 inet static
	    address 10.193.2.2
	    netmask 255.255.0.0
    ```
    - Gustave
    ```
    auto eth0
    iface eth0 inet static
	    address 10.193.2.3
	    netmask 255.255.0.0
    ```
  - Config subnet 10.193.3.X
    - Renoir
    ```
    auto eth0
    iface eth0 inet static
	    address 10.193.3.1
	    netmask 255.255.0.0
    ```
    - Verso
    ```
    auto eth0
    iface eth0 inet static
	    address 10.193.3.2
	    netmask 255.255.0.0
    ```
  - Config subnet 10.193.4.X
    - Alicia
    ```
    auto eth0
    iface eth0 inet static
	    address 10.193.4.1
	    netmask 255.255.0.0
    ```
  - Config subnet 10.193.5.X
    - Esquie
    ```
    auto eth0
    iface eth0 inet static
	    address 10.193.5.1
	    netmask 255.255.0.0
  	  up echo nameserver 10.193.3.1 > /etc/resolv.conf
	    up echo nameserver 10.193.3.2 >> /etc/resolv.conf
    ```
    - Monoco
    ```
    auto eth0
    iface eth0 inet static
    	address 10.193.5.2
    	netmask 255.255.0.0
    	up echo nameserver 10.193.3.1 > /etc/resolv.conf
    	up echo nameserver 10.193.3.2 >> /etc/resolv.conf
    ```
    - Maele
    ```
    auto eth0
    iface eth0 inet static
    	address 10.193.5.3
    	netmask 255.255.0.0
    	up echo nameserver 10.193.3.1 > /etc/resolv.conf
    	up echo nameserver 10.193.3.2 >> /etc/resolv.conf
    ```
    - netics-pc-desktop-1
    ```
    auto eth0
    iface eth0 inet static
    	address 10.193.5.4
    	netmask 255.255.0.0
    	up echo -e "nameserver 10.193.3.1\nnameserver 10.193.3.2" > /etc/resolv.conf
    ```
<br>

## Soal 2

> Buatlah konfigurasi untuk domain 
> **lune33.com** → ke IP node Lune , 
> **sciel33.com** → ke IP node Sciel ,
> **gustave33.com** → ke IP node Gustave 
> pada DNS Master Renoir. Kemudian konfigurasikan node Verso sebagai DNS Slave yang bekerja untuk DNS Master Renoir.

> _Dns Configuration , on  the DNS Master (Renoir)_
> _lune33.com → IP of node Lune ,_
> _sciel33.com → IP of node Sciel ,_
> _gustave33.com → IP of node Gustave_
> _Configure Verso as the DNS Slave that works with DNS Master Renoir._

**Answer:**

- Screenshot

  <img width="1920" height="1020" alt="Screenshot 2025-10-31 174042" src="https://github.com/user-attachments/assets/799615cf-69cd-4fc3-8dde-8c7e19f447d6" />
  <br> <br>
  <img width="1920" height="1020" alt="Screenshot 2025-10-31 174053" src="https://github.com/user-attachments/assets/63534f06-ea48-4660-adb1-29a0d1a001d3" />
  <br> <br>
  <img width="1920" height="1020" alt="Screenshot 2025-10-31 174106" src="https://github.com/user-attachments/assets/5bd2b0c1-c44e-4bc2-b2f1-856dae58528f" />
  <br> <br>
  <img width="1920" height="1020" alt="Screenshot 2025-10-31 180625" src="https://github.com/user-attachments/assets/c1d8f6a3-cf7c-43a2-a61a-a3bf8aad5b7d" />
  <br> <br>
  <img width="1920" height="1020" alt="Screenshot 2025-10-31 180656" src="https://github.com/user-attachments/assets/e08b3fb5-dbf8-4a3e-822f-0f01709fc084" />
  <br><br>
  
- Explanation

  - Renoir 
    - Pertama tama adalah membuat direktori `dns` di dalam folder `/myscripts` 
    ```
    mkdir /myscripts/dns
    ```
    - Selanjutnya membuat file `named.conf`
    ```
    options {
      directory "/myscripts/dns";
      listen-on { any; };
      allow-query { any; };
    };
    
    zone "lune33.com" {
            type master;
            notify yes;
            also-notify { 10.193.3.2; };
            allow-transfer { 10.193.3.2; };
            file "db.lune33.com";
    };
    
    zone "sciel33.com" {
            type master;
            notify yes;
            also-notify { 10.193.3.2; };
            allow-transfer { 10.193.3.2; };
            file "db.sciel33.com";
    };
    
    zone "gustave33.com" {
            type master;
            notify yes;
            also-notify { 10.193.3.2; };
            allow-transfer { 10.193.3.2; };
            file "db.gustave33.com";
    };
  
    ```
    - Kemudian membuat file yang berkaitan dengan `named.conf` yaitu, `db.lune33.com`, `db.sciel33.com`, dan `db.gustave33.com`
      - `db.lune33.com`
      ```
      ;
      ; BIND data file for local loopback interface
      ;
      $TTL    604800
      @       IN      SOA     lune33.com. root.lune33.com. (
                           2022100601         ; Serial
                               604800         ; Refresh
                                86400         ; Retry
                              2419200         ; Expire
                               604800 )       ; Negative Cache TTL
      ;
      @       IN      NS      lune33.com.
      @       IN      A       10.193.2.1
      ```
      - `db.sciel33.com`
      ```
      ;
      ; BIND data file for local loopback interface
      ;
      $TTL    604800
      @       IN      SOA     sciel33.com. root.sciel33.com. (
                           2022100601         ; Serial
                               604800         ; Refresh
                                86400         ; Retry
                              2419200         ; Expire
                               604800 )       ; Negative Cache TTL
      ;
      @       IN      NS      sciel33.com.
      @       IN      A       10.193.2.2
      ```
      - `db.gustave33.com`
      ```
      ;
      ; BIND data file for local loopback interface
      ;
      $TTL    604800
      @       IN      SOA     gustave33.com. root.gustave33.com. (
                           2022100601         ; Serial
                               604800         ; Refresh
                                86400         ; Retry
                              2419200         ; Expire
                               604800 )       ; Negative Cache TTL
      ;
      @              IN      NS      gustave33.com.
      @              IN      A       10.193.2.3
      ```
    - Setelah itu membuat file `start_dns.sh`
    ```
    #!/bin/sh
    
    named -g -c /myscripts/dns/named.conf
    ```
    - Lalu ketikkan perintah ``chmod +x start_dns.sh``
    - Jalankan dengan cara ``/myscript/dns/start_dns.sh`` di root
  - Veso
    - Pertama tama adalah membuat direktori di dalam folder `/myscripts`
    ```
    mkdir /myscripts/dns
    ```
    - Selanjutnya membuat file bernama `named.conf`
    ```
    options {
    directory "/myscripts/dns";
    listen-on { any; };
    allow-query { any; };
    };
    
    zone "lune33.com" {
            type slave;
            masters { 10.193.3.1; };
            file "/var/cache/bind/db.lune33.com";
    };
    
    zone "sciel33.com" {
            type slave;
            masters { 10.193.3.1; };
            file "/var/cache/bind/db.sciel33.com";
    };
    
    zone "gustave33.com" {
            type slave;
            masters { 10.193.3.1; };
            file "/var/cache/bind/db.gustave33.com";
    };
    ```
    - Setelah itu membuat file `start_dns.sh`
    ```
    #!/bin/sh
    
    named -g -c /myscripts/dns/named.conf
    ```
    - Lalu ketikkan perintah ``chmod +x start_dns.sh``
    - Jalankan dengan cara ``/myscript/dns/start_dns.sh`` di root
  - Client Esquie, Monoco, Maele
    - Barulah arahkan nameserver dari client menuju DNS master dan DNS slave dengan menjalankan perintah ``nano /etc/resolv.conf``
    ```
    nameserver 10.193.3.1
    nameserver 10.193.3.2
    ```
    - Bisa juga langsung menaruhnya di config
    ```
    up echo nameserver 10.193.3.1 > /etc/resolv.conf
  	up echo nameserver 10.193.3.2 >> /etc/resolv.conf
  
    ```
    - Setelah itu baru bisa melakukan ping dari client dengan menjalankan peritah berikut
    ```
    ping lune33.com
    ping sciel33.com
    ping gustave33.com
    ```
<br>

## Soal 3

> Tambahkan subdomain alias berupa exp.lune33.com yang mengarah ke alamat lune33.com dan exp.sciel33.com yang mengarah ke alamat sciel33.com (HINT: CNAME). Selain itu, tambahkan konfigurasi untuk melakukan reverse DNS lookup untuk domain gustave33.com

> _Subdomain Configuration,_ 
> _Add alias subdomains (HINT: CNAME)._
> _exp.lune33.com → alias to lune33.com_
> _exp.sciel33.com → alias to sciel33.com_
> _Also, configure reverse DNS lookup for the domain gustave33.com._

**Answer:**

- Screenshot

  <img width="1920" height="1020" alt="Screenshot 2025-10-31 174042" src="https://github.com/user-attachments/assets/d5043bdc-e936-4513-abc4-8a4d533b4c9b" />
  <br><br>
  <img width="1920" height="1020" alt="Screenshot 2025-10-31 174053" src="https://github.com/user-attachments/assets/790e3fe5-c630-4f21-bf8e-ab70c99d776b" />
  <br><br>
  <img width="1920" height="1020" alt="Screenshot 2025-10-31 185021" src="https://github.com/user-attachments/assets/df2eab41-df03-4518-9db7-993539f82d86" />
  <br><br>
  <img width="1920" height="1020" alt="Screenshot 2025-10-31 185145" src="https://github.com/user-attachments/assets/bcfb59a9-c82f-4ec0-9181-66c1f19e6d7c" />
  <br><br>
  <img width="1920" height="1020" alt="Screenshot 2025-10-31 185152" src="https://github.com/user-attachments/assets/2bd54027-9ca1-42ba-a962-5b7ff81c6c1b" />
  <br><br>

- Explanation

  - Renoir
    - Pertama tama edit file `db.lune33.com` dan `db.sciel33.com`
      - `db.lune33.com`
      ```
      ;
      ; BIND data file for local loopback interface
      ;
      $TTL    604800
      @       IN      SOA     lune33.com. root.lune33.com. (
                           2022100601         ; Serial
                               604800         ; Refresh
                                86400         ; Retry
                              2419200         ; Expire
                               604800 )       ; Negative Cache TTL
      ;
      @       IN      NS      lune33.com.
      @       IN      A       10.193.2.1
      exp     IN      CNAME   lune33.com.
      ```
      - `db.sciel33.com`
      ```
      ;
      ; BIND data file for local loopback interface
      ;
      $TTL    604800
      @       IN      SOA     sciel33.com. root.sciel33.com. (
                           2022100601         ; Serial
                               604800         ; Refresh
                                86400         ; Retry
                              2419200         ; Expire
                               604800 )       ; Negative Cache TTL
      ;
      @       IN      NS      sciel33.com.
      @       IN      A       10.193.2.2
      exp     IN      CNAME   sciel33.com.
      ```
    - Edit config `named.conf` dan tambahkan
    ```
    zone "2.193.10.in-addr.arpa" {
          type master;
          notify yes;
          also-notify { 10.193.3.2; };
          allow-transfer { 10.193.3.2; };
          file "db.2.193.10.in-addr.arpa";
    };
    ```
    - Lalu buat file baru `db.2.193.10.in-addr.arpa`
    ```
    ;
    ; BIND data file for local loopback interface
    ;
    $TTL    604800
    @       IN      SOA     gustave33.com. root.gustave33.com. (
                         2022100601         ; Serial
                             604800         ; Refresh
                              86400         ; Retry
                            2419200         ; Expire
                             604800 )       ; Negative Cache TTL
    ;
    2.193.10.in-addr.arpa. IN      NS      gustave33.com.
    3                      IN      PTR     gustave33.com.
    ```
  - Verso
    - Edit config di `named.conf` tambahkan
    ```
    zone "2.193.10.in-addr.arpa" {
        type slave;
        masters { 10.193.3.1; };
        file "/var/cache/bind/db.2.193.10.in-addr.arpa";
    };
    ```
  - Client
    - Bisa di tes dengan menjalankan perintah berikut
    ```
    host -t CNAME exp.lune33.com
    ping exp.lune33.com -c 5
    host -t CNAME exp.sciel33.com
    ping exp.sciel33.com -c 5
    host -t PTR 10.193.2.3  
    ```

<br>

## Soal 4

> Buatlah subdomain berupa expedition.gustave33.com dan delegasikan subdomain tersebut dari Renoir ke Verso dengan alamat IP tujuan adalah node Gustave. Kemudian, matikan Renoir dan coba lakukan ping ke semua domain dan subdomain yang telah dikonfigurasikan pada nomor 2, 3, dan 4.

> _Create a subdomain expedition.gustave33.com and delegate it from Renoir to Verso, with the target IP being node Gustave.Then, turn off Renoir and try pinging all domains and subdomains configured in tasks 2, 3, and 4 to verify delegation works correctly._

**Answer:**

- Screenshot

  - Ketika Renoir dan Verso dijalankan
  <img width="1920" height="1020" alt="Screenshot 2025-10-31 192424" src="https://github.com/user-attachments/assets/59d6284f-5cde-43e8-902b-7902ab12dbb3" />
  <br><br>
  <img width="1920" height="1020" alt="Screenshot 2025-10-31 192431" src="https://github.com/user-attachments/assets/8d557a0b-e8c2-473f-ac16-9c0f5f9e062a" />
  <br><br>
  <img width="1920" height="1020" alt="Screenshot 2025-10-31 192831" src="https://github.com/user-attachments/assets/34c95867-4a31-4017-b41a-601e9e88f18f" />
  <br><br>
  - Ketika Renoir dimatikan dan Verso dijalankan
  <img width="1920" height="1020" alt="Screenshot 2025-10-31 192841" src="https://github.com/user-attachments/assets/a2809616-4c72-4ed6-b7b5-202453e6c015" />
  <br><br>
  <img width="1920" height="1020" alt="Screenshot 2025-10-31 192851" src="https://github.com/user-attachments/assets/36a06d76-1c9e-4b31-9127-4c66a563dcc2" />
  <br><br>
  <img width="1920" height="1020" alt="Screenshot 2025-10-31 193001" src="https://github.com/user-attachments/assets/40e48cdb-5e53-402e-87dc-f53f0267868d" />
  <br><br>

- Explanation

  - Renoir
    - Edit file `db.gustave33.com` seperti ini
    ```
    ;
    ; BIND data file for local loopback interface
    ;
    $TTL    604800
    @       IN      SOA     gustave33.com. root.gustave33.com. (
                         2022100601         ; Serial
                             604800         ; Refresh
                              86400         ; Retry
                            2419200         ; Expire
                             604800 )       ; Negative Cache TTL
    ;
    @           IN      NS      gustave33.com.
    @           IN      A       10.193.2.3
    ns1         IN      A       10.193.3.2
    expedition  IN      NS      ns1.expedition.gustave33.com
    ```
  - Verso
    - Edit file `named.conf` tambahkan
    ```
    zone "expedition.gustave33.com" {
        type master;
        file "db.gustave33.com";
    };
    ```
    - Buat file baru di verso dengan nama `db.gustave33.com` 
    ```
    ;
    ; BIND data file for local loopback interface
    ;
    $TTL    604800
    @       IN      SOA    expedition.gustave33.com. root.gustave33.com. (
                         2022100601         ; Serial
                             604800         ; Refresh
                              86400         ; Retry
                            2419200         ; Expire
                             604800 )       ; Negative Cache TTL
    ;
    @           IN      NS      ns1.expedition.gustave33.com.
    @           IN      A       10.193.2.3
    ns1         IN      A       10.193.3.2
    ```
  - Client Esqui, Monoco, Maele
    - Bisa di tes dengan menjalankan perintah berikut
    ```
    host -t CNAME exp.lune33.com
    ping exp.lune33.com -c 5
    host -t CNAME exp.sciel33.com
    ping exp.sciel33.com -c 5
    host -t PTR 10.193.2.3
    ping expedition.gustave33.com -c 5
    ```
<br>

## Soal 5

> Konfigurasi node Lune, Sciel, dan Gustave agar berfungsi sebagai web server Nginx yang akan menyajikan halaman profil, dimana halaman profil akan berbeda untuk setiap node. Dari folder berikut, gunakan profile_lune.html untuk menyajikan halaman profil di node Lune, profile_sciel.html untuk menyajikan halaman profil di node Sciel, dan profile_gustave.html untuk menyajikan halaman profil di node Gustave. Konfigurasikan Nginx di setiap node untuk menyimpan custom access log ke file /tmp/access.log dan error log ke file /tmp/error.log. 

> _Configure Lune, Sciel, and Gustave as Nginx web servers serving profile pages, where each node has a unique profile page:_
> _- Use profile_lune.html for Lune_
> _- Use profile_sciel.html for Sciel_
> _- Use profile_gustave.html for Gustave_
> _In each web server, Configure Nginx to store custom logs:_
> _- Access log: /tmp/access.log_
> _- Error log: /tmp/error.log_

**Answer:**

- Screenshot

  <img width="1920" height="1020" alt="Screenshot 2025-10-31 200132" src="https://github.com/user-attachments/assets/cc22ada1-3e20-44de-a2cf-70ada3cb5a31" />
  <br><br>
  <img width="1920" height="1020" alt="Screenshot 2025-10-31 200140" src="https://github.com/user-attachments/assets/49607fdb-fe51-4970-9e1a-d7e6e9395275" />
  <br><br>
  <img width="1920" height="1020" alt="Screenshot 2025-10-31 203631" src="https://github.com/user-attachments/assets/877b9b34-a2a1-4713-ac77-6a39b5b2e139" />
  <br><br>
  <img width="1920" height="1020" alt="Screenshot 2025-10-31 203641" src="https://github.com/user-attachments/assets/dd3e1e99-d0af-4e0c-994a-587fd311c127" />
  <br><br>
  <img width="1920" height="1020" alt="Screenshot 2025-10-31 203651" src="https://github.com/user-attachments/assets/4b07c9d0-e301-4a2d-987a-173cf01d0eca" />
  <br><br>
  <img width="1918" height="1079" alt="Screenshot 2025-10-31 205649" src="https://github.com/user-attachments/assets/5ca87ac0-c36a-45c0-96b0-fc5e29766475" />
  <br><br>
  <img width="1919" height="1079" alt="Screenshot 2025-10-31 205703" src="https://github.com/user-attachments/assets/e9fffb5b-1024-4f96-b9d9-9a12d9a9645b" />
  <br><br>
  <img width="1919" height="1079" alt="Screenshot 2025-10-31 205723" src="https://github.com/user-attachments/assets/5e3c9278-8cdf-445e-9b38-61f7fce2df61" />
  <br><br>

- Explanation

  - Lune
    - Buat direktori `myweb`,`myconfig`, dan file `start_http.sh` didalam folder `myscripts`
    - `myweb`
      - Masukkan file `profile_lune.html` yang ada di soal
      ```
      <!DOCTYPE html>
      <html lang="en">
      <head>
      <meta charset="UTF-8">
      <meta name="viewport" content="width=device-width, initial-scale=1.0">
      <title>Lune</title>
      <style>
        body {
          margin: 0;
          font-family: Arial, Helvetica, sans-serif;
          color: #fff;
          background: linear-gradient(270deg, #0a043c, #4a0c25, #7b1b0c, #f9a826);
          background-size: 800% 800%;
          animation: bgShift 20s ease infinite;
        }
        @keyframes bgShift {
          0% {background-position: 0% 50%;}
          50% {background-position: 100% 50%;}
          100% {background-position: 0% 50%;}
        }
        .container {
          max-width: 700px;
          margin: 4rem auto;
          background: rgba(255, 255, 255, 0.08);
          border-radius: 16px;
          padding: 2.5rem;
          box-shadow: 0 4px 20px rgba(0,0,0,0.5);
          backdrop-filter: blur(6px);
        }
        h1 {
          text-align: center;
          color: #00e5ff;
          text-shadow: 0 0 10px #00e5ff;
        }
        h2 {
          color: #ffd166;
          margin-top: 1.5rem;
        }
        p, li { line-height: 1.6; }
        ul { list-style: none; padding-left: 0; }
        li::before { content: "▹ "; color: #00e5ff; }
        footer { text-align: center; font-size: 0.85rem; color: #ccc; margin-top: 2rem; }
      </style>
      </head>
      <body>
        <div class="container">
          <h1>Lune</h1>
          <p><i>“When one falls, we continue.”</i></p>
      
          <h2>Core Expertise</h2>
          <ul>
            <li>Analysis of Ancient Technologies</li>
            <li>Equipment Calibration & Field Maintenance</li>
            <li>Defense System Deployment</li>
            <li>Data Collection & Anomaly Detection</li>
          </ul>
      
          <h2>Profile Summary</h2>
          <p>Lune is the mind behind the expedition’s technology. 
             Her understanding of ancient mechanisms and magical artifacts 
             is key to decoding the Paintress’ secrets and keeping the team operational.</p>
        </div>
      
        <footer>© 2025 Expedition 33 — For Those Who Come After</footer>
      </body>
      </html>
      ```
    - `myconfig`
      - Buat file `nginx.conf`
      ```
      user www-data;
      worker_processes auto;
      worker_cpu_affinity auto;
      pid /tmp/nginx.pid;
      error_log  /tmp/error.log;
      
      events { worker_connections 768; }
      
      http {
      access_log /tmp/access.log;
          server {
              listen 80;
              server_name _;
      
              root /myscripts/myweb;
              index profile_lune.html;
      
              location / {
                  try_files $uri $uri/ =404;
              }
          }
      }
      ```
    - Buat file `start_http.sh` untuk menjalankan nginx
    ```
    #!/bin/bash
    
    nginx -c /myscripts/myconfig/nginx.conf -g 'daemon off;'
    ```
      - Lalu jalankan perintah berikut: chmod +x start_http.sh
      - Jalankan nginx dengan perintah berikut /myscripts/start_http.sh
    - Client Esquie, Monoco, Maele
      - Bisa menjalankan perintah berikut untuk melakukan tesnya
      ```
      curl lune33.com
      ```
    - Bisa juga mengetesnya di vnc viewer
    - Cek acces dan error log di web server yaitu dengan cara
    ```
    tmux
    ```
      - Gunakan tmux untuk membagi dua layar terminal lalu tekan ctrl + b, shift + 5 
      - jalankan perintah berikut di salah satu layar terminal
      ```
      myscripts/start_http.sh 
      ```
      - Jalnkan perintah berikut di selain layar terminal tersebut dengan menekan ctrl+b o untuk mengganti ke layar sebelah
      ```
      cat /tmp/error.log
      cat /tmp/access.log
      ```
  - Sciel
    - Buat direktori `myweb`,`myconfig`, dan file `start_http.sh` didalam folder `myscripts`
    - `myweb`
      - Masukkan file `profile_sciel.html` yang ada di soal
      ```
      <!DOCTYPE html>
      <html lang="en">
      <head>
      <meta charset="UTF-8">
      <meta name="viewport" content="width=device-width, initial-scale=1.0">
      <title>Sciel</title>
      <style>
        body {
          margin: 0;
          font-family: Arial, Helvetica, sans-serif;
          color: #fff;
          background: linear-gradient(270deg, #0a043c, #4a0c25, #7b1b0c, #f9a826);
          background-size: 800% 800%;
          animation: bgShift 20s ease infinite;
        }
        @keyframes bgShift {
          0% {background-position: 0% 50%;}
          50% {background-position: 100% 50%;}
          100% {background-position: 0% 50%;}
        }
        .container {
          max-width: 700px;
          margin: 4rem auto;
          background: rgba(255, 255, 255, 0.08);
          border-radius: 16px;
          padding: 2.5rem;
          box-shadow: 0 4px 20px rgba(0,0,0,0.5);
          backdrop-filter: blur(6px);
        }
        h1 {
          text-align: center;
          color: #00e5ff;
          text-shadow: 0 0 10px #00e5ff;
        }
        h2 {
          color: #ffd166;
          margin-top: 1.5rem;
        }
        p, li { line-height: 1.6; }
        ul { list-style: none; padding-left: 0; }
        li::before { content: "▹ "; color: #00e5ff; }
        footer { text-align: center; font-size: 0.85rem; color: #ccc; margin-top: 2rem; }
      </style>
      </head>
      <body>
        <div class="container">
          <h1>Sciel</h1>
          <p><i>“Tomorrow comes.”</i></p>
      
          <h2>Core Expertise</h2>
          <ul>
            <li>Stealth and Infiltration Tactics</li>
            <li>Long-Range Surveillance</li>
            <li>Navigation and Terrain Mapping</li>
            <li>Rapid Response & Target Acquisition</li>
          </ul>
      
          <h2>Profile Summary</h2>
          <p>Sciel serves as the eyes and ears of Expedition 33. 
             Agile and perceptive, he scouts ahead, tracks enemy movement, 
             and secures safe passage before every major confrontation.</p>
        </div>
      
        <footer>© 2025 Expedition 33 — For Those Who Come After</footer>
      </body>
      </html>
      ```
    - `myconfig`
      - Buat file `nginx.conf`
      ```
      user www-data;
      worker_processes auto;
      worker_cpu_affinity auto;
      pid /tmp/nginx.pid;
      error_log  /tmp/error.log;
      
      events { worker_connections 768; }
      
      http {
      access_log /tmp/access.log;
          server {
              listen 80;
              server_name _;
      
              root /myscripts/myweb;
              index profile_sciel.html;
      
              location / {
                  try_files $uri $uri/ =404;
              }
          }
      }
      ```
    - Buat file `start_http.sh` untuk menjalankan nginx
    ```
    #!/bin/bash
    
    nginx -c /myscripts/myconfig/nginx.conf -g 'daemon off;'
    ```
      - Lalu jalankan perintah berikut: chmod +x start_http.sh
      - Jalankan nginx dengan perintah berikut /myscripts/start_http.sh
    - Client Esquie, Monoco, Maele
      - Bisa menjalankan perintah berikut untuk melakukan tesnya
      ```
      curl sciel33.com
      ```
    - Bisa juga mengetesnya di vnc viewer
    - Cek acces dan error log di web server yaitu dengan cara
    ```
    tmux
    ```
      - Gunakan tmux untuk membagi dua layar terminal lalu tekan ctrl + b, shift + 5 
      - jalankan perintah berikut di salah satu layar terminal
      ```
      myscripts/start_http.sh 
      ```
      - Jalnkan perintah berikut di selain layar terminal tersebut dengan menekan ctrl+b o untuk mengganti ke layar sebelah
      ```
      cat /tmp/error.log
      cat /tmp/access.log
      ```
  - Gustave
    - Buat direktori `myweb`,`myconfig`, dan file `start_http.sh` didalam folder `myscripts`
    - `myweb`
      - Masukkan file `profile_sciel.html` yang ada di soal
      ```
      <!DOCTYPE html>
      <html lang="en">
      <head>
      <meta charset="UTF-8">
      <meta name="viewport" content="width=device-width, initial-scale=1.0">
      <title>Gustave</title>
      <style>
        body {
          margin: 0;
          font-family: Arial, Helvetica, sans-serif;
          color: #fff;
          background: linear-gradient(270deg, #0a043c, #4a0c25, #7b1b0c, #f9a826);
          background-size: 800% 800%;
          animation: bgShift 20s ease infinite;
        }
        @keyframes bgShift {
          0% {background-position: 0% 50%;}
          50% {background-position: 100% 50%;}
          100% {background-position: 0% 50%;}
        }
        .container {
          max-width: 700px;
          margin: 4rem auto;
          background: rgba(255, 255, 255, 0.08);
          border-radius: 16px;
          padding: 2.5rem;
          box-shadow: 0 4px 20px rgba(0,0,0,0.5);
          backdrop-filter: blur(6px);
        }
        h1 {
          text-align: center;
          color: #00e5ff;
          text-shadow: 0 0 10px #00e5ff;
        }
        h2 {
          color: #ffd166;
          margin-top: 1.5rem;
        }
        p, li {
          line-height: 1.6;
        }
        ul {
          list-style: none;
          padding-left: 0;
        }
        li::before {
          content: "▹ ";
          color: #00e5ff;
        }
        footer {
          text-align: center;
          font-size: 0.85rem;
          color: #ccc;
          margin-top: 2rem;
        }
      </style>
      </head>
      <body>
        <div class="container">
          <h1>Gustave</h1>
          <p><i>“For those who come after. Right?”</i></p>
      
          <h2>Core Expertise</h2>
          <ul>
            <li>Tactical Combat Planning</li>
            <li>Frontline Leadership & Morale Management</li>
            <li>Heavy Weapon Proficiency</li>
            <li>Risk Assessment & Survival Techniques</li>
          </ul>
      
          <h2>Profile Summary</h2>
          <p>Gustave is a battle-hardened veteran and the backbone of Expedition 33. 
             With experience from countless missions, he oversees every tactical decision 
             made in the war against the Paintress.</p>
        </div>
      
        <footer>© 2025 Expedition 33 — For Those Who Come After</footer>
      </body>
      </html>

      ```
    - `myconfig`
      - Buat file `nginx.conf`
      ```
      user www-data;
      worker_processes auto;
      worker_cpu_affinity auto;
      pid /tmp/nginx.pid;
      error_log  /tmp/error.log;
      
      events { worker_connections 768; }
      
      http {
      access_log /tmp/access.log;
          server {
              listen 80;
              server_name _;
      
              root /myscripts/myweb;
              index profile_gustave.html;
      
              location / {
                  try_files $uri $uri/ =404;
              }
          }
      }
      ```
    - Buat file `start_http.sh` untuk menjalankan nginx
    ```
    #!/bin/bash
    
    nginx -c /myscripts/myconfig/nginx.conf -g 'daemon off;'
    ```
      - Lalu jalankan perintah berikut: chmod +x start_http.sh
      - Jalankan nginx dengan perintah berikut /myscripts/start_http.sh
    - Client Esquie, Monoco, Maele
      - Bisa menjalankan perintah berikut untuk melakukan tesnya
      ```
      curl gustave33.com
      ```
    - Bisa juga mengetesnya di vnc viewer
    - Cek acces dan error log di web server yaitu dengan cara
    ```
    tmux
    ```
      - Gunakan tmux untuk membagi dua layar terminal lalu tekan ctrl + b, shift + 5 
      - jalankan perintah berikut di salah satu layar terminal
      ```
      myscripts/start_http.sh 
      ```
      - Jalnkan perintah berikut di selain layar terminal tersebut dengan menekan ctrl+b o untuk mengganti ke layar sebelah
      ```
      cat /tmp/error.log
      cat /tmp/access.log
      ```
<br>

## Soal 6

> Setelah website berhasil dideploy pada masing-masing node web server dan halaman dapat menampilkan profil yang sesuai,  buatlah custom access log ke file /tmp/access.log di masing-masing node web server menggunakan format log tertentu seperti di bawah:
> - Tanggal dan waktu akses dalam format standar log.
> - Nama node yang sedang diakses.
> - Alamat IP klien yang mengakses website.
> - Metode HTTP dan URI yang diakses oleh klien.
> - Status respons HTTP yang diberikan oleh server.
> - Jumlah byte yang dikirimkan dalam respons.
> - Waktu yang dihabiskan oleh server untuk menangani permintaan.
> - Contoh format log yang sesuai:
>   [01/Oct/2024:11:30:45 +0000] Jarkom Node Lune Access from 192.168.1.15 using method "GET /resep/bayam HTTP/1.1" returned status 200 with 2567 bytes sent in 0.038 seconds

> _After successfully deploying each website and verifying the correct profile page is displayed, create a custom access log in /tmp/access.log on each web server using the following format:_
> _- Date and time of access (standard log format)_
> _- Name of the node being accessed_
> _- IP address of the client accessing the website_
> _- HTTP method and URI accessed by the client_
> _- HTTP response status code_
> _- Number of bytes sent in the response_
> _- Time taken by the server to process the request_
> _- Example Log Format:_
> _[01/Oct/2024:11:30:45 +0000] Jarkom Node Lune Access from 192.168.1.15 using method "GET /resep/bayam HTTP/1.1" returned status 200 with 2567 bytes sent in 0.038 seconds_

**Answer:**

- Screenshot

  <img width="1920" height="1020" alt="Screenshot 2025-10-31 213814" src="https://github.com/user-attachments/assets/585fa777-7f09-49f6-874e-d57e05743a6f" />
  <br><br>
  <img width="1920" height="1020" alt="Screenshot 2025-10-31 213820" src="https://github.com/user-attachments/assets/0cd80d50-de1e-49ce-a709-909fa5f50b6d" />
  <br><br>
  <img width="1920" height="1020" alt="Screenshot 2025-10-31 213836" src="https://github.com/user-attachments/assets/84ff44b5-1608-4d29-a5cd-85e248ea723e" />
  <br><br>
- Explanation

  - Lune
    - Edit dibagian `/myscripts/myconfig/nginx.conf`
    ```
    user www-data;
    worker_processes auto;
    worker_cpu_affinity auto;
    pid /tmp/nginx.pid;
    error_log  /tmp/error.log;
    
    events { worker_connections 768; }
    
    http {
    log_format custom '[$time_local] Jarkom Node Lune Access from $remote_addr using method "$request" returned status $status with $body_bytes_sent bytes sent in $request_time seconds';
    access_log /tmp/access.log custom;
        server {
            listen 80;
            server_name _;
    
            root /myscripts/myweb;
            index profile_lune.html;
    
            location / {
                try_files $uri $uri/ =404;
            }
        }
    }  
    ```
  - Sciel
    - Edit dibagian `/myscripts/myconfig/nginx.conf`
    ```
    user www-data;
    worker_processes auto;
    worker_cpu_affinity auto;
    pid /tmp/nginx.pid;
    error_log  /tmp/error.log;
    
    events { worker_connections 768; }
    
    http {
    log_format custom '[$time_local] Jarkom Node Sciel Access from $remote_addr using method "$request" returned status $status with $body_bytes_sent bytes sent in $request_time seconds';
    access_log /tmp/access.log custom;
        server {
            listen 80;
            server_name _;
    
            root /myscripts/myweb;
            index profile_sciel.html;
    
            location / {
                try_files $uri $uri/ =404;
            }
        }
    }
    ```
  - Gustave
    - Edit dibagian `/myscripts/myconfig/nginx.conf`
    ```
    user www-data;
    worker_processes auto;
    worker_cpu_affinity auto;
    pid /tmp/nginx.pid;
    error_log  /tmp/error.log;
    
    events { worker_connections 768; }
    
    http {
    log_format custom '[$time_local] Jarkom Node Gustave Access from $remote_addr using method "$request" returned status $status with $body_bytes_sent bytes sent in $request_time seconds';
    access_log /tmp/access.log custom;
        server {
            listen 80;
            server_name _;
    
            root /myscripts/myweb;
            index profile_gustave.html;
    
            location / {
                try_files $uri $uri/ =404;
            }
        }
    }
    ```
    - Cek acces log di web server yaitu dengan cara
    ```
    tmux
    ```
      - Gunakan tmux untuk membagi dua layar terminal lalu tekan ctrl + b, shift + 5 
      - jalankan perintah berikut di salah satu layar terminal
      ```
      myscripts/start_http.sh 
      ```
      - Jalnkan perintah berikut di selain layar terminal tersebut dengan menekan ctrl+b o untuk mengganti ke layar sebelah
      ```
      cat /tmp/access.log
      ```

<br>

## Soal 7

> Gustave merupakan web server yang tidak disarankan untuk dilihat oleh publik. Maka dari itu, ubahlah konfigurasi nginx sehingga halaman profil Gustave menjadi hanya bisa di akses melalui port 8080 dan 8888.

> _The Gustave web server should not be publicly accessible.
Modify the Nginx configuration so that Gustave’s profile page can only be accessed through ports 8080 and 8888._

**Answer:**

- Screenshot

  <img width="1919" height="1079" alt="Screenshot 2025-10-31 215436" src="https://github.com/user-attachments/assets/5e833241-86e0-4844-a50e-6c1d0758154c" />
  <br><br>

- Explanation

  - Gustave
    - Edit dibagian `/myscripts/myconfig/nginx.conf`
    ```
    user www-data;
    worker_processes auto;
    worker_cpu_affinity auto;
    pid /tmp/nginx.pid;
    error_log  /tmp/error.log;
    
    events { worker_connections 768; }
    
    http {
    log_format custom '[$time_local] Jarkom Node Gustave Access from $remote_addr using method "$request" returned status $status with $body_bytes_sent bytes sent in $request_time seconds';
    access_log /tmp/access.log custom;
        server {
            listen 8080;
            listen 8888;
            server_name _;
    
            root /myscripts/myweb;
            index profile_gustave.html;
    
            location / {
                try_files $uri $uri/ =404;
            }
        }
    }
    ```
    - Lalu jalankan web servernya dengan `myscripts/start_http.sh`
  - Client
    - Cek dengan menjalankan perintah berikut
    ```
    curl gustave33.com
    ```
  - Bisa juga melihatnya di nvc dengan mengecek `gustave33.com`
<br>

## Soal 8

> Untuk mempermudah program ekspedisi, maka node Lune, Sciel, Gustave sepakat untuk membuat halaman informasi dengan konten yang sama. Maka dari itu, buatlah lagi 1 server block di dalam konfigurasi nginx yang akan menyajikan file HTML ini. Namun, mereka ingin menyajikan halaman informasi tersebut di port yang berbeda-beda, yaitu Lune menggunakan port 8000, Sciel menggunakan port 8100, dan Gustave menggunakan port 8200.

> _To simplify coordination for the expedition program, Lune, Sciel, and Gustave agree to create a shared information page with the same content. Add one more server block in each node’s Nginx configuration that serves this HTML file 
Each node should serve the information page on a different port:_
> _- Lune → port 8000_
> _- Sciel → port 8100_
> _- Gustave → port 8200_

**Answer:**

- Screenshot

  <img width="1919" height="1079" alt="Screenshot 2025-10-31 220725" src="https://github.com/user-attachments/assets/81ce43aa-1c0c-4939-8874-85b63483c5e6" />
  <br><br>
  <img width="1919" height="1079" alt="Screenshot 2025-10-31 220841" src="https://github.com/user-attachments/assets/c8df9839-2387-4f53-831f-c4d69229af2f" />
  <br><br>
  <img width="1919" height="1079" alt="Screenshot 2025-10-31 220854" src="https://github.com/user-attachments/assets/82e74198-9ba3-474e-9fbf-50e5693ddd03" />
  <br><br>

- Explanation

  - Lune
    - Buat file
    ```
    <!DOCTYPE html>
    <html lang="en">
    <head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Expedition Lune33 — Mission Brief</title>
    <style>
      body {
        margin: 0;
        font-family: Arial, Helvetica, sans-serif;
        color: #fff;
        background: linear-gradient(270deg, #0a043c, #4a0c25, #7b1b0c, #f9a826);
        background-size: 800% 800%;
        animation: bgShift 20s ease infinite;
      }
      @keyframes bgShift {
        0% {background-position: 0% 50%;}
        50% {background-position: 100% 50%;}
        100% {background-position: 0% 50%;}
      }
      header {
        text-align: center;
        padding: 3rem 1rem 1rem;
      }
      header h1 {
        font-size: 2.8rem;
        color: #00e5ff;
        letter-spacing: 1px;
        text-shadow: 0 0 10px #00e5ff;
      }
      header p {
        font-size: 1rem;
        color: #b5eaff;
        margin-top: 0.3rem;
      }
      .container {
        max-width: 700px;
        margin: 2rem auto 3rem;
        background: rgba(255, 255, 255, 0.08);
        border-radius: 16px;
        padding: 2rem 2.5rem;
        box-shadow: 0 4px 20px rgba(0,0,0,0.4);
        backdrop-filter: blur(6px);
      }
      h2 {
        color: #00e5ff;
        margin-top: 1.5rem;
      }
      p, li {
        line-height: 1.6;
      }
      ul {
        list-style: none;
        padding: 0;
      }
      li {
        margin: 0.4rem 0;
      }
      strong {
        color: #ffd166;
      }
      .motto {
        text-align: center;
        margin-top: 1.5rem;
        font-style: italic;
        color: #ccc;
        opacity: 0.9;
      }
      footer {
        text-align: center;
        font-size: 0.9rem;
        color: #ddd;
        padding: 1rem;
        background: rgba(0,0,0,0.4);
      }
    </style>
    </head>
    <body>
    <header>
      <h1>Expedition 33</h1>
      <p>Mission Log #E33-00</p>
    </header>
    
    <div class="container">
      <h2>Mission Brief</h2>
      <p>Expedition 33 is a digital exploration led by <strong>Lune</strong>, <strong>Sciel</strong>, and <strong>Gustave</strong>.  
         Together, they traverse the unknown layers of the Paintress system — seeking order within chaos.</p>
    
      <h2>Active Nodes</h2>
      <ul>
        <li><strong>Lune</strong> — “When one falls, we continue.”</li>
        <li><strong>Sciel</strong> — “Tomorrow comes.”</li>
        <li><strong>Gustave</strong> — “For those who come after. Right?”</li>
      </ul>
    
      <h2>Ports</h2>
      <ul>
        <li>Lune: Port <strong>8000</strong></li>
        <li>Sciel: Port <strong>8100</strong></li>
        <li>Gustave: Port <strong>8200</strong></li>
      </ul>
    
      <div class="motto">
        “Despite the odds, Expedition 33 marches forward.”
      </div>
    </div>
    
    <footer>
      © 2025 Expedition 33 — For Those Who Come After
    </footer>
    </body>
    </html>

    ```
    - Edit dibagian `/myscripts/myconfig/nginx.conf`
    ```
    user www-data;
    worker_processes auto;
    worker_cpu_affinity auto;
    pid /tmp/nginx.pid;
    error_log  /tmp/error.log;
    
    events { worker_connections 768; }
    
    http {
    log_format custom '[$time_local] Jarkom Node Lune Access from $remote_addr using method "$request" returned status $status with $body_bytes_sent bytes sent in $request_time seconds';
    access_log /tmp/access.log custom;
        server {
            listen 80;
            server_name _;
    
            root /myscripts/myweb;
            index profile_lune.html;
    
            location / {
                try_files $uri $uri/ =404;
            }
        }
    
        server {
            listen 8000;
            server_name _;
    
            root /myscripts/myweb;
            index info.html;
    
            location / {
                try_files $uri $uri/ =404;
            }
        }
    }
    ```
  - Sciel
    - Buat file
    ```
    <!DOCTYPE html>
    <html lang="en">
    <head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Expedition Sciel33 — Mission Brief</title>
    <style>
      body {
        margin: 0;
        font-family: Arial, Helvetica, sans-serif;
        color: #fff;
        background: linear-gradient(270deg, #0a043c, #4a0c25, #7b1b0c, #f9a826);
        background-size: 800% 800%;
        animation: bgShift 20s ease infinite;
      }
      @keyframes bgShift {
        0% {background-position: 0% 50%;}
        50% {background-position: 100% 50%;}
        100% {background-position: 0% 50%;}
      }
      header {
        text-align: center;
        padding: 3rem 1rem 1rem;
      }
      header h1 {
        font-size: 2.8rem;
        color: #00e5ff;
        letter-spacing: 1px;
        text-shadow: 0 0 10px #00e5ff;
      }
      header p {
        font-size: 1rem;
        color: #b5eaff;
        margin-top: 0.3rem;
      }
      .container {
        max-width: 700px;
        margin: 2rem auto 3rem;
        background: rgba(255, 255, 255, 0.08);
        border-radius: 16px;
        padding: 2rem 2.5rem;
        box-shadow: 0 4px 20px rgba(0,0,0,0.4);
        backdrop-filter: blur(6px);
      }
      h2 {
        color: #00e5ff;
        margin-top: 1.5rem;
      }
      p, li {
        line-height: 1.6;
      }
      ul {
        list-style: none;
        padding: 0;
      }
      li {
        margin: 0.4rem 0;
      }
      strong {
        color: #ffd166;
      }
      .motto {
        text-align: center;
        margin-top: 1.5rem;
        font-style: italic;
        color: #ccc;
        opacity: 0.9;
      }
      footer {
        text-align: center;
        font-size: 0.9rem;
        color: #ddd;
        padding: 1rem;
        background: rgba(0,0,0,0.4);
      }
    </style>
    </head>
    <body>
    <header>
      <h1>Expedition 33</h1>
      <p>Mission Log #E33-00</p>
    </header>
    
    <div class="container">
      <h2>Mission Brief</h2>
      <p>Expedition 33 is a digital exploration led by <strong>Lune</strong>, <strong>Sciel</strong>, and <strong>Gustave</strong>.  
         Together, they traverse the unknown layers of the Paintress system — seeking order within chaos.</p>
    
      <h2>Active Nodes</h2>
      <ul>
        <li><strong>Lune</strong> — “When one falls, we continue.”</li>
        <li><strong>Sciel</strong> — “Tomorrow comes.”</li>
        <li><strong>Gustave</strong> — “For those who come after. Right?”</li>
      </ul>
    
      <h2>Ports</h2>
      <ul>
        <li>Lune: Port <strong>8000</strong></li>
        <li>Sciel: Port <strong>8100</strong></li>
        <li>Gustave: Port <strong>8200</strong></li>
      </ul>
    
      <div class="motto">
        “Despite the odds, Expedition 33 marches forward.”
      </div>
    </div>
    
    <footer>
      © 2025 Expedition 33 — For Those Who Come After
    </footer>
    </body>
    </html>
    ```
    - Edit dibagian `/myscripts/myconfig/nginx.conf`
    ```
    user www-data;
    worker_processes auto;
    worker_cpu_affinity auto;
    pid /tmp/nginx.pid;
    error_log  /tmp/error.log;
    
    events { worker_connections 768; }
    
    http {
    log_format custom '[$time_local] Jarkom Node Sciel Access from $remote_addr using method "$request" returned status $status with $body_bytes_sent bytes sent in $request_time seconds';
    access_log /tmp/access.log custom;
        server {
            listen 80;
            server_name _;
    
            root /myscripts/myweb;
            index profile_sciel.html;
    
            location / {
                try_files $uri $uri/ =404;
            }
        }
    
        server {
            listen 8100;
            server_name _;
    
            root /myscripts/myweb;
            index info.html;
    
            location / {
                try_files $uri $uri/ =404;
            }
        }
    }
    ```
  - Gustave
    - Buat file
    ```
    <!DOCTYPE html>
    <html lang="en">
    <head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Expedition Gustave33 — Mission Brief</title>
    <style>
      body {
        margin: 0;
        font-family: Arial, Helvetica, sans-serif;
        color: #fff;
        background: linear-gradient(270deg, #0a043c, #4a0c25, #7b1b0c, #f9a826);
        background-size: 800% 800%;
        animation: bgShift 20s ease infinite;
      }
      @keyframes bgShift {
        0% {background-position: 0% 50%;}
        50% {background-position: 100% 50%;}
        100% {background-position: 0% 50%;}
      }
      header {
        text-align: center;
        padding: 3rem 1rem 1rem;
      }
      header h1 {
        font-size: 2.8rem;
        color: #00e5ff;
        letter-spacing: 1px;
        text-shadow: 0 0 10px #00e5ff;
      }
      header p {
        font-size: 1rem;
        color: #b5eaff;
        margin-top: 0.3rem;
      }
      .container {
        max-width: 700px;
        margin: 2rem auto 3rem;
        background: rgba(255, 255, 255, 0.08);
        border-radius: 16px;
        padding: 2rem 2.5rem;
        box-shadow: 0 4px 20px rgba(0,0,0,0.4);
        backdrop-filter: blur(6px);
      }
      h2 {
        color: #00e5ff;
        margin-top: 1.5rem;
      }
      p, li {
        line-height: 1.6;
      }
      ul {
        list-style: none;
        padding: 0;
      }
      li {
        margin: 0.4rem 0;
      }
      strong {
        color: #ffd166;
      }
      .motto {
        text-align: center;
        margin-top: 1.5rem;
        font-style: italic;
        color: #ccc;
        opacity: 0.9;
      }
      footer {
        text-align: center;
        font-size: 0.9rem;
        color: #ddd;
        padding: 1rem;
        background: rgba(0,0,0,0.4);
      }
    </style>
    </head>
    <body>
    <header>
      <h1>Expedition 33</h1>
      <p>Mission Log #E33-00</p>
    </header>
    
    <div class="container">
      <h2>Mission Brief</h2>
      <p>Expedition 33 is a digital exploration led by <strong>Lune</strong>, <strong>Sciel</strong>, and <strong>Gustave</strong>.  
         Together, they traverse the unknown layers of the Paintress system — seeking order within chaos.</p>
    
      <h2>Active Nodes</h2>
      <ul>
        <li><strong>Lune</strong> — “When one falls, we continue.”</li>
        <li><strong>Sciel</strong> — “Tomorrow comes.”</li>
        <li><strong>Gustave</strong> — “For those who come after. Right?”</li>
      </ul>
    
      <h2>Ports</h2>
      <ul>
        <li>Lune: Port <strong>8000</strong></li>
        <li>Sciel: Port <strong>8100</strong></li>
        <li>Gustave: Port <strong>8200</strong></li>
      </ul>
    
      <div class="motto">
        “Despite the odds, Expedition 33 marches forward.”
      </div>
    </div>
    
    <footer>
      © 2025 Expedition 33 — For Those Who Come After
    </footer>
    </body>
    </html>

    ```
    - Edit dibagian `/myscripts/myconfig/nginx.conf`
    ```
    user www-data;
    worker_processes auto;
    worker_cpu_affinity auto;
    pid /tmp/nginx.pid;
    error_log  /tmp/error.log;
    
    events { worker_connections 768; }
    
    http {
    log_format custom '[$time_local] Jarkom Node Gustave Access from $remote_addr using method "$request" returned status $status with $body_bytes_sent bytes sent in $request_time seconds';
    access_log /tmp/access.log custom;
        server {
            listen 8080;
            listen 8888;
            server_name _;
    
            root /myscripts/myweb;
            index profile_gustave.html;
    
            location / {
                try_files $uri $uri/ =404;
            }
        }
    
        server {
            listen 8200;
            server_name _;
    
            root /myscripts/myweb;
            index info.html;
    
            location / {
                try_files $uri $uri/ =404;
            }
        }
    }
    ```
  - Lalu jalankan web servernya dengan `myscripts/start_http.sh`
  - Client
    - Cek dengan menjalankan perintah berikut
    ```
    curl lune33.com:8000
    curl sciel33.com:8100
    curl gustave33.com:8200
    ```
  - Bisa juga melihatnya di nvc dengan mengecek `lune33.com:8000`, `sciel33.com:8100` dan `gustave33.com:8200`
    
<br>

## Soal 9

> Untuk mempermudah akses ke profil tiap anggota ekspedisi, buatlah 1 domain lagi yaitu "expeditioners.com" yang akan mengarah ke Alicia. Lalu, untuk mencegah overload dari salah satu web server, konfigurasikan reverse proxy Alicia agar bisa forward request ke server yang sesuai berdasarkan URL profile yang diminta oleh klien dengan ketentuan sebagai berikut:
> -  Request untuk “expeditioners.com/profil_lune” harus dialihkan ke halaman profil web server Lune.
> -  Request untuk “expeditioners.com/profil_sciel” harus dialihkan ke halaman profil web server Sciel.
> -  Request untuk “expeditioners.com/profil_gustave” harus dialihkan ke halaman profil web server Gustave.
> Jika terdapat request ke URL selain profil yang ditentukan, reverse proxy akan mengalihkan ke halaman informasi pada web server Lune.

> _To make it easier to access each member’s profile, create a new domain “expeditioners.com” that points to Alicia. "
Configure Alicia’s reverse proxy (Nginx) to forward requests to the correct web server based on the requested URL, with the following rules:_
> _- Request URL expeditioners.com/profil_lune, Forward To Lune’s profile page_
> _- Request URL expeditioners.com/profil_sciel, Forward To Sciel’s profile page_
> _- Request URL expeditioners.com/profil_gustave, Forward To Gustave’s profile page_
> _- Any other URL, Forward To Lune’s information page_

**Answer:**

- Screenshot

  <img width="960" height="1020" alt="Screenshot 2025-10-31 231747" src="https://github.com/user-attachments/assets/433f6ce6-ddfd-4786-b1e5-9fb7ec038386" />
  <br><br>
  <img width="960" height="1020" alt="Screenshot 2025-10-31 231803" src="https://github.com/user-attachments/assets/8351cc80-dee6-477b-a033-7bc86d3036f6" />
  <br><br>
  <img width="960" height="1020" alt="Screenshot 2025-10-31 231814" src="https://github.com/user-attachments/assets/f7c7f1a4-b4d0-4961-858d-9f24ed646c8b" />
  <br><br>
  <img width="960" height="1020" alt="Screenshot 2025-10-31 231825" src="https://github.com/user-attachments/assets/17247c2f-3bed-47b7-b3d1-62ab6c9d9d7d" />
  <br><br>
  <img width="960" height="1020" alt="Screenshot 2025-10-31 231836" src="https://github.com/user-attachments/assets/fda0f7f0-a632-4a8b-8e5d-985bc123b239" />
  <br><br>
  
- Explanation

  - Renoir
    - Di bagian `named.conf` tambahkan
    ```
    zone "expeditioners.com" {
        type master;
        notify yes;
        also-notify { 10.193.3.2; };
        allow-transfer { 10.193.3.2; };
        file "db.expeditioners.com";
    };
    ```
    - Lalu tambahkan file `db.expeditioners.com`
    ```
    ;
    ; BIND data file for local loopback interface
    ;
    $TTL    604800
    @       IN      SOA     expeditioners.com. root.expeditioners.com. (
                         2022100601         ; Serial
                             604800         ; Refresh
                              86400         ; Retry
                            2419200         ; Expire
                             604800 )       ; Negative Cache TTL
    ;
    @       IN      NS      expeditioners.com.
    @       IN      A       10.193.4.1
    ```
  - Verso
    - Di bagian `named.conf` tambahkan
    ```
    zone "expeditioners.com" {
        type slave;
        file "/var/cache/bind/db.expeditioners.com";
    };
    ```
  - Alicia
    - Buat direkori `myconfig`
    ```
    mkdir /myscripts/myconfig
    ```
    - Selanjutnya buat file `nginx.conf` didalam myconfig 
    ``` 
    user www-data;
    worker_processes auto;
    worker_cpu_affinity auto;
    pid /tmp/nginx.pid;
    error_log /tmp/error.log;
    
    events { worker_connections 768; }
    
    http {
        server {
            listen 80;
            server_name expeditioners.com;
    
            location = /profile_lune {
                proxy_pass http://10.193.2.1/;
                proxy_set_header Host $host;
                proxy_set_header X-Real-IP $remote_addr;
            }
    
            location = /profile_sciel {
                proxy_pass http://10.193.2.2/;
                proxy_set_header Host $host;
                proxy_set_header X-Real-IP $remote_addr;
            }
    
            location = /profile_gustave {
                proxy_pass http://10.193.2.3:8080/;
                proxy_set_header Host $host;
                proxy_set_header X-Real-IP $remote_addr;
            }
    
            location / {
                proxy_pass http://10.193.2.1/;
                proxy_set_header Host $host;
                proxy_set_header X-Real-IP $remote_addr;
                try_files $uri $uri/ /;
            }
        }
    }
    ```
    - Setelah itu buat file `start_http.sh`
    ```
    #!/bin/bash
    
    nginx -c /myscripts/myconfig/nginx.conf -g 'daemon off;'
    ```
    - Jalankan perintah ``chmod +x sstart_http.sh``
    - Jalankan nginxnya dengan perintah berikut ``/myscripts/start_http.sh``

    - Lalu bisa dijalankan di Client dengan mengunakan perintah
    ```
    curl expeditioners.com
    curl expeditioners.com/profile_lune
    curl expeditioners.com/profile_sciel
    curl expeditioners.com/profile_gustave
    curl expeditioners.com/hygyutfrdee
    ```
    - Bisa juga dijalankan di vnc viewer yaitu dengan mengsearch `expeditioners.com`,`expeditioners.com/profile_lune`,`expeditioners.com/profile_sciel`,`expeditioners.com/profile_gustave`,`expeditioners.com/hygyutfrdee`
    
<br>

## Soal 10

> Untuk mendistribusikan traffic halaman informasi, atur Reverse Proxy Alicia agar dapat membagi pekerjaan kepada web server Lune, Sciel, dan Gustave secara optimal menggunakan algoritma Round-robin. Pastikan target pembagian load merupakan halaman informasi, bukan halaman profil masing-masing web server.

> _To distribute traffic for the information page, configure the reverse proxy (Alicia) to use Round-robin load balancing between the three web servers: Lune, Sciel, and Gustave.
Ensure that only the information page is included in the load-balancing configuration - not the profile pages._

**Answer:**

- Screenshot

  <img width="1919" height="1079" alt="Screenshot 2025-10-31 233316" src="https://github.com/user-attachments/assets/0685ebb7-249f-4119-be21-196aee06045f" />
  <br><br>
  <img width="1919" height="1079" alt="Screenshot 2025-10-31 233327" src="https://github.com/user-attachments/assets/b042376d-3adf-419d-aa05-ce9ca3e5af4d" />
  <br><br>
  <img width="1919" height="1079" alt="Screenshot 2025-10-31 233337" src="https://github.com/user-attachments/assets/c2e101f9-5e2f-4eb4-9cad-4a0c6e25eff8" />
  <br><br>

- Explanation

  - Alicia
    - Edit dibagian `nginx.conf`
    ```
    user www-data;
    worker_processes auto;
    worker_cpu_affinity auto;
    pid /tmp/nginx.pid;
    error_log /tmp/error.log;
    
    events { worker_connections 768; }
    
    http {
        upstream myweb  {
            server 10.193.2.1:8000;
            server 10.193.2.2:8100;
            server 10.193.2.3:8200;
        }
    
        server {
            listen 80;
            server_name expeditioners.com;
    
            location = /profile_lune {
                proxy_pass http://10.193.2.1/;
                proxy_set_header Host $host;
                proxy_set_header X-Real-IP $remote_addr;
            }
    
            location = /profile_sciel {
                proxy_pass http://10.193.2.2/;
                proxy_set_header Host $host;
                proxy_set_header X-Real-IP $remote_addr;
            }
    
            location = /profile_gustave {
                proxy_pass http://10.193.2.3:8080/;
                proxy_set_header Host $host;
                proxy_set_header X-Real-IP $remote_addr;
            }
    
            location / {
                proxy_pass http://myweb;
                proxy_set_header Host $host;
                proxy_set_header X-Real-IP $remote_addr;
                try_files $uri $uri/ /;
            }
    
        }
    }

    ```
  - Lalu bisa dicek di nvc viewer dengan mengecek expeditioners.com disini saya membedakan judul webnya di html
  - Atau bisa juga deangan curl di bagian clien yaitu dengan menjalankan perintah
  ```
  curl expeditioners.com
  ```

<br>
  
## Problems

-

## Revisions (if any)
