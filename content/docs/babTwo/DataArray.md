---
weight: 16
title: "Array"
description: "Memahami definisi, jenis, karakteristik dan contoh program array"
icon: "Data_Array"
date: "2025-09-13T16:48:46+07:00"
lastmod: "2025-09-13T16:48:46+07:00"
toc: true
---

## Definisi tipe data Array

Array adalah struktur data yang terdiri dari kumpulan elemen yang memiliki tipe data yang sama, disusun dalam urutan tertentu, dan diakses menggunakan indeks. Dalam konteks FPGA, array digunakan untuk menyimpan dan mengelola data secara efisien.

## Jenis Array

Terdapat 2 jenis array yang ditentukan dalam standar VHDL, yaitu:

### String

merupakan karakter yang digunakan untuk menyimpan teks, seperti pesan atau data komunikasi.

Variable MESSAGE : STRING (1 to 10) := "Acsl";

<span></span>

### Bit Vector

merupakan sebuah array dari tipe data BIT yang dikelompokkan. Biasanya digunakan untuk mendefinisikan banyak input pin. Jika kita ingin membuat sebuah rangkaian dengan 4 input, daripada mendefinisikannya satu persatu, kita dapat membuatnya lebih sederhana dengan menggunakan BIT vector ini. Contoh :

Signal input : BIT_VECTOR (3 downto 0);

<span></span>

Pernyataan tersebut mendefinisikan input 4 bit. Untuk mengaturnya, kita dapat menggunakan input (0) untuk mengakses bit pertama dan (1) untuk bit kedua, begitu seterusnya. Contoh :

Input <= "0101";

## Karakteristik Array

<ul><li>Semua elemen dalam array memiliki tipe data yang sama.</li></ul>
<ul><li>Setiap elemen dalam array diakses menggunakan indeks, yang biasanya dimulai dari 0</li></ul>
<ul><li>Ukuran array biasanya ditentukan saat deklarasi dan tidak dapat diubah selama <i>runtime</i> atau saat sedang dijalankan.</li></ul>

## Contoh Program

Contoh di bawah ini adalah BIT Vector sederhana yang meringkas 2 input A.

<div class="d-flex justify-content-center w-100">
<img src="/images/babTwo/Batw-2.png"
class="img-fluid mb-3 responsive-img">
</div>

Contoh dibawah ini memiliki output setiap array vector merupakan kebalikan dari input-nya.

<div class="d-flex justify-content-center w-100">
<img src="/images/babTwo/Batw-3.png"
class="img-fluid mb-3 responsive-img">
</div>

<span></span>

## Soal

<div class="alert alert-info" role="alert">
<h5 class="alert-heading"><i class="material-icons align-middle me-2">assignment</i>Tugas Praktikum</h5>
<hr>
<p class="mb-3"><strong>Kerjakanlah soal latihan berikut ini:</strong></p>

<span></span>

<div class="row">
<p class="mb-2"><strong>Soal 1:</strong></p>
</div>

<span></span>

<center>
      <img src="/images/BabTwo/Batw-4.png" class="img-fluid mb-3 responsive-img">
</center>

<div class="row">
<p class="mb-2"><strong>Soal 2:</strong></p>
</div>

<span></span>

<center>
      <img src="/images/BabTwo/Batw-5.png" class="img-fluid mb-3 responsive-img">
</center>

<div class="row">
<p class="mb-2"><strong>Soal 3:</strong></p>
</div>

<span></span>

<center>
      <img src="/images/BabTwo/Batw-6.png" class="img-fluid mb-3 responsive-img">
</center></div>
