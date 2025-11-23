[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/tPVgLsdF)
| Name | NRP | Class |
| ---- | --- | ----- |
| Muhamad Aziz Romdhoni  | 5025241071 | C |

## Task 1

- Flag

  `JARKOM25{Ja0G_Bbbb4ng3t_S1_O7WNS2ENU83IQ7DVFWWHSSBDAV2M7Z0xl0vel1ln5tjwdxi6v69k0o6d3xbb0_81575dcffee180bbf3b62f34b90ef667}`

> a. Berapa banyak packet yang terekam pada file pcapng?

> _a. How many packets are recorded in the pcapng file?_

**Answer:** `9596`

- Filter expression

  `-`

- Explanation

  `menggunakan ctrl+shift+alt+c untuk melihat jumlah paket yang terekam yaitu berjumlah "9596"`

- Output result

  #### Wireshark
  <img width="1920" height="1080" alt="Screenshot From 2025-09-11 19-03-25" src="https://github.com/user-attachments/assets/843c3577-1957-4eac-aaaa-5f26c01cb38d" />

  #### Terminal
  <img width="1920" height="1080" alt="Screenshot From 2025-09-11 19-27-27" src="https://github.com/user-attachments/assets/29758afa-d245-433b-a6e5-eb6c95994b9d" />

<br>
<br>

> b. Ada berapa jenis protocol (total) yang terekam pada traffic?

> _b. How many types of protocol (totals) are recorded in the traffic?_

**Answer:** `12`

- Filter expression

  `-`

- Explanation

  `Masuk kebagian protocol hierarchy di statistic lalu menghitung jumlah protokol yang ada, yaitu berjumlah "12"`

- Output result
  
  #### Wireshark
  <img width="1920" height="1080" alt="Screenshot From 2025-09-11 19-11-00" src="https://github.com/user-attachments/assets/d6cb5104-5a9b-4ed0-9c41-6f78dc0a41f8" />

  #### Terminal
  <img width="1920" height="1080" alt="Screenshot From 2025-09-11 19-27-27" src="https://github.com/user-attachments/assets/463a536e-d97c-4839-a1ee-494f7b6274a6" />

<br>
<br>

> c. Ada berapa jenis protocol berbasis TCP yang terekam pada traffic?

> _c. How many types of TCP-based applications protocol are recorded in the traffic?_

**Answer:** `8`

- Filter expression

  `-`

- Explanation

  `Masuk kebagian protocol hierarchy di statistic lalu menghitung jumlah protokol yang berbasis tcp, yaitu berjumlah "8"`

- Output result
  
  #### Wirshark
  <img width="1920" height="1080" alt="Screenshot From 2025-09-11 19-11-00" src="https://github.com/user-attachments/assets/3ed575a8-7d8f-40df-9b77-271f83e64732" />

  #### Terminal
  <img width="1920" height="1080" alt="Screenshot From 2025-09-11 19-27-27" src="https://github.com/user-attachments/assets/0e56a3a2-bae6-41d6-99d3-00f42c78ae3d" />

  <br>
  <br>

> d. Ada berapa banyak packet dengan protokol TCP murni yang terekam pada traffic (tanpa data)?

> _d. How many packets with pure TCP protocol are recorded in the traffic (without data)?_

**Answer:** `3223`

- Filter expression

  `tcp && not (http or telnet or vnc or thrift or sigcomp or hipercontracer or data)`

- Explanation

  `Melakukan filter hanya tcp murni saja tidak termasuk http,telnet,vnc,thrift,sigcomp,hipercontracer,data, yaitu berjumlah "3223" `

- Output result
  
  #### Wireshark
  <img width="1920" height="1080" alt="Screenshot From 2025-09-11 19-48-44" src="https://github.com/user-attachments/assets/9354e66f-c715-4035-8f10-3c60d0a9b447" />
  
  #### Terminal
  <img width="1920" height="1080" alt="Screenshot From 2025-09-11 19-27-27" src="https://github.com/user-attachments/assets/2aefe3f8-ed11-4d27-a45a-db611d3a525a" />


## Task 2

