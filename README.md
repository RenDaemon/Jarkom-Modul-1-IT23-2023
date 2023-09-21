# Jarkom Modul 1
- [Soal 1](#soal-1)
- [Soal 2](#soal-2)
- [Soal 3](#soal-3)
- [Soal 4](#soal-4)
- [Soal 5](#soal-5)
- [Soal 6](#soal-6)
- [Soal 7](#soal-7)
- [Soal 8](#soal-8)
- [Soal 9](#soal-9)
- [Soal 10](#soal-10)

### Soal 1  
#### Description :
User melakukan berbagai aktivitas dengan menggunakan protokol FTP. Salah satunya adalah **mengunggah suatu file**.

#### PoC :
Dari deskripsi soal tersebut kita diminta untuk menganalisis protokol FTP terutama pada suatu aksi tertentu yaitu **upload** file. Dari hasil analisis terdapat sebuah packet FTP yang terlihat mencurigakan, Ditemukan request STOR file GrabThePhisher.zip
![image](/uploads/6a7c2d78bb1904a21a0c060bd430bd2c/image.png)
Klik 2x lalu buka Transmission Control Protocol dan cari Sequence Number (raw) dan Acknowledgment number (raw).
untuk menemukan Response, dibawah Request ‘STOR’, Klik 2x lalu buka Transmission Control Protocol dan cari Sequence Number (raw) dan Acknowledgment number (raw).
![image](/uploads/9f963cee0ebd9e158072038d0f48c170/image.png)
![image](/uploads/29a6b31121c896da9f959ff1868d6e4c/image.png)
Copy semua value yang dibutuhkan, dan submit jawabannya melalui nc dan akan didapatkan flag.

### Soal 2
#### Description :
Sebutkan web server yang digunakan pada portal praktikum Jaringan Komputer!

#### PoC :
Dari deskripsi soal tersdebut kita diminta untuk mengetahui web server yang digunakan. Coba saja analisis packetnya dan cek pada header response pada salah satu packet untuk menemukannya.
![image](/uploads/d3f9d7ebf8423cb620ab6f96430a0265/image.png)
web-server yang digunakan adalah gunicorn, langsung saja submit jawabannya ke nc dan akan didapatkan flag
![image](/uploads/c2922f84c1c4e26c9c450915aefd16d2/image.png)  


### Soal 3 :
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

Submit semua jawaban tersebut dan akan didapatkan flag.
![image](/uploads/b465bac46162926a44a84581f3ee29fd/image.png)  

### Soal 4 :
#### Description :
Berapa nilai checksum yang didapat dari header pada paket nomor 130?

#### PoC :
Dari deskripsi soal tersebut, kita diminta untuk mengetahui value checksum yang dimiliki oleh packet ke 130. Untuk mendapatkannya cukup kita filtering dengan `frame.number == 130` dan check nilai checksum pada bagian header. Didapatkan bahwa nilai checksum adalah `0x18e5`.
![image](/uploads/45580276d462c3ced15ea23c5fab9f5e/image.png)
Submit jawabannya ke nc dan akan didapatkan flag.
![image](/uploads/352c72d4d6adae3c10f0abca08849743/image.png)

### Soal 5 :
#### Description :
Elshe menemukan suatu file packet capture yang menarik. Bantulah elshe untuk menganalisis file packet capture tersebut.

#### PoC :
Diberikan 1 file pcap dan 1 file zip(protected). Untuk menemukan password kita lakukan analisis terhadap file pcap, dan benar saja follow tcp stream langsung kita dapatkan password file zip dalam bentuk base64.
![image](/uploads/f5a6a6d5ee30edab798c30208fbfb42f/image.png)
Decrypt passwordnya, didapatkan `5implePas5word` . Setelah dibuka file zipnya ternyata isinya adalah nc ke suatu address.
![image](/uploads/561427f3227e7d0fd65ad4a69d8fd8de/image.png)
Setelah terhubung, terdapat 3 pertanyaan :
- Jumlah packet = `61`
- Port pada server untuk smtp = `25`
- Public IP = `74.53.140.153`
jawaban" tersebut diperoleh dari analisis packetnya.
![image](/uploads/d821111be7761e9ecba1fd539772da3a/image.png)
Submit semua jawaban, maka akan didapatkan flag.
![image](/uploads/8b76896a1c5731a2d338663a24e0ebc6/image.png)

### Soal 8
#### Description :
Berikan kueri filter sehingga wireshark hanya mengambil semua protokol paket yang menuju port 80! (Jika terdapat lebih dari 1 port, maka urutkan sesuai dengan abjad)!

#### PoC :
Untuk soal no.8 kita hanya perlu untuk submit filtering sesuai dengan yang di soal dengan nc dan akan didapatkan flag.
![image](/uploads/1f2a42a35a923f6f69eaf11b1498b275/image.png)

### Soal 10
#### Description :
Sebutkan kredensial yang benar ketika user mencoba login menggunakan Telnet!

#### PoC :
Sesuai dengan deskripsi soal, objektifnya adalah mencari kredensial yang berhasil masuk dengan menggunakan protokol telnet. kita coba analisis stream protokol telnet dan ditemukan kredensial yang valid`dhafin:kesayangannyak0k0`.
![image](/uploads/15e675f4a7494670ea85397dc282aa62/image.png)
Submit jawaban ke nc, dan akan didapatkan flag.
![image](/uploads/b9c6fa2f54f1fc63f09621ea8b487b4d/image.png)






