# Jarkom Modul 1
- [Soal 1](#soal-1)
- [Soal 2](#soal-2)
- [Soal 3](#soal-3)
- [Soal 4](#soal-4)
- [Soal 5](#soal-5)
- [Soal 7](#soal-7)
- [Soal 8](#soal-8)
- [Soal 9](#soal-9)
- [Soal 10](#soal-10)

### Soal 1
#### Description :
User melakukan berbagai aktivitas dengan menggunakan protokol FTP. Salah satunya adalah **mengunggah suatu file**.

#### PoC :
Dari deskripsi soal tersebut kita diminta untuk menganalisis protokol FTP terutama pada suatu aksi tertentu yaitu **upload** file. Dari hasil analisis terdapat sebuah packet FTP yang terlihat mencurigakan, Ditemukan request STOR file GrabThePhisher.zip
![image](https://github.com/RenDaemon/Jarkom-Modul-1-IT23-2023/assets/94961661/de046533-83c9-4c1f-a50b-a259ba272bb9)
Klik 2x lalu buka Transmission Control Protocol dan cari Sequence Number (raw) dan Acknowledgment number (raw).
untuk menemukan Response, dibawah Request ‘STOR’, Klik 2x lalu buka Transmission Control Protocol dan cari Sequence Number (raw) dan Acknowledgment number (raw).
![image](https://github.com/RenDaemon/Jarkom-Modul-1-IT23-2023/assets/94961661/eb47be6b-4bdf-4000-a24f-992c19a051e7)
![image](https://github.com/RenDaemon/Jarkom-Modul-1-IT23-2023/assets/94961661/3d715c19-ccc8-40c7-9640-f2f26432a8da)
Copy semua value yang dibutuhkan, dan submit jawabannya melalui nc dan akan didapatkan flag.

### Soal 2
#### Description :
Sebutkan web server yang digunakan pada portal praktikum Jaringan Komputer!

#### PoC :
Dari deskripsi soal tersebut kita diminta untuk mengetahui web server yang digunakan. Coba saja analisis packetnya dan cek pada header response pada salah satu packet untuk menemukannya.
![image](https://github.com/RenDaemon/Jarkom-Modul-1-IT23-2023/assets/94961661/19b38944-e43e-413a-a897-aae83304d0ad)web-server yang digunakan adalah gunicorn, langsung saja submit jawabannya ke nc dan akan didapatkan flag
![image](https://github.com/RenDaemon/Jarkom-Modul-1-IT23-2023/assets/94961661/3fcdb24a-17e0-4631-8fe4-e2522c91e6c5)

### Soal 3
#### Description :
Dapin sedang belajar analisis jaringan. Bantulah Dapin untuk mengerjakan soal berikut:

#### PoC :
Dari dekripsi soal tersebut kita lakukan analisis, namun untuk objektif lebih jelasnya langsung saja nc ke host yang disediakan.
Terdapat 2 pertanyaan : 

a. Berapa banyak paket yang tercapture dengan IP source maupun destination address adalah 239.255.255.250 dengan port 3702?

Untuk pertanyaan ini kita lakukan filtering seperti berikut
ip.addr == 239.255.255.250 && (udp.port == 3702 || udp.srcport == 3702), dan kita hitung berapa jumlah packet yang ada. terdapat 21 packet yang ada.

b. Protokol layer transport apa yang digunakan? 

Untuk pertanyaan ini sudah cukup jelas kita hanya perlu melihat protokol apa yang digunakan. Protokol yang digunakan yaitu UDP.
![image](https://github.com/RenDaemon/Jarkom-Modul-1-IT23-2023/assets/94961661/75af56c0-db90-4006-8409-be07b534c384)

Submit semua jawaban tersebut dan akan didapatkan flag.
![image](https://github.com/RenDaemon/Jarkom-Modul-1-IT23-2023/assets/94961661/bf085e3b-e282-429c-92b6-2f5eaf734dcc)

### Soal 4
#### Description :
Berapa nilai checksum yang didapat dari header pada paket nomor 130?

#### PoC :
Dari deskripsi soal tersebut, kita diminta untuk mengetahui value checksum yang dimiliki oleh packet ke 130. Untuk mendapatkannya cukup kita filtering dengan `frame.number == 130` dan check nilai checksum pada bagian header. Didapatkan bahwa nilai checksum adalah `0x18e5`.
![image](https://github.com/RenDaemon/Jarkom-Modul-1-IT23-2023/assets/94961661/f95ea355-abfd-4652-bd5b-733ef754a7f5)Submit jawabannya ke nc dan akan didapatkan flag.
![image](https://github.com/RenDaemon/Jarkom-Modul-1-IT23-2023/assets/94961661/7a035b63-d3bf-4e0d-801c-e85948f7b2a0)

### Soal 5
#### Description :
Elshe menemukan suatu file packet capture yang menarik. Bantulah elshe untuk menganalisis file packet capture tersebut.

#### PoC :
Diberikan 1 file pcap dan 1 file zip(protected). Untuk menemukan password kita lakukan analisis terhadap file pcap, dan benar saja follow tcp stream langsung kita dapatkan password file zip dalam bentuk base64.
![image](https://github.com/RenDaemon/Jarkom-Modul-1-IT23-2023/assets/94961661/32b70961-88a0-44bb-b39e-36a442b90574)
Decrypt passwordnya, didapatkan `5implePas5word` . Setelah dibuka file zipnya ternyata isinya adalah nc ke suatu address.
![image](https://github.com/RenDaemon/Jarkom-Modul-1-IT23-2023/assets/94961661/f5040542-0d5e-46ba-bcfe-a5406e4ff4d8)
Setelah terhubung, terdapat 3 pertanyaan :
- Jumlah packet = `61`
- Port pada server untuk smtp = `25`
- Public IP = `74.53.140.153`
jawaban" tersebut diperoleh dari analisis packetnya.
![image](https://github.com/RenDaemon/Jarkom-Modul-1-IT23-2023/assets/94961661/a75f5346-e535-4602-ba4f-d2277857f870)Submit semua jawaban, maka akan didapatkan flag.
![image](https://github.com/RenDaemon/Jarkom-Modul-1-IT23-2023/assets/94961661/b65b01a6-a85e-474f-af0d-2d7dfd49d601)

### Soal 7
#### Description :
Berapa jumlah packet yang menuju IP 184.87.193.88?

#### PoC :
Dari soal nomor 7 diminta untuk mencari berapa banyak packet yang menuju IP 184.87.193.88 pada file warkshark tersebut. Disini langsung saja mengklik file warkshark yang dimaksud dan melakukan pencarian pada fitur filter dengan keyword berikut :
ip.dst==184.87.193.88

Keyword ini bertujuan untuk melakukan pencarian menuju IP 184.87.193.88

Didapatkan 6 packet yang menuju IP 184.87.193.88
![img](https://i.ibb.co/JqfGqDb/wireshark-7.jpg)

Lalu, inputkan jawaban tersebut di nc dan didapatkan flag:
![img](https://i.ibb.co/nmLJW0T/flag-7.jpg)

### Soal 8
#### Description :
Berikan kueri filter sehingga wireshark hanya mengambil semua protokol paket yang menuju port 80! (Jika terdapat lebih dari 1 port, maka urutkan sesuai dengan abjad)!

#### PoC :
Untuk soal no.8 kita hanya perlu untuk submit filtering sesuai dengan yang di soal dengan nc dan akan didapatkan flag.
![image](https://github.com/RenDaemon/Jarkom-Modul-1-IT23-2023/assets/94961661/16f56409-f4d5-4f7e-94e6-4d21dac0b987)

### Soal 9
#### Description :
Berikan kueri filter sehingga wireshark hanya mengambil paket yang berasal dari alamat 10.51.40.1 tetapi tidak menuju ke alamat 10.39.55.34!

#### PoC :
Karena hanya diminta kueri filter nya, maka inputkan kueri berikut:
ip.src == 10.51.40.1 && ip.dst != 10.39.55.34

ip.src atau IP Source merupakan IP asal/sumber, sedangkan ip.dst atau IP Destination merupakan IP tujuan. Lalu, input kueri tersebut dengan nc dan didapatkan flag:
![img](https://i.ibb.co/Sd3j9tt/flag-9.jpg)

### Soal 10
#### Description :
Sebutkan kredensial yang benar ketika user mencoba login menggunakan Telnet!

#### PoC :
Sesuai dengan deskripsi soal, objektifnya adalah mencari kredensial yang berhasil masuk dengan menggunakan protokol telnet. kita coba analisis stream protokol telnet dan ditemukan kredensial yang valid`dhafin:kesayangannyak0k0`.
![image](https://github.com/RenDaemon/Jarkom-Modul-1-IT23-2023/assets/94961661/c30f72e7-f716-434c-aeb3-f7f2ff794d7d)
Submit jawaban ke nc, dan akan didapatkan flag.
![image](https://github.com/RenDaemon/Jarkom-Modul-1-IT23-2023/assets/94961661/67795f1e-6d8d-48d9-9e68-25c53a739003)