- Flag

  `JARKOM25{N1c3_0ne_b4nggg_WAEAVNHMXXyuMM13yewvoiaoumazwjbxcgjddc3r4t0ps49290236966716873391_30f923d038af3640201b00444727e470}`

> a. Berapa banyak packet berhasil yang berbasis murni TCP dan memiliki flag [ACK]?

> _a. How many packets succeed that are pure TCP based and have [ACK] flag?_

**Answer:** `3209`

- Filter expression

  `tcp && not (http or telnet or vnc or thrift or sigcomp or hipercontracer or data) && tcp.flags.ack==1`

- Explanation

  `Pertama tama melakukan filter yang berbasis murni TCP dan memiliki flag ACk, setelah itu ctrl+shift+alt+c akan menampilakn seluruh jumlah packet yaitu "3211" karena ada 2 packet yang hitam atau tidak berhasil maka "3211 - 2" jadi packet yang berhasil berbasis murni TCP dan memiliki flag ACK berjumlah "3209"`

- Output result
  
  #### Wireshark
  <img width="1919" height="1047" alt="Screenshot From 2025-09-14 13-31-05" src="https://github.com/user-attachments/assets/fca775e9-7198-4f27-8dd7-a01adc309185" />

  #### Terminal
  <img width="1920" height="1080" alt="Screenshot From 2025-09-11 22-18-45" src="https://github.com/user-attachments/assets/982ab9d7-cca5-4544-be90-f674784ffa2a" />

  <br>
  <br>

> b. Berapa banyak packet berhasil yang berbasis murni TCP yang hanya memiliki flag [ACK]?

> _b. How many packets succeed that are pure TCP based and have only [ACK] flag?_

**Answer:** `3172`

- Filter expression

  `tcp && not (http or telnet or vnc or thrift or sigcomp or hipercontracer or data) && tcp.flags.ack == 1 && tcp.flags.fin == 0 && tcp.flags.syn == 0 && tcp.flags.push == 0`

- Explanation

  `Sama seperti sub soal a yaitu melakukan filter yang berbasis murni TCP dan hanya memiliki flag ACk, setelah itu ctrl+shift+alt+c akan menampilakn seluruh jumlah packet yaitu "3174" karena ada 2 packet yang hitam atau tidak berhasil maka "3174 - 2" jadi packet yang berhasil berbasis murni TCP dan hanya memiliki flag ACK berjumlah "3172"`

- Output result
  
  #### Wireshark
  <img width="1919" height="1047" alt="Screenshot From 2025-09-14 13-35-55" src="https://github.com/user-attachments/assets/3e9a36f5-dab1-476c-b170-fcff58c34079" />

  #### Terminal
  <img width="1920" height="1080" alt="Screenshot From 2025-09-11 22-18-45" src="https://github.com/user-attachments/assets/adae7e6e-a01c-46a3-bac5-fcd111fb678e" />

  <br>
  <br>

> c. Berapa banyak packet berhasil yang berbasis murni TCP dan memiliki flag selain hanya [ACK]?

> _c. How many packets succeed that are pure TCP based and contain flags other than just [ACK] flag?_

**Answer:** `49`

- Filter expression

  `tcp && not (http or telnet or vnc or thrift or sigcomp or hipercontracer or data or tcp.flags == 0x010)`

- Explanation

  `Melakukan filter yang berbasis murni TCP dan memiliki flag selain hanya ACK, selanjutnya ctrl+shift+alt+c akan menampilkan jumlahnya yaitu "49". "0x010" adalah hexadesimal dari flag ACK `

- Output result
  
  #### Wireshark
  <img width="1919" height="1047" alt="Screenshot From 2025-09-14 13-59-42" src="https://github.com/user-attachments/assets/e7b41d74-88dc-4fe8-a7a8-f40781d85252" />

  #### Terminal
  <img width="1920" height="1080" alt="Screenshot From 2025-09-11 22-18-45" src="https://github.com/user-attachments/assets/5a870985-49fb-4002-8059-6649ec47bd50" />

  <br>
  <br>

## Task 3

- Flag

  `JARKOM25{W0w_Y0uU_h4V33e_d0n3_444_90od_j0bB_8DM6Lg0dl1k3b19jdgky50vvxuazrmndvi_ee4f20056119e7f130c44249a4d02895}`

