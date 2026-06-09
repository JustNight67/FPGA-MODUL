---
weight: 27
title: "SEVEN SEGMENT"
description: "Memahami konsep dan implementasi Seven Segment Display menggunakan Nexys Board A7"
icon: "Lightbulb"
date: "2025-10-13T12:31:10+07:00"
lastmod: "2025-10-20T18:05:10+07:00"
toc: true
---

Pada bab ini, praktikan akan mempelajari konsep dasar seven segment display dan push button sebagai elemen penting dalam sistem digital. Seven segment display digunakan untuk menampilkan informasi numerik atau karakter, sementara push button berfungsi sebagai input sederhana yang dapat mengubah kondisi atau memicu suatu aksi pada rangkaian. Asisten praktikum atau praktikan diharapkan membaca tujuan dan persyaratan bab ini agar praktikum dapat berjalan sesuai dengan prosedur.

## Tujuan

{{< table "table-striped" >}}
| **TUJUAN** | **PENJELASAN** |
|---------|------|
| **Memahami Konsep Seven Segment Display** | <p style="text-align: justify;>">Praktikan diharapkan dapat memahami cara kerja dan fungsi seven segment display dalam menampilkan angka atau karakter, serta bagaimana mengontrol tiap segmen secara digital.</p> |
| **Mengimplementasikan Seven Segment pada Rangkaian Digital** | <p style="text-align: justify;>">Praktikan diharapkan mampu menghubungkan dan memprogram seven segment display untuk menampilkan angka atau karakter yang diinginkan dalam sebuah sistem digital.</p> |
| **Memahami Fungsi Push Button** | <p style="text-align: justify;>">Praktikan diharapkan dapat memahami mekanisme kerja push button sebagai input digital dan bagaimana push button digunakan dalam sistem digital untuk memicu suatu tindakan </p> |
| **Mengintegrasikan Push Button dengan Seven Segment** | <p style="text-align: justify;>">Praktikan diharapkan dapat merancang dan mengimplementasikan rangkaian yang menggabungkan push button dan seven segment display, seperti menampilkan angka atau mengubah tampilan berdasarkan input dari push button. </p> |
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

*Seven Segment* adalah suatu tampilan digital yang terdiri dari tujuh segmen (bagian) LED (Light Emitting Diode) yang dapat dinyalakan secara individu atau kombinasi untuk menampilkan angka dari 0 hingga 9, serta beberapa huruf seperti A, B, C, E, F. Tampilan ini sangat umum digunakan pada jam digital, kalkulator, dan berbagai perangkat elektronik lainnya.

<div class="d-flex justify-content-center w-60">
<img src="/images/babFive/Ba5-1.png" alt="Gambar 5.1 - Tampilan Seven Segment" class="img-fluid mb-3 responsive-img">
</div>

<p style="text-align: center;"><b>Gambar 5.1</b> Tampilan Seven Segment</p>

<span></span>

Dalam konteks FPGA, Seven Segment dapat dikendalikan secara penuh melalui pemrograman logika. FPGA memberikan fleksibilitas yang sangat tinggi untuk merancang dan mengimplementasikan berbagai macam sistem digital, termasuk tampilan Seven Segment. Seven Segment merupakan salah satu perangkat layar untuk menampilkan sistem angka decimal yang merupakan alternatif dari layar dot-matrix. Seven Segment ini seringkali digunakan pada jam digital, meteran elektronik, dan perangkat elektronik lainnya yang menampilkan informasi numerik. Ide mengenai Seven Segment ini sudah cukup tua, misalnya pada tahun 1910, dimana sudah terdapat layar tujuh segmen yang diterangi oleh lampu pijar yang digunakan pada panel sinyal kamar ketel suatu pembangkit listrik.

<span></span>

Tujuh bagian dari layar dapat dinyalakan dalam bermacam-macam kombinasi untuk menampilkan angka. Seringkali ketujuh segmen tersebut disusun dengan kemiringan tertentu untuk memudahkan pembacaan.

<div class="d-flex justify-content-center w-60">
<img src="/images/babFive/Ba5-2.png" alt="Gambar 5.2 - Seven Segment pada Nexys A7" class="img-fluid mb-3 responsive-img">
</div>

<p style="text-align: center;"><b>Gambar 5.2</b> Seven Segment pada Nexys A7</p>

<span></span>

*Seven Segment* memiliki 7 segmen dimana setiap segmen dikendalikan secara ON dan OFF untuk menampilkan angka yang diinginkan. Angka-angka dari 0 (nol) sampai 9 (sembilan) dapat ditampilkan dengan menggunakan beberapa kombinasi segmen. Selain 0 – 9, Seven Segment juga dapat menampilkan huruf heksadesimal dari A sampai F. Segmen atau elemen-elemen pada Seven Segment diatur menjadi bentuk angka “8” yang agak miring ke kanan dengan tujuan untuk mempermudah pembacaannya. Pada beberapa jenis Seven Segment, terdapat juga penambahan “titik” yang menunjukan angka koma desimal. Terdapat beberapa jenis Seven Segment, diantaranya adalah Incandescent bulbs, Fluorescent lamps (FL), Liquid Crystal Display (LCD), dan Light Emitting Diode (LED).

