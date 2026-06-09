---
weight: 19
title: "Basic Arithmetic Implementation"
description: "Melakukan perhitungan sederhana dalam VHDL"
icon: "Calculate"
date: "2025-09-13T16:48:46+07:00"
lastmod: "2025-09-13T16:48:46+07:00"
toc: true
---

FPGA dapat melakukan perhitungan sederhana seperti operasi penjumlahan (adder) dan pengurangan (subtractor) dalam VHDL. Blok logika aritmatika ini dideskripsikan secara spesifik, kemudian diimplementasikan menjadi konfigurasi hardware yang dapat dijalankan oleh FPGA.

## Half Adder

*Half Adder* adalah rangkaian logika kombinasional yang melakukan penjumlahan dua bit biner. Rangkaian ini memiliki dua input yaitu A dan B yang masing-masing input merepresentasikan satu bit, dan dua output yaitu Sum (S) dan Carry (C). Output Sum merupakan hasil penjumlahan dari kedua input, sedangkan output Carry menunjukkan apakah terjadi nilai lebih dari hasil penjumlahan dari kedua input. Berikut adalah *Truth Table* dari rangkaian *Half Adder*.

<p style="text-align: center;"><b>Tabel 3.2</b> Truth Table Half Adder</p>

<div class="d-flex justify-content-center">

| <p style="text-align: center;"><b>INPUT</b></p> | <p style="text-align: center;"><b>INPUT</b></p> | <p style="text-align: center;"><b>OUTPUT</b></p> | <p style="text-align: center;"><b>OUTPUT</b></p> |
| :---: | :---: | :---: | :---: |
| **A** | **B** | **S** | **C** |
| 0 | 0 | 0 | 0 |
| 0 | 1 | 1 | 0 |
| 1 | 0 | 1 | 0 |
| 1 | 1 | 0 | 1 |

</div>

Dari Truth Table diatas dapat dilihat bahwa output Sum akan bernilai 1 jika salah satu dari input (A atau B) bernilai 1. Output Carry bernilai 1 hanya jika kedua input (A dan B) bernilai 1. Rangkaian Half Adder dapat diimplementasikan menggunakan gerbang logika XOR untuk output Sum dan gerbang AND untuk output Carry.

<div class="d-flex justify-content-center w-60">
<img src="/images/babThree/Ba3-25.png" alt="Gambar 3.4 - Rangkaian Half Adder" class="img-fluid mb-3 responsive-img">
</div>

<p style="text-align: center;"><b>Gambar 3.4</b> Rangkaian Half Adder </p>

## Full Adder

Full Adder juga merupakan rangkaian logika kombinasional yang melakukan penjumlahan. Namun, berbeda dengan Half Adder, Full Adder dapat menjumlahkan tiga bit biner. Input tambahan pada Full Adder adalah Carry-in (Cin), yang merupakan carry dari penjumlahan sebelumnya. Full Adder memiliki dua output yang sama seperti dengan Half Adder, yaitu Sum (S) dan Carry-out (Cout). Berikut adalah Truth Table dari rangkaian Full Adder.

<p style="text-align: center;"><b>Tabel 3.3</b> Truth Table Full Adder</p>

<div class="d-flex justify-content-center">

| <p style="text-align: center;"><b>INPUT</b></p> | <p style="text-align: center;"><b>INPUT</b></p> | <p style="text-align: center;"><b>INPUT</b></p> | <p style="text-align: center;"><b>OUTPUT</b></p> | <p style="text-align: center;"><b>OUTPUT</b></p> |
| :---: | :---: | :---: | :---: | :---: |
| **A** | **B** | **Cin** | **S** | **Cout** |
| 0 | 0 | 0 | 0 | 0 |
| 0 | 0 | 1 | 1 | 0 |
| 0 | 1 | 0 | 1 | 0 |
| 0 | 1 | 1 | 0 | 1 |
| 1 | 0 | 0 | 1 | 0 |
| 1 | 0 | 1 | 0 | 1 |
| 1 | 1 | 0 | 0 | 1 |
| 1 | 1 | 1 | 1 | 1 |

</div>

Dari Truth Table diatas, Full Adder memiliki tiga input yaitu A, B, Cin dan dua output yaitu S dan Cout. Output S menunjukkan hasil penjumlahan dari ketiga input, sedangkan output Cout menunjukkan apakah ada lebih (Carry) dari penjumlahan tersebut. Rangkaian Full Adder dapat diimplementasikan menggunakan dua gerbang Half Adder dan satu gerbang OR.

