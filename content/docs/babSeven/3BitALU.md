---
weight: 38
title: "3-Bit ALU (Arithmetic Logic Unit)"
description: "Memahami Rangkaian 3 bit pada ALU seperti Adder, Subtractor, Multiplier, dan Comparator"
icon: "Counter_3"
date: "2025-09-13T16:48:46+07:00"
lastmod: "2025-09-13T16:48:46+07:00"
toc: true
---

## 3-Bit Adder

Rangkaian 3-Bit Adder melakukan penjumlahan biner dengan input yang memiliki nilai 3-bit, rangkaian 3-Bit adder dapat dibuat dengan cara menghubungkan 3 rangkaian full adder menjadi satu rangkaian. Setiap full adder menjumlahkan satu bit dari setiap bilangan biner dan carry dari full adder sebelumnya. Output dari 3-bit adder adalah bilangan biner 4-bit, yang merupakan hasil dari penjumlahan dari dua bilangan biner 3-bit.

<div class="d-flex justify-content-center w-60">
<img src="/images/babSeven/Ba7-3.png" alt="Gambar 7.3 - Skematik 3-Bit Adder" class="img-fluid mb-3 responsive-img">
</div>

<p style="text-align: center;"><b>Gambar 7.3</b> Skematik 3-Bit Adder</p>

## 3-Bit Subtractor

Rangkaian 3-Bit Subtractor melakukan pengurangan biner dengan input yang memiliki nilai 3-bit, rangkaian 3-Bit Subtractor dapat dibuat dengan cara menghubungkan 3 rangkaian full subtractor menjadi satu rangkaian. Setiap full subtractor mengurangkan satu bit dari bilangan biner pertama dengan satu bit dari bilangan biner kedua dan borrow dari full subtractor sebelumnya. Output dari 3-bit subtractor adalah bilangan biner 3-bit yang merupakan selisih antara dua bilangan biner 3-bit dan sebuah borrow output.

<div class="d-flex justify-content-center w-60">
<img src="/images/babSeven/Ba7-4.png" alt="Gambar 7.4 - Skematik 3-Bit Subtractor" class="img-fluid mb-3 responsive-img">
</div>

<p style="text-align: center;"><b>Gambar 7.3</b> Skematik 3-Bit Subtractor</p>

## 3-Bit Multiplier

Rangkaian 3-Bit Multiplier adalah rangkaian yang digunakan untuk melakukan  operasi  perkalian  dua  bilangan  biner  3-bit.  Rangkaian ini menghasilkan output 6 bit yang merupakan hasil dari perkalian dari kedua bilangan.

<div class="d-flex justify-content-center w-60">
<img src="/images/babSeven/Ba7-5.png" alt="Gambar 7.5 - Skematik 3-Bit Multiplier" class="img-fluid mb-3 responsive-img">
</div>

<p style="text-align: center;"><b>Gambar 7.3</b> Skematik 3-Bit Multiplier</p>

## 3-Bit Comparator

Comparator adalah rangkaian yang digunakan untuk membandingkan nilai berdasarkan input yang diterimanya. Comparator 3-bit adalah rangkaian yang membandingkan antara kedua input yang memiliki nilai 3-bit dan menghasilkan output berdasarkan perbandingan nilai biner kedua input tersebut. Hasil dari perbandingan dua bilangan biner 3-bit dapat dinyatakan dalam tiga kemungkinan kondisi yaitu :

<ul><li>A < B: Jika nilai A lebih kecil dari B. (less)</li></ul>
<ul><li>A = B: Jika nilai A sama dengan B. (equal)</li></ul>
<ul><li>A > B: Jika nilai A lebih besar dari B. (greater)</li></ul>

<div class="d-flex justify-content-center w-60">
<img src="/images/babSeven/Ba7-6.png" alt="Gambar 7.5 - Skematik 3-Bit Comparator" class="img-fluid mb-3 responsive-img">
</div>

<p style="text-align: center;"><b>Gambar 7.3</b> Skematik 3-Bit Comparator</p>
