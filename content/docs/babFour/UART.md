---
weight: 21
title: "UART (Universal Asynchronous Receiver-Transmitter)"
description: "Memahami konsep dasar dan fungsi dari UART"
icon: "Developer_Board"
date: "2025-10-13T12:24:40+07:00"
lastmod: "2025-10-13T12:24:40+07:00"
toc: true
---

Pada bab ini, praktikan akan mempelajari konsep dasar dan fungsi dari UART (Universal Asynchronous Receiver-Transmitter), yang merupakan komponen penting dalam komunikasi serial. Praktikan akan mempelajari cara kerja UART dan bagaimana mengimplementasikannya pada FPGA untuk mendeskripsikan proses transmisi dan penerimaan data secara asinkron. Selain itu, praktikan akan memahami peran FTDi chip dalam konversi sinyal USB ke sinyal serial. Asisten praktikum atau praktikan diharapkan membaca tujuan dan persyaratan bab ini agar praktikum dapat berjalan sesuai dengan prosedur.

## Tujuan

{{< table "table-striped" >}}
| **TUJUAN** | **PENJELASAN** |
|---------|------|
| **Memahami Fungsi dan Cara Kerja UART** | <p style="text-align: justify;>">Praktikan diharapkan dapat memahami fungsi UART sebagai modul komunikasi serial yang bertugas mengonversi data paralel menjadi data serial dan sebaliknya.</p> |
| **Mengimplementasikan UART Pada FPGA** | <p style="text-align: justify;>">Praktikan diharapkan mampumengimplementasikan modul UART pada FPGA menggunakan bahasa pemrograman VHDL atau Verilog.</p> |
| **Memahami Fungsi dan Cara Kerja FTDI Chip** | <p style="text-align: justify;>">Praktikan akan memahami cara kerja FTDI chip, serta bagaimana chip ini digunakan dalam proyek FPGA untuk mempermudah koneksi serial dengan perangkat eksternal seperti komputer </p> |
{{< /table >}}

## Persyaratan

<span></span>

Disarankan praktikan menggunakan hardware dan software sesuai pada dokumentasi ini. Apabila terdapat versi hardware atau software yang cukup lama dari versi yang direkomendasikan maka sebaiknya bertanya kepada Asisten Mengajar Shift.

{{< table "table-striped" >}}
| **HARDWARE YANG DIBUTUHKAN PRAKTIKUM** |
|--|--|
| **PC / Laptop** | 
| **FPGA Board Nexys A7 dan Nexys 4** | 
| **Kabel Power USB** | 
{{< /table >}}

{{< table "table-striped" >}}
| **SOFTWARE YANG DIBUTUHKAN PRAKTIKUM** |
|--|--|
| **Vivado Design Suite**|
{{< /table >}}

{{< alert context="info" text="Diusahakan untuk memakai **Versi** dan **Aplikasi** yang sama agar tidak terjadinya kesalahan yang tidak diinginkan!." />}}

## Pengertian

UART adalah kepanjangan dari *Universal Asynchronous Receiver/Transmitter* adalah perangkat keras yang menerjemahkan antara bit- bit paralel data dan serial. UART umumnya digunakan sebagai protokol komunikasi serial asinkron dalam pengiriman data antara perangkat satu dengan yang lainnya. Sebagai contoh, komunikasi antara sesama mikrokontroler atau mikrokontroler dengan PC.

<div class="d-flex justify-content-center w-60">
<img src="/images/babFour/Ba4-1.png" alt="Gambar 4.1 - Port UART pada Nexys A7" class="img-fluid mb-3 responsive-img">
</div>

<p style="text-align: center;"><b>Gambar 4.1</b> Port UART pada Nexys A7</p>

## Cara Kerja UART

Dalam pengiriman data menggunakan UART, baud rate antara pengirim dan penerima harus sama karena paket data dikirim tiap bit mengandalkan clock tersebut. Inilah salah satu keuntungan menggunakan model asynchronous dalam pengiriman data karena dengan hanya satu kabel transmisi maka data dapat dikirimkan. Berbeda dengan model synchronous yang terdapat pada protocol SPI dan I2C karena protokol tersebut membutuhkan minimal dua kabel dalam transmisi data, yaitu transmisi clock dan data. Namun, kelemahan model asynchronous adalah dalam hal kecepatannya dan jarak transmisi. Semakin cepat dan jauhnya jarak transmisi, membuat paket-paket bit data menjadi terdistorsi sehingga data yang dikirim atau diterima bisa mengalami error.

<h5>Transmitter/Pengiriman Data</h5>

Data paralel dari perangkat sumber dikonversi menjadi data serial oleh UART. Bit data dikirim secara berurutan melalui jalur komunikasi serial.

<ul><li>Data paralel dari perangkat sumber dikonversi menjadi data serial oleh UART dan dibagi menjadi bit-bit individu.</ul></li>
<ul><li>Bit individu dari data yang dikirim dimulai dari yang terkecil pertama (LSB).</ul></li>
<ul><li>Bit start (0) dikirim untuk menandai awal transmisi.</ul></li>
<ul><li>Setelah bit start, dikirimkan bit-bit data.</ul></li>
<ul><li>Bit parity (opsional) dikirim untuk deteksi kesalahan.</ul></li>
<ul><li>Setelah semua bit data dikirim, dikirimkan bit stop.</ul></li>
<ul><li>Bit stop (1) dikirim untuk menandai akhir transmisi.</ul></li>