> a. Pada port berapa client telnet terbuka?

> _a. In what port is the telnet client open?_

**Answer:** `54184`

- Filter expression

  `telnet`

- Explanation

  `Pertama tama filter packet selanjutnya klik salah satu packet, di packet tersebut terdapat Dst Port yaitu "54184"`

- Output result
  
  #### Wireshark
  <img width="1913" height="1046" alt="Screenshot From 2025-09-14 16-11-25" src="https://github.com/user-attachments/assets/407874b7-43a3-44f5-908b-61c633a9e547" />

  #### Terminal
  <img width="1920" height="1080" alt="Screenshot From 2025-09-11 20-16-55" src="https://github.com/user-attachments/assets/8a393fb4-5067-480d-84fe-1cd1a61eec0c" />

  <br>
  <br>

> b. Berapa byte file response yang dikirim dari server?

> _b. How many bytes of the response files are sent from the server?_

**Answer:** `1449`

- Filter expression

  `telnet && tcp.srcport==23`

- Explanation

  `Pertama tama filter packet selanjutnya ke menu statistics lalu ke protocol hierarchy, disana terdapat "1449" byte file response yang dikirim dari server`

- Output result
  
  #### Wireshark
  <img width="1920" height="1080" alt="Screenshot From 2025-09-11 20-09-26" src="https://github.com/user-attachments/assets/64fdcf44-9e36-432d-ab9a-e89ddfb0f5d1" />

  #### Terminal
  <img width="1920" height="1080" alt="Screenshot From 2025-09-11 20-16-55" src="https://github.com/user-attachments/assets/14a64bd4-cd95-4782-9578-2d4da003fc8e" />

  <br>
  <br>

> c. Apa username yang digunakan client telnet untuk berhubungan dengan server?

> _c. What telnet client's username is used to connect with the server?_

**Answer:** `jovyan`

- Filter expression

  `telnet`

- Explanation

  `Pertama tama filter packet selanjutnya follow stream salah satu packet, didalam packet akan berisi username yang digunakan yaitu "jovyan"`

- Output result
  
  #### Wireshark
  <img width="1920" height="1080" alt="Screenshot From 2025-09-11 20-15-53" src="https://github.com/user-attachments/assets/45f2942d-af0f-42a6-96f5-9e5cc17fde3b" />

  #### Terminal
  <img width="1920" height="1080" alt="Screenshot From 2025-09-11 20-16-55" src="https://github.com/user-attachments/assets/5db25cf6-5b48-47e7-a367-67d166d2905b" />

  <br>
  <br>

> d. Apa password client telnet?

> _d. What is the telnet client's password?_

**Answer:** `123`

- Filter expression

  `telnet`

- Explanation

  `Sama seperti sub soal c yaitu filter packet selanjutnya follow stream salah satu packet, didalam packet akan berisi password yang digunakan yaitu "123" `

- Output result
  
  #### Wireshark
  <img width="1920" height="1080" alt="Screenshot From 2025-09-11 20-15-53" src="https://github.com/user-attachments/assets/f67b29d3-8358-42c6-a7b2-cf2855a4ffbf" />

  #### Terminal
  <img width="1920" height="1080" alt="Screenshot From 2025-09-11 20-16-55" src="https://github.com/user-attachments/assets/f28bdf0e-425a-4e86-b85f-951a57e44669" />

  <br>
  <br>

## Task 4

- Flag

  `JARKOM25{G04t__a4n4liz333er_CM3RTSGKHG520GFIHLUUfr0g3o28jn29y5mjldvr3ys3633920893_15d120e5985693c32e0bb64008d835c6}`

> a. Apa perintah pertama yang ditulis client pada koneksi telnet?

> _a. What is the first command that client wrote on telnet connection?_

**Answer:** `echo`

- Filter expression

  `telnet`

- Explanation

  `Pertama tama filter packet setelah itu follow stream salah satu packet nanti didalam packet tersebut ada perintah pertama yaitu "echo"`