<div class="d-flex justify-content-center w-60">
<img src="/images/babThree/Ba3-26.png" alt="Gambar 3.5 - Rangkaian Full Adder" class="img-fluid mb-3 responsive-img">
</div>

<p style="text-align: center;"><b>Gambar 3.5</b> Rangkaian Full Adder </p>

<span></span>

## Half Subtractor

*Half Subtractor* adalah rangkaian logika kombinasional yang digunakan untuk melakukan operasi pengurangan pada bilangan biner. Rangkaian ini memiliki dua input yaitu A dan B, dan juga dua output yaitu Difference (D) dan Borrow (B). Output Difference merupakan hasil dari pengurangan A dan B (A – B), sedangkan output Borrow menunjukkan apakah terjadi peminjaman ("borrow") dari bit berikutnya atau tidak.

<p style="text-align: center;"><b>Tabel 3.4</b> Truth Table Half Subtractor</p>

<div class="d-flex justify-content-center">

| <p style="text-align: center;"><b>INPUT</b></p> | <p style="text-align: center;"><b>INPUT</b></p> | <p style="text-align: center;"><b>OUTPUT</b></p> | <p style="text-align: center;"><b>OUTPUT</b></p> |
| :---: | :---: | :---: | :---: |
| **A** | **B** | **Diff** | **Borrow** |
| 0 | 0 | 0 | 0 |
| 0 | 1 | 1 | 1 |
| 1 | 0 | 1 | 0 |
| 1 | 1 | 0 | 0 |

</div>

Dari Truth Table diatas, output Difference (D) akan bernilai 1 jika nilai dari input A dan B berbeda, dan bernilai 0 jika nilai dari input A dan B sama. Output Borrow (B) akan bernilai 1 hanya ketika nilai dari input A bernilai 0 dan B bernilai 1, yang menunjukkan bahwa diperlukan peminjaman dari bit berikutnya. Half Subtractor dapat diimplementasikan menggunakan gerbang XOR untuk output Difference dan gerbang AND NOT pada input A untuk output Borrow.

<div class="d-flex justify-content-center w-60">
<img src="/images/babThree/Ba3-27.png" alt="Gambar 3.6 - Rangkaian Half Subtractor" class="img-fluid mb-3 responsive-img">
</div>

<p style="text-align: center;"><b>Gambar 3.6</b> Rangkaian Half Subtractor </p>

## Full Subtractor

Full Subtractor digunakan untuk melakukan pengurangan pada tiga bit biner. Input tambahan pada Full Subtractor adalah Borrow-in (Bin), yang merupakan borrow dari pengurangan sebelumnya. Output Full Subtractor sama dengan Half Subtractor, yaitu Difference (D) dan Borrow-out (Bout).

<p style="text-align: center;"><b>Tabel 3.5</b> Truth Table Full Subtractor</p>

<div class="d-flex justify-content-center">

| <p style="text-align: center;"><b>INPUT</b></p> | <p style="text-align: center;"><b>INPUT</b></p> | <p style="text-align: center;"><b>INPUT</b></p> | <p style="text-align: center;"><b>OUTPUT</b></p> | <p style="text-align: center;"><b>OUTPUT</b></p> |
| :---: | :---: | :---: | :---: | :---: |
| **A** | **B** | **Bin** | **Diff** | **Bout** |
| 0 | 0 | 0 | 0 | 0 |
| 0 | 0 | 1 | 1 | 1 |
| 0 | 1 | 0 | 1 | 1 |
| 0 | 1 | 1 | 0 | 1 |
| 1 | 0 | 0 | 1 | 0 |
| 1 | 0 | 1 | 0 | 0 |
| 1 | 1 | 0 | 0 | 0 |
| 1 | 1 | 1 | 1 | 1 |

</div>

Dari Truth Table diatas, Full Subtractor memiliki tiga input yaitu A, B, dan Bin, dan dua output yaitu D dan Bout. Output Diff menunjukkan hasil pengurangan dari input A dan B dengan memperhitungkan input Borrow Bin, sedangkan output Bout menunjukkan apakah ada kekurangan (borrow) dari pengurangan tersebut.

<div class="d-flex justify-content-center w-80">
<img src="/images/babThree/Ba3-28.png" alt="Gambar 3.7 - Rangkaian Full Subtractor" class="img-fluid mb-3 responsive-img">
</div>

<p style="text-align: center;"><b>Gambar 3.7</b> Rangkaian Full Subtractor </p>
