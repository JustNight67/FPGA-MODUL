---
weight: 37
title: "ALU (Arithmetic Logic Unit)"
description: "Memahami konsep dasar dari ALU pada FPGA"
icon: "Equal"
date: "2025-09-13T16:48:46+07:00"
lastmod: "2025-09-13T16:48:46+07:00"
toc: true
---

Pada bab ini, praktikan akan mempelajari konsep dasar dari Arithmetic Logic Unit (ALU) serta implementasinya dalam sistem digital menggunakan FPGA. ALU merupakan komponen penting dalam pemrosesan data yang mampu melakukan operasi aritmatika seperti penjumlahan dan pengurangan, serta operasi logika. Asisten praktikum atau praktikan diharapkan membaca tujuan dan persyaratan bab ini agar praktikum dapat berjalan sesuai dengan prosedur.

## Tujuan

{{< table "table-striped" >}}
| **TUJUAN** | **PENJELASAN** |
|---------|------|
| **Memahami Konsep ALU (Arithmetic Logic Unit)** | <p style="text-align: justify;>">Praktikan diharapkan dapat memahami konsep dasar dari ALU, termasuk operasi aritmatika dan logika yang dapat dilakukan oleh unit ini dalam sebuah sistem digital.</p> |
| **Mengimplementasikan ALU 3-bit pada FPGA** | <p style="text-align: justify;>">Praktikan diharapkan mampu membuat dan memprogram ALU sederhana yang dapat melakukan operasi penjumlahan, pengurangan, dan logika dasar menggunakan FPGA.</p> |
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

## Pengertian ALU

ALU (Arithmetic Logic Unit) adalah komponen utama dari Central Processing Unit atau CPU yang bertugas untuk melakukan operasi aritmatika dan operasi logika menggunakan nilai biner. ALU dapat melakukan operasi aritmatika dan logika berdasarkan input yang dimasukkan dan operasi apa yang akan dilakukan dengan memilih pada bagian operand atau selector seperti operasi pertambahan, pengurangan, perkalian dan lain lain. Unit pemrosesan pada ALU dibagi menjadi dua bagian yaitu AU (Arithmetic Unit) dan LU (Logic Unit).

<ul><li><b>Arithmetic Unit :</b> Bagian dari ALU yang melakukan operasi matematika yang termasuk dalam operasi sederhana yaitu pertambahan, pengurangan, perkalian,dan pembagian. Arithmetic Unit bekerja dengan menggunakan bilangan biner sebagai input ataupun sebagai outputnya,</li></ul>
<ul><li><b>Logic Unit :</b> Bagian dari ALU yang melakukan operasi logika berdasarkan gerbang-gerbang logika dasar seperti AND, OR, NOT dan gerbang logika lainnya, selain operasi logika bagian ini juga dapat melakukan operasi perbandingan dan operasi bitwise yang digunakan untuk menggeser dan memutar nilai bit.</li></ul>

<div class="d-flex justify-content-center w-60">
<img src="/images/babSeven/Ba7-1.png" alt="Gambar 7.1 - Rangkaian ALU" class="img-fluid mb-3 responsive-img">
</div>

<p style="text-align: center;"><b>Gambar 7.1</b> Rangkaian ALU</p>

<span></span>

ALU secara internal selalu melakukan beberapa operasi seperti penjumlahan, pengurangan, pembagian, dan perkalian. Kita harus menentukan hasil mana yang ingin dihasilkan sebagai output dengan menggunakan operand atau selector. Dalam praktikum ini, kita akan mengimplementasikan ALU 3-bit yang akan melakukan operasi aritmatika menggunakan bilangan biner dan operasi yang akan dilakukan adalah Adder (penjumlahan), Subtractor (pengurangan), Multiplier (perkalian), dan Comparator (pembanding).

<div class="d-flex justify-content-center w-60">
<img src="/images/babSeven/Ba7-2.png" alt="Gambar 7.2 - 3-Bit ALU" class="img-fluid mb-3 responsive-img">
</div>

<p style="text-align: center;"><b>Gambar 7.2</b> 3-Bit ALU</p>