<div class="d-flex justify-content-center w-60">
<img src="/images/babFive/Ba5-3.png" alt="Gambar 5.3 - Tampilan Angka Seven Segment" class="img-fluid mb-3 responsive-img">
</div>

<p style="text-align: center;"><b>Gambar 5.3</b> Tampilan Angka Seven Segment</p>

## LED Seven Segment

LED Seven Segment umumnya memiliki 7 segmen atau elemen garis dan 1 segmen titik yang menandakan ‘koma’ sebagai desimal atau dot product. Jumlah keseluruhan segmen atau elemen LED sebenarnya terdapat 8.

<span></span>

## Cara Kerja Seven Segment

Setiap segmen LED pada Seven Segment memiliki pin yang terhubung dengan rangkaian pengendali yang berfungsi untuk menentukan segmen mana yang akan menyala dan mana yang akan mati. Dengan mengkombinasikan segmen-segmen yang menyala, pengguna bisa membentuk berbagai macam angka dan huruf. Terdapat 2 jenis LED Seven Segment, diantaranya adalah LED Seven Segment Common Cathoda dan LED Seven Segment Common Anoda.

<div class="d-flex justify-content-center w-60">
<img src="/images/babFive/Ba5-4.png" alt="Gambar 5.4 - Common Anoda dan Common Katoda pada Seven Segment" class="img-fluid mb-3 responsive-img">
</div>

<p style="text-align: center;"><b>Gambar 5.4</b> Common Anoda dan Common Katoda pada Seven Segment</p>

### Common Katoda

Kaki katoda pada semua segmen LED adalah terhubung menjadi 1 pin, sedangkan kaki anoda akan menjadi input untuk masing – masing segmen LED. Kaki katoda yang terhubung menjadi 1 pin ini merupakan terminal negatif (-) atau ground, sedangkan sinyal kendali akan diberikan kepada masing-masing kaki anoda Segmen LED. Cara kerja Seven Segment Common Katoda adalah aktif pada kondisi high ‘1’ untuk menyalakan sebuah segmen.

<div class="d-flex justify-content-center w-60">
<img src="/images/babFive/Ba5-5.png"class="img-fluid mb-3 responsive-img">
</div>

### Common Anoda

Kaki anoda pada semua segmen LED adalah terhubung menjadi 1 pin, sedangkan kaki katoda akan menjadi input untuk masing-masing segmen LED. Kaki anoda yang terhubung menjadi 1 pin ini akan diberi tegangan positif (+) dan sinyal kendali akan diberkan pada masing-masing kaki katoda segmen LED. Cara kerja Seven Segment Common Anoda adalah aktif pada kondisi low ‘0’ untuk menyalakan sebuah segmen.

<div class="d-flex justify-content-center w-60">
<img src="/images/babFive/Ba5-6.png"class="img-fluid mb-3 responsive-img">
</div>

## Prinsip Kerja Dasar Driver System Pada LED Seven Segment

<div class="d-flex justify-content-center w-60">
<img src="/images/babFive/Ba5-7.png" alt="Gambar 5.5 - Skematik Seven Segment" class="img-fluid mb-3 responsive-img">
</div>

<p style="text-align: center;"><b>Gambar 5.5</b> Skematik Seven Segment</p>

<span></span>

Blok Dekoder pada skematik diatas mengubah sinyal input yang diberikan menjadi 8 jalur yaitu A sampai G dan dot product (koma) untuk meng- ON-kan segmen sehingga menghasilkan angka atau digit yang diinginkan. Contohnya, jika output decoder adalah a, b, dan c, maka segmen LED akan menghasilkan angka ‘7’. Jika sinyal input adalah berbentuk analog, maka diperlukan ADC (Analog to Digital Converter) untuk mengubah sinyal analog menjadi sinyal digital sebelum masuk ke input decoder. Jika sinyal input sudah merupakan sinyal digital, maka decoder akan menanganinya sendiri tanpa harus menggunakan ADC.

Fungsi daripada Blok Driver adalah untuk memberikan arus listrik yang cukup kepada segmen LED untuk menyala. Pada tipe decoder tertentu, decoder dapat mengeluarkan tegangan dan arus listrik yang cukup untuk menyalakan segmen LED, maka blok driver ini tidak diperlukan. Pada umunya, driver untuk menyalakan 7 segmen ini adalah terdiri dari 8 transistor switch pada masing- masing elemen LED.
