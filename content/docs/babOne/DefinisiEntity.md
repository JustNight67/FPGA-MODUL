---
weight: 10
title: "Entity"
description: "Memahami Pengertian Entitas yang digunakan pada aplikasi Vivado"
icon: "Accessibility"
date: "2025-08-24T18:41:23+07:00"
lastmod: "2025-08-24T18:41:23+07:00"
toc: true
---

Pada bab ini, praktikan akan mempelajari konsep entity & Architecture dalam VHDL, yang merupakan bagian penting dalam mendefinisikan antarmuka modul pada desain digital. Selain itu, praktikan juga akan mempelajari cara membuat entity sederhana, Praktikan akan mempelajari cara membuat architecture sederhana dan bagaimana architecture berfungsi dalam merancang desain yang lebih besar dan kompleks. Asisten praktikum atau praktikan diharapkan membaca tujuan dan persyaratan pada bab ini agar praktikum dapat berjalan sesuai prosedur.

## Tujuan

{{< table "table-striped" >}}
| **TUJUAN** | **PENJELASAN** |
|---------|------|
| **Mengenal dan memahami tentang entity & Architecture dalam VHDL** | <p style="text-align: justify;>">Praktikan diharapkan dapat memahami konsep dasar entity & Architecture dalam VHDL, jenis-jenis architecture, bagaimana architecture dan entity bekerja bersama dalam mendesain rangkaian digital.</p> |
| **Membuat entity & Architecture sederhana** | <p style="text-align: justify;>">Praktikan diharapkan dapat membuat entity & Architecture sederhana menggunakan VHDL, sehingga dapat memahami struktur penulisan entity serta komponen yang harus ada dalam mendesain suatu rangkaian digital. </p> |
| **Mengenal jenis-jenis library** | <p style="text-align: justify;>">Praktikan diharapkan dapat mengenal berbagai jenis library yang sering digunakan dalam VHDL, memahami fungsi dari setiap library, serta
bagaimana library ini mendukung proses pengembangan desain digital.
</p> |
{{< /table >}}

## Persyaratan

<span class=""> </span>

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

Entity adalah nama dari sebuah desain yang biasanya didalamnya sudah mendefinisikan input dan output dari suatu desain program. Selain itu, entity ini juga dapat mengatur jenis atau tipe port apa yang akan dipakai. Di dalam entity, diperlukan sebuah nama atau variabel untuk menentukan port masukan dan keluaran. Penentuan port mengandung nama, mode, dan tipe data. Mode port terdiri dari 3 jenis, yaitu :

1. IN, merupakan port yang digunakan untuk mendeklarasikan masukan atau input pada desain entity.
2. OUT, merupakan port yang digunakan untuk mendeklarasikan keluaran atau output pada desain entity.
3. INOUT (bidirectional), merupakan port yang dapat digunakan sebagai masukan sekaligus keluaran pada desain entity.

<div class="d-flex justify-content-center w-100">
<img src="/images/babOne/Bao-1.png" alt="Gambar 1.1 - Contoh Desain Entity" class="img-fluid mb-3 responsive-img">
</div>

<p style="text-align: center;"><b>Gambar 1.1</b> Contoh Desain Entity</p>

<span class=""> </span>

Dari gambar tersebut, terdapat sebuah desain yang didalamnya masing- masing terdapat dua input dan dua output. Diketahui bahwa rangkaian diatas merupakan rangkaian *half adder* yang memiliki dua output yaitu Sum dan Carry. Seperti yang sudah dijelaskan diawal, *entity* adalah nama dari sebuah desain yang akan dirancang serta mendefinisikan *input* dan *output*, maka dari itu *entity* dari sebuah desain diatas dapat diberi nama “*Half Adder*”.

*Entity* memberikan arti tentang bagaimana sebuah bagian rancangan dideskripsikan di VHDL dalam hubungannya dengan model VHDL lain dan juga memberikan nama untuk model tersebut. Di dalam entity juga diperbolehkan untuk mendefinisikan beberapa parameter yang mengambil model menggunakan hierarki. Kerangka dasar untuk sebuah entity digambarkan sebagai berikut :