<span></span>

Setiap bit yang ditransmisikan serupa dengan jumlah bit lainnya, dan penerima mendeteksi jalur disekitar pertengahan periode setiap bit untuk menentukan apakah bit adalah 1 atau 0. Misalnya, jika dibutuhkan dua detik untuk mengirim setiap bit, penerima akan memeriksa sinyal untuk menentukan apakah itu adalah 1 atau 0 setelah satu detik telah berlalu.

<h5>Receiver/Penerimaan Data</h5>

UART menerima data serial dan mengonversinya kembali menjadi data paralel untuk perangkat tujuan.

<ul><li>Bit start dideteksi untuk menyinkronkan penerima dengan kecepatan data</ul></li>
<ul><li>Ketika terdeteksi bit start, perangkat penerima mulai mengukur waktu.</ul></li>
<ul><li>Pada setiap batas waktu, perangkat penerima membaca nilai bit data.</ul></li>
<ul><li>Bit data diterima dan dirakit sesuai urutan.</ul></li>
<ul><li>Bit parity diperiksa untuk deteksi kesalahan.</ul></li>
<ul><li>Bit stop dideteksi untuk menandai akhir transmisi.</ul></li>

## Komunikasi Serial

UART pada dasarnya merupakan protokol komunikasi serial. Artinya, data dikirimkan bit demi bit melalui satu saluran komunikasi. Komunikasi serial adalah proses pengiriman bit data satu per satu, secara berurutan, melalui sebuah saluran komunikasi. Hal ini berbeda dengan komunikasi paralel, dimana beberapa bit dikirim secara keseluruhan, link dengan beberapa saluran paralel. UART menggunakan komunikasi serial karena hanya membutuhkan dua kabel utama (TX dan RX) untuk komunikasi dua arah, sehingga lebih hemat biaya dan mudah diimplementasikan.

Metode komunikasi serial sering disebut dengan TTL Serial (transistor- transistor logic). Komunikasi serial pada tingkat TTL akan selalu tetap antara batas 0V dan VCC, yang sering digunakan yaitu 5V atau 3.3V. Sebuah logika tinggi (1) diwakili oleh VCC sedangkan logika rendah (0) adalah 0V.

<div class="d-flex justify-content-center w-60">
<img src="/images/babFour/Ba4-2.png" alt="Gambar 4.2 - Komunikasi Serial dan Paralel" class="img-fluid mb-3 responsive-img">
</div>

<p style="text-align: center;"><b>Gambar 4.2</b> Komunikasi Serial dan Paralel</p>

Pada saat berkomunikasi, semakin tinggi frekuensi pengiriman data, maka semakin tinggi juga gangguan elektromagnetik. Setiap kabel dapat diperlakukan sebagai antena untuk menangkap noise yang ada di sekitarnya yang mengganggu data yang sedang ditransmisikan. Dalam komunikasi paralel, karena banyaknya kabel yang digunakan, masalah gangguan elektromagnetik menjadi lebih serius. Komunikasi serial dibutuhkan jumlah kabel yang lebih sedikit, bisa hanya menggunakan tiga kabel, yaitu saluran **Transmit Data** (TX), saluran **Receive Data** (RX) dan saluran **Ground** (GND).

### Jenis-jenis Komunikasi Serial

<h5>a. Synchronous</h5>

Sebuah pengiriman data serial yang disertai dengan clock sebagai pengatur waktu untuk mengindikasi bahwa ada bit siap untuk dibaca. Contoh : I2C, USRT, SPI, dll.

<h5>b. Aynchronous</h5>

Sebuah pengiriman data dimana clock tidak dikirim bersamaan dengan data sehingga masing-masing perangkat keras yang berkomunikasi harus membuat clock-nya sendiri yang sama. Contoh : UART, RS- 232, USB, dll.

<h5>c. Full Duplex</h5>

Jenis komunikasi serial yang menyatakan hubungan antara dua perangkat keras. Misalnya ada sebuah perangkat A dan B, jika A sedang melakukan pengiriman data, pada saat yang sama A dapat menerima data dari B, begitupun sebaliknya. Kondisi ini dinamakan full duplex atau komunikasi dua arah, contohnya adalah telepon.

<h5>d. Half Duplex</h5>

Kondisi ketika proses pengiriman dan penerimaan data tidak dapat dilakukan secara bersamaan, namun secara bergantian. Contohnya adalah walkie talkie.

<h5>e. Simplex</h5>

Jenis komunikasi dimana pengiriman hanya terjadi satu arah saja kepada penerima. Contohnya seperti broadcast sebuah pesan atau seperti TV.

<div class="d-flex justify-content-center w-60">
<img src="/images/babFour/Ba4-3.png" alt="Gambar 4.3 - Simplex, Full Duplex, Half Duplex" class="img-fluid mb-3 responsive-img">
</div>

<p style="text-align: center;"><b>Gambar 4.3</b> Simplex, Full Duplex, Half Duplex</p>