- Output result

  #### Wireshark
  <img width="1919" height="1047" alt="Screenshot From 2025-09-14 13-01-38" src="https://github.com/user-attachments/assets/e5da0622-a8b8-4e7e-9daa-e8e50e6cac16" />

  #### Terminal
  <img width="1920" height="1080" alt="Screenshot From 2025-09-11 22-17-56" src="https://github.com/user-attachments/assets/888ee921-9d6f-4fc3-8d0f-f5edc512e336" />

  <br>
  <br>

> b. Apa nama file .txt di server (ditulis bersama ekstensinya)?

> _b. What is the name of .txt file on the server (write with the extension)?_

**Answer:** `test.txt`

- Filter expression

  `telnet`

- Explanation

  `Sama seperti sub soal a yaitu filter packet selanjutnya scroll isi packet, didalam packet ada file dengan nama "test.txt"`

- Output result

  #### Wireshark
  <img width="1919" height="1047" alt="Screenshot From 2025-09-14 13-03-12" src="https://github.com/user-attachments/assets/337ece67-e190-462c-852d-aef647727342" />

  #### Terminal
  <img width="1920" height="1080" alt="Screenshot From 2025-09-11 22-17-56" src="https://github.com/user-attachments/assets/3a25890b-69cf-4c6b-bf4c-fd700a232023" />

  <br>
  <br>

> c. Apa kata pertama dari frasa yang dimasukkan client ke dalam file sebelumnya?

> _c. What is the first word that the client inserted into the previous file?_

**Answer:** `Jarkom`

- Filter expression

  `telnet`

- Explanation

  `Sama seperti sub soal a dan b filter packet selanjutnya scroll isi packet, didalamnya ada frasa yang dimasukkan yaitu "Jarkom gampang" ambil kata pertama saja yaitu "Jarkom"`

- Output result

  #### Wireshark
  <img width="1919" height="1047" alt="Screenshot From 2025-09-14 13-04-36" src="https://github.com/user-attachments/assets/7c42f11a-c005-466a-bb96-45115c53152a" />

  #### Terminal
  <img width="1920" height="1080" alt="Screenshot From 2025-09-11 22-17-56" src="https://github.com/user-attachments/assets/734e5706-0ddf-4fcf-9b9a-4b4fca7add09" />

  <br>
  <br>

## Task 5

- Flag

  `JARKOM25{n41l0ng_m1lk_dr4g000n_Q7MJEP6D6C6LKG6D7H5508DHH5YVSKcr0chs5c6ty4z6r0aa60n5zab437_cc3ca74d9eb87c40f267398713f65659}`

> a. Berapa banyak packet berbasis HTTP yang terekam pada file pcapng?

> _a. How many HTTP packets are recorded in the pcapng file?_

**Answer:** `298`

- Filter expression

  `http`

- Explanation

  `Pertama tama filter packet, selanjutnya tekan ctrl+shift+alt+c untuk melihat jumlah packet bebasis http yang terekam, yaitu berjumlah "298"`

- Output result

  #### Wireshark
  <img width="1917" height="1039" alt="Screenshot From 2025-09-14 12-33-52" src="https://github.com/user-attachments/assets/83fd8301-075f-4e0e-9712-1616e062180d" />

  #### Terminal
  <img width="1920" height="890" alt="Screenshot From 2025-09-14 12-44-44" src="https://github.com/user-attachments/assets/99cdb896-8b10-4839-91f5-bf9d51da0382" />

  <br>
  <br>

> b. Ada berapa HTTP packet yang berupa response?

> _b. How many response HTTP packets are recorded in the traffic?_

**Answer:** `149`

- Filter expression

  `http.response`

- Explanation

  `Sama seperti sebelumnya filter packet, selanjutnya tekan ctrl+shift+alt+c untuk melihat jumlah http packet yang berupa response, yaitu berjumlah "149"`

- Output result
  
  #### Wireshark
  <img width="1917" height="1039" alt="Screenshot From 2025-09-14 12-36-01" src="https://github.com/user-attachments/assets/6593cbba-4e3a-42ec-a051-8990428b9c94" />

  #### Terminal
  <img width="1920" height="890" alt="Screenshot From 2025-09-14 12-44-44" src="https://github.com/user-attachments/assets/37b8eec3-06b8-4ce1-886f-7f2b4a900f10" />

  <br>
  <br>