<div class="d-flex justify-content-center w-100">
<img src="/images/babOne/Bao-2.png"
class="img-fluid mb-3 responsive-img">
</div>

Dalam konstruksi ini, <entity_name> akan menjadi nama komponen yang sedang dirancang. Kemudian menggunakan port dalam deklarasi entity VHDL untuk mendefinisikan input dan output dari komponen yang dirancang. Oleh karena itu, *port* sama seperti dengan pin pada komponen elektronik pada umumnya.

*Port* dapat didefinisikan sebagai in, out, atau inout, yang masing-masing berhubungan dengan input, output, dan port bidirectional. Biasanya berbagai jenis port ini disebut sebagai mode. Selain itu, mendeklarasikan jenis data yang digunakan oleh port dalam bagian <signal_type>. Misalkan sebuah entity diberi nama “test”, maka kerangka entity tersebut akan menjadi :

<div class="d-flex justify-content-left w-25">
<img src="/images/babOne/EntityB1.png" class="img-fluid mb-3 responsive-img">
</div>

<span class=""> </span>

<div class="d-flex justify-content-center w-100">
<img src="/images/babOne/Bao-3.png" alt="Gambar 1.2 - Bagan Program" class="img-fluid mb-3 responsive-img">
</div>

<p style="text-align: center;"><b>Gambar 1.2</b> Bagan Program</p>

## Port

Sebuah cara atau metode untuk menghubungkan entity secara bersama adalah menggunakan port. Berikut adalah cara mendefinisikan port atau struktur dari port sebagai berikut :

<div class="d-flex justify-content-center w-100">
<img src="/images/babOne/Bao-4.png" class="img-fluid mb-3 responsive-img">
</div>

Penulisan *port* adalah dengan memberikan nama pada *port* yang akan digunakan kemudian masukan mode *port* dan dilanjutkan dengan tipe data.

<h5> Contoh: </h5>

<div class="d-flex justify-content-center w-100">
<img src="/images/babOne/Bao-5.png" class="img-fluid mb-3 responsive-img">
</div>

Dengan menggunakan port maka titik koneksi diantara entity akan berlangsung dengan efektif dalam hal proses koneksi entity satu sama lain. Selain itu, dengan menggunakan port akan menjadikan sinyal yang ada menjadi efektif serta cocok digunakan dalam model VHDL.

## Keywords dan Define Words

Dalam penulisan entity, dikenal juga istilah “Keywords” dan “Define Words”. Keywords merupakan sintaks yang digunakan untuk menulis program VHDL, sedangkan Define Words adalah deskripsi dari sebuah desain yang ingin kita buat.

<div class="d-flex justify-content-center w-100">
<img src="/images/babOne/Bao-6.png" class="img-fluid mb-3 responsive-img">
</div>

Dari gambar tersebut, tulisan yang berwarna ungu merupakan keywords. Penulisan program VHDL ini harus mengikuti sintaks yang sudah ada, selanjutnya diikuti dengan define words. Define words sebenarnya hanyalah sebuah variabel, kita dapat menuliskan apa saja dengan catatan kita mengetahui define words tersebut akan kita gunakan untuk apa. Berikut merupakan jenis- jenis keyword pada VHDL :

<div class="d-flex justify-content-center w-100">
<img src="/images/babOne/Bao-7.jpg" alt="Gambar 1.3 - Jenis-jenis Keyword pada VHDL" class="img-fluid mb-3 responsive-img">
</div>

<p style="text-align: center;"><b>Gambar 1.3</b> Jenis-jenis Keyword pada VHDL</p>

