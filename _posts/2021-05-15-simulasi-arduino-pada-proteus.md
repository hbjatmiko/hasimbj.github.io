---
layout: single
title: "Simulasi Arduino Pada Proteus 8 Professional"
date: 2021-05-15 11:47:00 +0700
categories:
    - Arduino
tags:
    - Arduino
---

Pada kesempatan kali ini, saya ingin berbagi cara simulasi Arduino pada Proteus 8 Professional.

Apa itu Arduino?

> Arduino adalah pengendali mikro single-board (mikrokontroler) yang bersifat open source, diturunkan dari Wiring platform, dirancang untuk memudahkan penggunaan elektronik dalam berbagai bidang.

Lalu, apa itu Proteus?

> Proteus adalah sebuah software untuk mendesain PCB yang dilengkapi dengan simulasi pspice pada level skematik sebelum rangkaian skematik diupgrade ke PCB sehingga sebelum PCB-nya dicetak kita akan tahu apakah PCB yang akan dicetak sudah benar atau belum.

Jadi dengan software Proteus kita dapat melakukan simulasi Arduino tanpa harus memiliki papan Arduino-nya.

## Persiapan

Sebelum mulai, pastikan Proteus dan Arduino IDE sudah terpasang di laptop kamu.

1. [Proteus 8 Professional](https://drive.google.com/drive/folders/10bMxRAFMu3PcUN-DjWY53PmAdTyKBMKB)
2. [Arduino IDE](https://www.arduino.cc/en/software)
3. [Arduino Library for Proteus](https://www.theengineeringprojects.com/downloads?file=31937)

## Menambahkan Arduino Library ke Proteus

Ekstrak berkas Arduino Library for Proteus yang terdiri dari `ArduinoTEP.LIB` dan `ArduinoTEP.IDX` ke dalam folder library Proteus yang berada di `C:\Program Files (x86)\Labcenter Electronics\Proteus 8 Professional\DATA\LIBRARY`.

## Membuat Program Sederhana

Kita akan mencoba membuat program sederhana yakni lampu led berkedip. Buat project baru di Proteus dan buat skema seperti gambar berikut.

![blink-skema.png](/assets/images/arduino/blink-skema.png)

## Program Arduino

Setelah membuat skema rangkaian, buka Arduino IDE dan mulai membuat program untuk lampu led berkedip.

~~~c++
// Blink led

void setup() {
    // Set pin no. 13 sebagai output
    pinMode(13, OUTPUT);
}

void loop() {
    digitalWrite(13, HIGH); // ON
    delay(1000); // delay 1 detik = 1000 ms
    digitalWrite(13, LOW); // OFF
    delay(1000); // delay 1 detik
}
~~~

Setelah program selesai dibuat, lakukan verify pada Arduino IDE.

![kode-blink-arduino.png](/assets/images/arduino/kode-blink-arduino.png)

Salin kode hex hasil verify.

![hex-blink-arduino.png](/assets/images/arduino/hex-blink-arduino.png)

## Simulasi Arduino pada Proteus

Setelah membuat skema dan mendapatkan file hex dari program Arduino. Kini saatnya untuk simulasi menjalankan Arduino pada Proteus.

Klik dua kali pada component arduino, dan edit program file-nya, isi dengan lokasi kode hex program hasil verify tadi.

![program-file-proteus.png](/assets/images/arduino/program-file-proteus.png)

Kemudian pilih OK, dan jalankan simulasinya dengan menekan tombol run. Jika berhasil lampu led akan berkedip selama 1 detik sesuai program.

![run-proteus.png](/assets/images/arduino/run-proteus.png)

Sekian postingan kali ini, semoga bermanfaat.

Referensi:

1. [https://binus.ac.id/bandung/2020/03/proteus-sebagai-aplikasi-software-pengendali-mikrokontroller/](https://binus.ac.id/bandung/2020/03/proteus-sebagai-aplikasi-software-pengendali-mikrokontroller/)