> c. Ada berapa paket berbasis HTTP yang berhasil?

> _c. How many HTTP packets that succeed?_

**Answer:** `296`

- Filter expression

  `http`

- Explanation

  `Caranya sama seperti sub soal a yaitu filter packet, selanjutnya tekan ctrl+shift+alt+c untuk melihat jumlah packet bebasis http yang terekam, yaitu berjumlah "298" karena ada dua packet yang berwarna hitam maka "298-2" jadi total packet berbasis http yang berhasil adalah "296" `

- Output result

  #### Wireshark
  <img width="1917" height="1039" alt="Screenshot From 2025-09-14 12-37-47" src="https://github.com/user-attachments/assets/143ff95e-ae98-420f-a817-a78a3b4af2d1" />

  #### Terminal
  <img width="1920" height="890" alt="Screenshot From 2025-09-14 12-44-44" src="https://github.com/user-attachments/assets/ee16b6e3-be67-432f-b10c-a85bd727d8aa" />

  <br>
  <br>

> d. Apa alamat IP dari client HTTP yang tersambung lokal dengan mesin lain?

> _d. What is the client HTTP IP Address in connection with other local machine?_

**Answer:** `176.16.16.101`

- Filter expression

  `http && ip.dst_host`

- Explanation

  `Langkah pertama adalah memfilter packet, kemudian mencari dengan menggunakan string "host" setalah itu memilih satu packet nanti mendapat alamat IP yaitu "176.16.16.101"`

- Output result

  #### Wireshark
  <img width="1919" height="1047" alt="Screenshot From 2025-09-14 12-49-28" src="https://github.com/user-attachments/assets/e957c127-b4b3-4bb4-b802-3e688454b0e8" />


  #### Terminal
  <img width="1920" height="890" alt="Screenshot From 2025-09-14 12-44-44" src="https://github.com/user-attachments/assets/44be67e6-c703-4bb4-a5b8-45061b144f54" />

  <br>
  <br>

## Task 6

- Flag

  `JARKOM25{br0mb44rdin0u_Cr0ccc0c0c0cdi1l10l_2105078225awaesacnsa0fiekksh1n0buVK9XVC977NQH04I_cc1ba541de1261ab72d7133015b9d47a}`

> a. Apakah kamu menemukan fake flag? Tuliskan seluruhnya!

> _a. Did you find the fake flag? Write it whole!_

**Answer:** `FakeFlag{JarkomGampang}`

- Filter expression

  `http`

- Explanation

  `Pertama tama filter packet, setelah itu mencari dengan menggunakan string "flag" selanjutnya follow stream packet tersebut, lalu didapatkan fake flag yaitu "FakeFlag{JarkomGampang}"`

- Output result
  
  #### Wireshark
  <img width="1917" height="1039" alt="Screenshot From 2025-09-14 12-27-19" src="https://github.com/user-attachments/assets/96f608cc-b8ac-4783-a339-20ea0fb980c3" />

  #### Terminal
  <img width="1920" height="1080" alt="Screenshot From 2025-09-11 21-23-50" src="https://github.com/user-attachments/assets/0d6be8e0-7049-4838-814a-84295c375796" />

  <br>
  <br>

> b. Tuliskan username dan password yang tertulis! (format username:password)

> _b. Write the written username and password! (format username:password)_

**Answer:** `Rey:123`

- Filter expression

  `http`

- Explanation

  `Sama seperti sub soal a yaitu filter packet, setelah itu mencari dengan menggunakan string "passwd" selanjutnya follow stream packet tersebut, lalu didapatkan username dana password yaitu "Rey:123"`

- Output result
  
  #### Wireshark
  <img width="1917" height="1039" alt="Screenshot From 2025-09-14 12-24-29" src="https://github.com/user-attachments/assets/fcc8e490-d274-403b-9089-844dd7e50b25" />

  #### Terminal
  <img width="1920" height="1080" alt="Screenshot From 2025-09-11 21-23-50" src="https://github.com/user-attachments/assets/f0c4636b-adca-4806-a860-043aea12e86e" />

  <br>
  <br>

## Task 7