<ul><li><i>Entity</i>, digunakan untuk menyatakan entity pada VHDL.</li>
<ul><li><i>Architecture,</i> digunakan untuk menyatakan architecture pada VHDL.</li>
<ul><li><i>Process</i>, digunakan untuk tugas-tugas seperti membuat proses yang dikendalikan oleh clock dan operasi kondisional.</li>
<ul><li><i>Signal</i> dan <i>Variable</i>, digunakan untuk membuat objek data dalam VHDL dan keduanya berbeda dalam hal karakteristik penugasan dan waktu.</li>
<ul><li><i>If</i>, <i>then</i>, dan <i>elseif</i>, digunakan sebagai bagian dari pernyataan kondisional yang digunakan dalam VHDL untuk mendefinisikan percabangan di dalam proses atau blok konkuren.</li>
<ul><li><i>Logic Gate</i>, digunakan untuk mendeklarasikan gerbang logika yang akan digunakan pada VHDL.</li>

<span class=""> </span>

## Praktek

### Membuat Entity & Architecture Sederhana

<h5> 1. Buka Aplikasi Vivado 2020 </h5>

<span class=""> </span>

<h5> 2. Buka menu File > Project > New Project </h5>

<div class="d-flex justify-content-center w-80">
<img src="/images/babOne/Bao-8.png" class="img-fluid mb-3 responsive-img">
</div>

<h5> 3. Kemudian akan muncul tampilan diatas dan kemudian pilih next. Setelah itu pilih RTL Project </h5>

<div class="d-flex justify-content-center w-80">
<img src="/images/babOne/Bao-9-1.png" class="img-fluid mb-3 responsive-img">
</div>

<div class="d-flex justify-content-center w-80">
<img src="/images/babOne/Bao-9-2.png" class="img-fluid mb-3 responsive-img">
</div>

<h5> 4. Buatlah nama project seperti diatas kemudian pilih next. </h5>

<div class="d-flex justify-content-center w-80">
<img src="/images/babOne/Bao-10.png" class="img-fluid mb-3 responsive-img">
</div>

<h5> 5. Kemudian muncul tampilan menu baru yaitu <i>add source</i> lalu pastikan target
<i>language</i> yang digunakan adalah VHDL, lalu pilih <i>create file</i>. </h5>

<span class=""> </span>

<h5> 6. Maka tampilan <i>create source file</i> akan muncul dan berikan nama BAB 1 lalu pilih ok. </h5>

<div class="d-flex justify-content-center w-80">
<img src="/images/babOne/Bao-11.png" class="img-fluid mb-3 responsive-img">
</div>

<h5> 7.	Lalu pada tampilan default part pastikan <i>family</i>, <i>package</i> dan <i>speed</i> yang digunakan seperti gambar diatas lalu pilih board yang akan digunakan yaitu <b>xc7a100tcsg324-1</b>. </h5>

<div class="d-flex justify-content-center w-80">
<img src="/images/babOne/Bao-12.png" class="img-fluid mb-3 responsive-img">
</div>

<h5> 8.	Setelah itu akan muncul menu baru yaitu define module yang digunakan untuk mendefinisikan port-port yang akan digunakan. </h5>

<span class=""> </span>

<h5> 9.	Buatlah <i>port name</i> A, B dan C. </h5>

<span class=""> </span>

<h5> 10. Ubah port direction A dan B menjadi in dan port direction C menjadi out, lalu pilih ok. </h5>

<div class="d-flex justify-content-center w-80">
<img src="/images/babOne/Bao-13.png" class="img-fluid mb-3 responsive-img">
</div>

<h5> 11.Kemudian pada bagian <i>sources</i> > <i>design sources</i> akan muncul <i>entity</i> yang telah dibuat sebelumnya, lalu klik 2 kali pada <i>entity</i> yang telah dibuat sebelumnya yaitu BAB 1. </h5>

<div class="d-flex justify-content-center w-80">
<img src="/images/babOne/Bao-14.png" class="img-fluid mb-3 responsive-img">
</div>

<h5> 12. Berikutnya akan muncul tampilan program seperti gambar diatas. </h5>

<span class=""> </span>

Inilah salah satu cara untuk membuat sebuah entity beserta architecture. Sebenarnya kita juga dapat membuat manual dengan cara melewati langkah 8 dan mengisi program itu sesuai dengan apa yang ingin kita buat.

