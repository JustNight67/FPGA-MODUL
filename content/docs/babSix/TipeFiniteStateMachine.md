---
weight: 32
title: "Tipe Finite State Machine"
description: "Memahami Tipe Finite State Machine seperti Mealy State Machine dan Moore State Machine "
icon: "router"
date: "2025-09-13T16:48:46+07:00"
lastmod: "2025-09-13T16:48:46+07:00"
toc: true
---

Finite State Machine terdiri dari dua tipe yaitu Mealy State Machine dan Moore State Machine yang memiliki cara kerja yang berbeda dari setiap tipe :

## Mealy State Machine

Sebuah Finite State Machine disebut sebagai Mealy State Machine apabila keluarannya bergantung pada masukan saat ini dan juga state saat ini. Diagram blok dari Mealy State Machine ditunjukkan pada gambar berikut :

<div class="d-flex justify-content-center w-60">
<img src="/images/babSix/Ba6-1.png" alt="Gambar 6.1 - Blok Diagram Mealy State Machine" class="img-fluid mb-3 responsive-img">
</div>

<p style="text-align: center;"><b>Gambar 6.1</b> Blok Diagram Mealy State Machine</p>

Seperti yang terlihat pada gambar, terdapat dua bagian utama dalam Mealy State Machine, yaitu rangkaian logika kombinasional dan elemen memori. Elemen memori berfungsi untuk memberikan sebagian keluaran sebelumnya dan state saat ini sebagai masukan ke rangkaian logika kombinasional. Berdasarkan masukan saat ini dan state saat ini, Mealy State Machine menghasilkan keluaran. Oleh karena itu, keluaran hanya akan valid pada transisi positif atau negatif dari sinyal clock.

<div class="d-flex justify-content-center w-60">
<img src="/images/babSix/Ba6-2.png" alt="Gambar 6.2 - State Diagram Mealy" class="img-fluid mb-3 responsive-img">
</div>

<p style="text-align: center;"><b>Gambar 6.2</b> State Diagram Mealy</p>

Pada gambar di atas, terdapat tiga state, yaitu A, B, dan C. State-state ini diberi label di dalam lingkaran, dan setiap lingkaran merepresentasikan satu state. Transisi antar state ditunjukkan dengan garis berarah. Pada gambar, notasi 0 / 0, 1 / 0, dan 1 / 1 menunjukkan masukan / keluaran. Dari setiap state, terdapat dua kemungkinan transisi state berdasarkan nilai masukan. Secara umum, jumlah state yang dibutuhkan pada Mealy State Machine lebih sedikit atau sama dengan jumlah state yang dibutuhkan pada Moore State Machine. Untuk setiap Mealy State Machine, selalu ada Moore State Machine yang ekuivalen.

## Moore State Machine

Sebuah Finite State Machine disebut sebagai Moore State Machine apabila keluarannya hanya bergantung pada state saat ini. Diagram blok dari Mealy State Machine ditunjukkan pada gambar berikut :

<div class="d-flex justify-content-center w-60">
<img src="/images/babSix/Ba6-3.png" alt="Gambar 6.3 - Blok Diagram Moore State Machine" class="img-fluid mb-3 responsive-img">
</div>

<p style="text-align: center;"><b>Gambar 6.3</b> Blok Diagram Moore State Machine</p>

Seperti yang ditunjukkan pada gambar, terdapat dua bagian utama dalam Moore State Machine, yaitu rangkaian logika kombinasional dan elemen memori. Dalam hal ini, masukan saat ini dan state saat ini menentukan state berikutnya. Berdasarkan state berikutnya inilah Moore State Machine menghasilkan keluaran. Oleh karena itu, keluaran pada Moore State Machine hanya akan valid setelah terjadi transisi state.

<div class="d-flex justify-content-center w-60">
<img src="/images/babSix/Ba6-4.png" alt="Gambar 6.4 - State Diagram Moore" class="img-fluid mb-3 responsive-img">
</div>

<p style="text-align: center;"><b>Gambar 6.4</b> State Diagram Moore</p>

Pada gambar di atas, terdapat empat state, yaitu A, B, C, dan D. State- state ini beserta keluarannya diberi label di dalam lingkaran. Pada transisi antar state, hanya nilai masukan yang ditunjukkan. Dari setiap state, terdapat dua kemungkinan transisi berdasarkan nilai masukan. Secara umum, jumlah state yang dibutuhkan pada Moore State Machine lebih banyak atau sama dengan jumlah state yang dibutuhkan pada Mealy State Machine. Untuk setiap Moore State Machine, selalu ada Mealy State Machine yang ekuivalen. Oleh karena itu, pemilihan apakah menggunakan Mealy atau Moore dapat ditentukan berdasarkan kebutuhan sistem.