- Flag

  `JARKOM25{tr4l4lel0_tr1lil1_ald7d2x1kjk3b0s0s8PD516BWWEQM7RV_36dc1fd61c311beaa1d4f95748587703}`

> Apa nama gambar yang direquest oleh client? (tulis dengan ekstensinya)

> _What is the image that is being requested by the client? (write with its extension)_

**Answer:** `donalbebek.jpg`

- Filter expression

  `http.request`

- Explanation

  `Pertama tama filter packet, setelah itu mencari dengan menggunakan string ".jpg", setelah itu didapatkan nama gambarnya yaitu "donalbebek.jpg"`

- Output result

  #### Wireshark
  <img width="1920" height="1080" alt="Screenshot From 2025-09-11 21-16-58" src="https://github.com/user-attachments/assets/cea7d352-a181-44df-9425-62222f4acf1b" />

  #### Terminal
  <img width="1920" height="1080" alt="Screenshot From 2025-09-11 21-17-27" src="https://github.com/user-attachments/assets/dc3bf9bb-90e8-471e-b7b0-9c94e8483e14" />

  <br>
  <br>

## Task 8

- Flag

  `JARKOM25{y0u_4r3_s0_G00d_1n_F0r3nsic_M8GAPUZHMV0U5HERHH72N59RS29IQZx45y4n634ph5p2jqberkgn94o9xaa2_68159244898708a29f2cdcf9ced9a4f6}`

> a. Berapa banyak packet berbasis FTP yang terekam pada file pcapng? (with the data)

> _a. How many FTP packets are recorded in the pcapng file? (with the data)_

**Answer:** `81`

- Filter expression

  `ftp or ftp-data`

- Explanation

  `Pertama tama yaitu memfilter packet, kemudian tekan ctrl+shift+alt+c untuk menampilkan jumlah packet`

- Output result

  #### Wireshark
  <img width="1917" height="1039" alt="Screenshot From 2025-09-14 10-57-01" src="https://github.com/user-attachments/assets/f4cd43a6-729c-4bf1-936b-4668a032bc64" />

  #### Terminal
  <img width="1920" height="1080" alt="Screenshot From 2025-09-11 21-30-30" src="https://github.com/user-attachments/assets/f4b5de12-84ed-499c-b8fb-497d66b153a1" />

  <br>
  <br>

> b. Apa username dan password client di koneksi FTP? (tulis dalam format username:password)

> _b. What is the client's username and password in FTP connection? (write in following format username:password)_

**Answer:** `rey:password123lingangu`

- Filter expression

  `ftp or ftp-data`

- Explanation

  `Karena packet sudah difilter follow stream salah satu packet, di dalam packet tersebut ada sebuah username dan password yaitu "rey:password123lingangu"`

- Output result
  
  #### Wireshark
  <img width="1917" height="1039" alt="Screenshot From 2025-09-14 10-57-51" src="https://github.com/user-attachments/assets/153b59b1-4a3c-44e8-aa93-8c214a209bb6" />

  #### Terminal
  <img width="1920" height="1080" alt="Screenshot From 2025-09-11 21-30-30" src="https://github.com/user-attachments/assets/c42f36ff-1994-4d9c-b90f-24b7ab8c171d" />

  <br>
  <br>

> c. What is the client's command for showing server directory that was sent on request packet?

> _c. Apa command client untuk melihat direktori server yang dikirimkan dalam request packet?_

**Answer:** `LIST`

- Filter expression

  `ftp or ftp-data`

- Explanation

  `Untuk mencari command caranya sama seperti sub soal b, didalam isi packet akan ada sebuah "LIST" untuk melihat direktori server yang dikirimkan dalam request packet`

- Output result

  #### Wireshark
  <img width="1920" height="1080" alt="Screenshot From 2025-09-11 21-29-42" src="https://github.com/user-attachments/assets/46a1ba12-1811-4f25-bb68-bf45eb20813e" />

  #### Terminal
  <img width="1920" height="1080" alt="Screenshot From 2025-09-11 21-30-30" src="https://github.com/user-attachments/assets/4d65aed8-947c-4656-abf8-cd467972f021" />

  <br>
  <br>

## Task 9

