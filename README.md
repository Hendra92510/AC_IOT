# AC_IOT
Membuat kendali remot AC agar bisa digunakan melewati internet (Internet of Things)

Rancang Bangun Kendali Air Conditioner berbasis IoT

![image.png](https://github.com/Hendra92510/AC_IOT/blob/main/Dokumentasi/alat%20jadi.png)

Project ini memanfaatkan kode blok setiap tombol AC target untuk kontrol AC. 
Alat yang dibutuhkan antara lain:
- Menggunakan KY-022 untuk merekam kode blok AC dengan infrared.
- KY-005 untuk transmit hasil blok rekam remot dengan infrared.
- DS18B2 untuk sensor suhu dan kelembaban guna memonitor suhu dan kelembaban ruangan.
- Arduino UNO sebagai penampung kode sementara yang nantinya akan dilakukan copy kode rekam remot ke ESP8266.
- ESP8266 sebagai mikrokontroler untuk transmit kode rekam remot dan menghubungkan alat ke internet melewati WiFi.
- Blynk sebagai interface kontrol AC.

![image.png](https://github.com/Hendra92510/AC_IOT/blob/main/Dokumentasi/blok%20diagram.png)

Cara kerja:
- merekam remot kode AC dengan KY-022 dan ditampung didalam Arduino UNO.
- copy hasil rekam kode AC kedalam ESP8266 dan konfirgurasi DS18B2 untuk suhu dan kelembaban.
- uji coba transmit dengan KY-005 ke AC melewati Blynk sebagai interface melalui internet.

Yang dimaksud blok rekam remot adalah kode dimana tercipta ketika tombol AC ditekan. kode rekam remot bisa seperti ini:

Raw: (229) 3224, -2920, 3176, -4324, 668, -1548, 668, -436, 636, -1576, 668, -436, 636, -464, 668, -1548, 668, -1548, 660, -440, 688, -1528, 640, -464, 668, -1548, 696, -1520, 664, -436, 664, -436, 664, -1556, 636, -464, 692, -408, 664, -436, 668, -432, 696, -408, 664, -436, 692, -408, 664, -436, 668, -432, 664, -436, 664, -440, 636, -464, 692, -408, 636, -464, 700, -404, 632, -1584, 664, -436, 636, -464, 636, -1580, 636, -464, 720, -384, 660, -440, 664, -436, 664, -436, 668, -432, 668, -432, 668, -436, 636, -1580, 692, -408, 664, -436, 636, -468, 636, -464, 660, -440, 664, -436, 636, -464, 664, -436, 640, -464, 664, -436, 696, -404, 692, -408, 720, -380, 668, -436, 636, -464, 664, -1552, 692, -408, 640, -464, 632, -468, 664, -436, 664, -436, 664, -436, 640, -464, 636, -464, 668, -432, 664, -436, 668, -432, 640, -464, 688, -412, 636, -464, 668, -436, 660, -436, 668, -436, 664, -436, 636, -464, 668, -432, 640, -464, 664, -436, 668, -432, 664, -440, 664, -436, 664, -436, 668, -432, 668, -432, 640, -460, 664, -440, 692, -408, 664, -436, 632, -468, 668, -436, 632, -468, 636, -464, 664, -436, 672, -432, 664, -436, 688, -412, 664, -440, 660, -436, 696, -1524, 664, -436, 664, -1552, 664, -1556, 660, -1552, 640, -464, 664, -1552, 664, -1552, 640, -1576, 700, -1516, 696, -1524, 664,

Setiap tombol dan merk tipe AC akan menghasilkan kode yang berbeda beda. untuk menggunakan sebagai transmit, maka tanda negatif di awalan angka harus hilang. untuk transmit akan seperti kode dibawah ini:

3224,2920,3176,4324,668,1548,668,436,636,1576,668,436,636,464,668,1548,668,1548,660,440,688,1528,640,464,668,1548,696,1520,664,436,664,436,664,1556,636,464,692,408,664,436,668,432,696,408,664,436,692,408,664,436,668,432,664,436,664,440,636,464,692,408,636,464,700,404,632,1584,664,436,636,464,636,1580,636,464,720,384,660,440,664,436,664,436,668,432,668,432,668,436,636,1580,692,408,664,436,636,468,636,464,660,440,664,436,636,464,664,436,640,464,664,436,696,404,692,408,720,380,668,436,636,464,664,1552,692,408,640,464,632,468,664,436,664,436,664,436,640,464,636,464,668,432,664,436,668,432,640,464,688,412,636,464,668,436,660,436,668,436,664,436,636,464,668,432,640,464,664,436,668,432,664,440,664,436,664,436,668,432,668,432,640,460,664,440,692,408,664,436,632,468,668,436,632,468,636,464,664,436,672,432,664,436,688,412,664,440,660,436,696,1524,664,436,664,1552,664,1556,660,1552,640,464,664,1552,664,1552,640,1576,700,1516,696,1524,664

Menghitung kapasitas AC menggunakan rumus:

![image.png](https://github.com/Hendra92510/AC_IOT/blob/main/Dokumentasi/rumus.png)

Denah Rumah Lantai 2:

![image.png](https://github.com/Hendra92510/AC_IOT/blob/main/Dokumentasi/Denah%20rumah.png)

Uji coba dilakukan pada ruangan kamar1 yang mempunyai ukuran 3m x 2,8m x 3.2m.
Dengan rumus tersebut didapatkan:

![image.png](https://github.com/Hendra92510/AC_IOT/blob/main/Dokumentasi/hasil%20rumus.png)

Untuk mengetahui tipe AC yang optimal digunakan didalam ruangan tersebut dapat melihat tabel dibawah ini. Tabel bersebut berguna untuk konversi BTU ke AC berapa PK sesuai dengan hasil perhitungan.

![image.png](https://github.com/Hendra92510/AC_IOT/blob/main/Dokumentasi/tabel%20BTU.png)

Untuk ruangan yang dilakukan uji coba, berdasarkan tabel konversi BTU maka AC lebih optimal jika ukuran PKnya adalah diantara 1/2PK dan 3/4PK.

Interface Blynk dapat dilihat pada gambar berikut:

![image.png](https://github.com/Hendra92510/AC_IOT/blob/main/Dokumentasi/Blynk.png)

Video Demo dapat dilihat di link berikut:
https://drive.google.com/file/d/13wOZnZk3XRfqt5Yi-eVZ8-_u84_L6XZX/view?usp=sharing
