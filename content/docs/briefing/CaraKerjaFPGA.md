---
weight: 5
title: "Cara Kerja FPGA"
description: "Memahami cara kerja Field Programmable Gate Array"
icon: "schema"
date: "2026-05-15T11:44:28+07:00"
lastmod: "2026-05-15T11:44:28+07:00"
toc: true
---

FPGA tersusun dari logic block yang saling terhubung satu sama lain. Kumpulan-kumpulan dari logic block ini berjumlah ratusan bahkan ribuan sehingga membentuk suatu fungsi yang kompleks. Sebuah logic block pada dasarnya terdiri dari sebuah LUT (*Lookup Table*), *Flip-Flop*, dan *Multiplexer*.

## LUT (Lookup Table)

LUT atau Lookup Table merupakan sejenis RAM yang berkapasitas kecil. Pada FPGA, LUT ini memegang peran dalam proses implementasi fungsi-fungsi logika dan mempunyai ciri khas yaitu memiliki 4 masukan.

<div class="d-flex justify-content-center w-100">
<img src="/images/briefing/Bri-4.png" alt="Gambar B.4 - Logic-Cell" class="img-fluid mb-3 responsive-img">
</div>

<p style="text-align: center;"><b>Gambar B.4</b> Logic-Cell</p>

## Flip-Flop

Flip-flop merupakan sebuah rangkaian yang memiliki dua keadaan stabil dan mewakili satu bit. Flip-flop adalah resource penyimpanan terkecil pada FPGA. Setiap flip-flop dalam sebuah CLB adalah register biner yang digunakan untuk menyimpan status logika antara siklus clock pada rangkaian FPGA.

<div class="d-flex justify-content-center w-100">
<img src="/images/briefing/Bri-5.png" alt="Gambar B.5 - Rangkaian Flip-Flop" class="img-fluid mb-3 responsive-img">
</div>

<p style="text-align: center;"><b>Gambar B.5</b> Rangkaian Flip-Flop</p>

## Multiplexer

*Multiplexer* bekerja sebagai switch (saklar) yang menghubungkan beberapa input menjadi satu input-an saja. Setiap logic block dapat dihubungkan dengan logic block lainnya melalui jalur koneksi yang ada. Setiap block hanya mampu bekerja secara ringkas dan sederhana, namun apabila antar block saling terhubung satu sama lain, maka sebuah fungsi-fungsi logika yang kompleks dapat terbentuk.

<div class="d-flex justify-content-center w-100">
<img src="/images/briefing/Bri-6.png" alt="Gambar B.6 - Kumpulan Logic-Cell" class="img-fluid mb-3 responsive-img">
</div>

<p style="text-align: center;"><b>Gambar B.6</b> Kumpulan Logic-Cell</p>

<span class=""> </span>

<div class="d-flex justify-content-center w-100">
<img src="/images/briefing/Bri-7.png" alt="Gambar B.7 - Kumpulan Configurable Logic Block" class="img-fluid mb-3 responsive-img">
</div>

<p style="text-align: center;"><b>Gambar B.6</b> Kumpulan Configurable Logic Block</p>