- Flag

  `JARKOM25{j4rk000000mmm_g4mpp4444n9999999_87374169858i41L4hs9mjzl9mjh321k0ncol1B0CW5VXEVAP98Q_1b78ffbe98d3497ae53085e149c02612}`

> a. Apa alamat IP dari FTP server?

> _a. What is the FTP server IP Address?_

**Answer:** `172.16.16.101`

- Filter expression

  `ftp-data`

- Explanation

  `Langkah pertama adalah memfilter packet, kemudian memilih satu packet nanti dibagian Internet Protocol Version 4 terdapat "src" yaitu alamat IP dari FTP server.`

- Output result

  #### Wireshark
  <img width="1917" height="1039" alt="Screenshot From 2025-09-14 10-44-25" src="https://github.com/user-attachments/assets/5f487d54-2699-4290-8718-f57d9a4b28eb" />

  #### Terminal
  <img width="1920" height="1080" alt="Screenshot From 2025-09-11 21-36-37" src="https://github.com/user-attachments/assets/8cf958d8-4255-4fbc-9849-8abf6cb1f3e0" />

  <br>
  <br>

> b. Berapa banyak file yang ada dalam direktori FTP server?

> _b. How many files are there inside the FTP server directory?_

**Answer:** `7`

- Filter expression

  `ftp-data`

- Explanation

  `Karena sudah difilter di sub soal sebelumnya langsung mencari suatu packet dengan [Command: LIST], setelah itu lakukan follow untuk melihat jumlah file yang ada didalam direktori FTP server.`

- Output result

  #### Wireshark
  <img width="1917" height="1039" alt="Screenshot From 2025-09-14 10-45-07" src="https://github.com/user-attachments/assets/f7009b2e-ffd7-4c5c-bdbe-3a8545e4b01c" />

  #### Terminal
  <img width="1920" height="1080" alt="Screenshot From 2025-09-11 21-36-37" src="https://github.com/user-attachments/assets/d359e77c-e7a4-4d9b-924d-bd7420e578fc" />

  <br>
  <br>

> c. Apa nama dari file yang digunakan dalam page.html? (tulis lengkap namanya beserta ekstensinya dan dipisahkan dengan koma ',')

> _c. What are the filenames used in the page.html? (write the filebames with their extensions and separate them with comma ',')_

**Answer:** `pokijan.jpg,research_center.jpg`

- Filter expression

  `ftp-data`

- Explanation

  `Sama seperti sebelumnya karena packetnya sudah difilter langsung mencari suatu packet dengan [Command: RETR page.html], setelah itu lakukan follow untuk melihat nama dari file yang digunakan yaitu "pokijan.jpg,research_center.jpg"`

- Output result

  #### Wireshark
  <img width="1917" height="1039" alt="Screenshot From 2025-09-14 10-46-03" src="https://github.com/user-attachments/assets/3d8f0cdb-73d3-4364-9b02-62ea0e8bca33" />

  #### Terminal
  <img width="1920" height="1080" alt="Screenshot From 2025-09-11 21-36-37" src="https://github.com/user-attachments/assets/99a59e52-b5bb-4ce4-ab39-e9b3135160b0" />

  <br>
  <br>

## Task 10

- Flag

  `JARKOM25{f1nisssshs55s5s533s_lin333ee333E3_63464278862910zdezsgbfwj3452151231232XDYQQIIDYTP7GL_8bc12cf93f1e8791e9268dc71095f42f}`

> a. Apa nama file yang mengandung string terencode?

> _a. What is the filename that contains encoded string?_

**Answer:** `secret.txt`

- Filter expression

  `ftp-data`

- Explanation

  `Langkah pertama adalah memfilter packet, kemudian mencari suatu packet dengan [Command: RETR secret.txt]`

- Output result

  #### Wireshark
  <img width="1920" height="1080" alt="Screenshot From 2025-09-11 21-41-32" src="https://github.com/user-attachments/assets/675e533c-b2ac-4855-bf9d-91d5c62907c1" />
  
  #### Terminal
  <img width="1920" height="1080" alt="Screenshot From 2025-09-11 21-42-40" src="https://github.com/user-attachments/assets/a7ceb796-87dc-44a0-863f-967ef1cf1ef7" />

  <br>
  <br>

> b. Apa nama file hasil copy file sebelumnya?

> _b. What is the filename of the previous file copy?_

**Answer:** `secret1.txt`

- Filter expression

  `ftp-data`

- Explanation

  `Karena packet sudah difilter di sub soal sebelumnya langsung mencari suatu packet dengan [Command: STOR secret1.txt]`

- Output result

  #### Wireshark
  <img width="1920" height="1080" alt="Screenshot From 2025-09-11 21-41-47" src="https://github.com/user-attachments/assets/81a303c9-01f1-4991-bae5-e2c1ddb2899e" />

  #### Terminal
  <img width="1920" height="1080" alt="Screenshot From 2025-09-11 21-42-40" src="https://github.com/user-attachments/assets/f00ee479-f814-4b24-80d2-c1f2f5625c92" />

  <br>
  <br>

> c. What is the decoded string from the previous file?

> _c. Apa decoded string dari file tersebut?_

**Answer:** `Pada suatu hari Rey bertemu dengan Nailong the Milk Dragon. Ketika bertemu, Rey mengajarkan Nailong apa itu Jaringan Komputer. Nailong pun senang karena ternyata Jaringan Komputer itu gampang.`

- Filter expression

  `ftp-data`

- Explanation

  `Langkah pertama yang diambil adalah mencari suatu packet dengan [Command: RETR secret.txt]. Kemudian lakukan follow, ditemukan suatu rangkaian huruf dan simbol (string) yang terencode. Lalu serangkaian "string" tersebut didecode dengan tool, disini saya pakai tool yang terdapat secara online yaitu "Base64 Decode and Encode". Sehingga hasil dari decode base64 dari "string" tersebut yaitu "Pada suatu hari Rey bertemu dengan Nailong the Milk Dragon. Ketika bertemu, Rey mengajarkan Nailong apa itu Jaringan Komputer. Nailong pun senang karena ternyata Jaringan Komputer itu gampang."`

- Output result

  #### Wireshark
  <img width="1911" height="1048" alt="Screenshot From 2025-09-14 00-25-59" src="https://github.com/user-attachments/assets/f714bb12-210f-420f-b067-b5fc1748bb7e" />

  #### Base64
  <img width="1920" height="1080" alt="Screenshot From 2025-09-11 21-42-02" src="https://github.com/user-attachments/assets/8a1a01aa-2002-46e3-a6de-1bbccf074417" />

  #### Terminal
  <img width="1920" height="1080" alt="Screenshot From 2025-09-11 21-42-40" src="https://github.com/user-attachments/assets/6a1346eb-8003-409d-a39a-5ba16e01f836" />

  <br>
  <br>

## Summary
Praktikum Jaringan Komputer 1 mencakup beberapa kegiatan yang dirancang untuk melatih keterampilan teknis sekaligus pemahaman teori. Salah satu bagian awal yang dikerjakan adalah crimping kabel UTP dengan konektor RJ45. Pada tahap ini harus memahami urutan warna kabel sesuai standar yaitu straight-through, kemudian memotong, menyusun, dan memasukkan kabel ke dalam konektor dengan rapi. Proses ini tidak hanya menuntut pemahaman teori, tetapi juga keterampilan manual serta ketelitian, karena kesalahan sekecil apa pun dapat menyebabkan kabel tidak berfungsi dengan baik. Praktikum berlanjut ke analisis jaringan menggunakan Wireshark. Pada bagian ini, diberikan tantangan berupa soal Capture The Flag (CTF) yang jawabannya tersembunyi di dalam file hasil tangkapan paket. Untuk menyelesaikan soal, harus menganalisis isi paket satu per satu dengan teliti. Pengetahuan tentang cara kerja Wireshark menjadi sangat penting, khususnya mengenai display filter untuk menyaring paket tertentu dan find string untuk mencari pola atau teks di dalam data. Dengan menggunakan fitur-fitur tersebut, dapat menemukan informasi yang berkaitan dan mengungkap jawaban dari tantangan yang diberikan.
## Problems
Terdapat hambatan untuk menentukan query nomer 2 tetapi setelah jawaban ditemukan semuanya berjalan lancar. 
